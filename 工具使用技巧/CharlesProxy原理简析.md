# CharlesProxy 原理简析

[CharlesProxy][1]官网介绍如下：

> [CharlesProxy][1]是 HTTP 代理/ HTTP 监视器/反向代理，使开发人员可以查看其计算机与 Internet 之间的所有 HTTP 和 SSL / HTTPS 通信。 这包括请求，响应和 HTTP 标头（其中包含 cookies 和缓存信息）。

## 正向代理（forward proxy）

## 反向代理（reverse proxy）

## Charles 捕获 HTTPS 报文原理

```mermaid
sequenceDiagram
	Title: HTTP协议
    客户端-->服务器: 不安全的HTTP
    Note over 客户端,服务器: 1.明文传输，被监听<br>2.内容被篡改<br>3.身份被冒充
```

| 对比     | 对称加密                                       | 非对称加密                                         |
| -------- | ---------------------------------------------- | -------------------------------------------------- |
| 特点     | 只有一个唯一的密钥                             | 有一对公钥和私钥                                   |
| 优点     | 速度快                                         | 公钥是公开的，私钥是不公开的，只要私钥不泄露就没事 |
| 缺点     | 每人手上都有个相同的密钥，任意一方泄露全体完蛋 | 速度慢                                             |
| 例子     | DES                                            | RSA                                                |
| 数学原理 | 异或运算                                       | 大整数因数分解                                     |

```mermaid
sequenceDiagram
	autonumber
	Title: 对称加密简析
	客户端->>服务器: 将请求用密钥加密，发送到服务器
	loop
        服务器->服务器: 使用密钥解密获得信息
    end
	服务器-->>客户端: 将返回信息用密码要加密，返回给客户端
    loop
        客户端->客户端: 使用密钥解密获得信息
    end
    Note over 客户端,服务器: 密钥直接在网络传输，则存在暴露风险
```

```mermaid
sequenceDiagram
	autonumber
    Title: 非对称加密简析
	客户端->>服务器: 我要发起HTTPS请求了，给我一个公钥吧
	loop
        服务器->服务器: 服务器早就生成好了一对密钥
    end
	服务器-->>客户端: 好，这就把公钥给你
	loop
        客户端->客户端: 客户端随机生成一个随机数，当作会要密钥，然后用公钥加密它
    end
    客户端->>服务器: 将加密后的会话密钥传给服务器
    loop
        服务器->服务器: 使用私钥解密会话密钥，得到随机数
    end
    服务器-->>客户端: 好，会话密钥已解出来，这次会话就用这个随机数进行对称加密吧！
    Note right of 服务器: 此处关于随机数的生成为简化版本，真正的HTTPS需要3个随机数来生成最终的随机数
```

```mermaid
sequenceDiagram
    autonumber
    Title: Charle捕获https报文原理简析
    客户端->>Charles: 客户端向服务器请求证书
    Charles->>服务器: 拦截，代替客户端向服务器发送请求
    服务器-->>Charles: 向客户端返回证书
    Charles-->>客户端: 拦截，将自己的证书返回给客户端
    客户端->>Charles: 信任Charles证书，用Charles公钥加密对称密钥，发送给"服务器"
    Charles->>服务器: 拦截，用自己私钥解密对称密钥，然后用服务器公钥加密后发送给"服务器"
    服务器-->>Charles: 解密对称密钥，发送响应
    Charles-->>客户端: 解密报文，修改证书
    客户端->服务器: 客户端与Charles通信，Charles与服务器通信，数据均被Charles拦截
```

> [CharlesProxy][1]的本质就是劫持。但是之所以能够劫持，并不是因为 https 不安全，而是因为操作人主动安装信任了[CharlesProxy][1]证书。

## 参考文档

- https://github.com/youngwind/blog/issues/108
- https://www.jianshu.com/p/405f9d76f8c4

[1]: https://www.charlesproxy.com/
