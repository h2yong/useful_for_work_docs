# docker搭建Arachni
## 拉取镜像
```shell
docker pull postgres:13.4
docker pull arachni/arachni:1.5.1
```

## 运行容器

1. 启动postgres，输入如下命令：

```shell
docker run \
-d \
--name postgres13 \
-p 5432:5432 \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=123456 \
postgres:13.4
```
2. 登录postgres，传教数据库实例arachni（此步骤略过）
3. 启动arachni，输入如下命令（注意DB_HOST需要填写postgres IP地址）：

```sh
docker run -d \
  -e "DB_ADAPTER=postgresql" \
  -e "DB_HOST=postgres13" \
  -e "DB_NAME=arachni" \
  -e "DB_USER=postgres" \
  -e "DB_PASS=123456" \
  -p 222:22 \
  -p 7331:7331 \
  -p 9292:9292 \
  --name arachni \
  -e SERVER_ROOT_PASSWORD="123456" \
  -e ARACHNI_PARAMS="--authentication-username arachni --authentication-password 123456 --only-positives"  \
  arachni/arachni:1.5.1
```
