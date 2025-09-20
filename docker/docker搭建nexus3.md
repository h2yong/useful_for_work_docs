# docker搭建nexus3

## 拉取镜像

```shell
docker pull sonatype/nexus3:3.36.0
```

## 运行容器

1. 运行nexus容器b，输入如下命令：

```shell
docker run -id --privileged=true --name=nexus3 --restart=always -p 8082:8081 -v /data/nexus3/nexus-data:/var/nexus-data sonatype/nexus3:3.36.0
```

## 验证

1. 访问服务

`http://{server_domain}:8082`

## Admin初始密码
nexus3默认的账号依旧是admin，密码存储在nexus3的容器的/nexus-data/admin.password文件中。

修改后的密码为：dmai123456

## 参考文档

https://segmentfault.com/a/1190000020832615