# docker搭建TestLink

## 创建容器间通信网络

```console
docker network create testlink-network
```

## 拉取镜像

```shell
docker pull bitnami/mariadb:10.3.31
docker pull bitnami/testlink:1.9.20
```

## 运行容器

1. 创建目录/data/mariadb，并修改权限`chown -R 1001:1001 /data/mariadb`
2. 创建目录/data/testlink，并修改权限`chown -R 1001:1001 /data/testlink`
3. 启动mariadb，输入如下命令：

```shell
docker run -d --name mariadb \
  -p 3306:3306 \
  --env ALLOW_EMPTY_PASSWORD=yes \
  --env MARIADB_USER=testlink \
  --env MARIADB_PASSWORD=testlink \
  --env MARIADB_DATABASE=testlink \
  --network testlink-network \
  --volume /data/mariadb:/bitnami/mariadb \
  bitnami/mariadb:10.3.31
```

3. 启动testlink，输入如下命令：

```shell
docker run -d --name testlink \
  -p 8080:8080 -p 8443:8443 \
  --env ALLOW_EMPTY_PASSWORD=yes \
  --env TESTLINK_DATABASE_USER=testlink \
  --env TESTLINK_DATABASE_PASSWORD=testlink \
  --env TESTLINK_DATABASE_NAME=testlink \
  --network testlink-network \
  --volume /data/testlink:/bitnami/testlink \
  bitnami/testlink:1.9.20
```

## 验证

1. 查看容器运行情况

```shell
docker ps | grep mariadb
docker ps | grep testlink
```

2. 访问服务，初始用户名密码：user/bitnami

`http://{server_domain}:8080`

## 参考文档

https://hub.docker.com/r/bitnami/testlink