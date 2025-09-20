# docker搭建Nacos

## 拉取镜像

```shell
docker pull nacos/nacos-server:v2.0.3
```

## 运行容器

```shell
docker run --name nacos-quick -e MODE=standalone -p 8848:8848 -d nacos/nacos-server:v2.0.3
```

更多用法：

* https://github.com/nacos-group/nacos-docker

* https://nacos.io/zh-cn/docs/quick-start.html

## 访问

http://127.0.0.1:8848/nacos/

访问用户：nacos/nacos