# docker搭建xmind2testcase

## 拉取镜像

```shell
docker pull cyberpixel/xmind2testcase:1.5.0
```

## 运行容器

```shell
docker run -d --name xmind2testcase -p 8000:8000 cyberpixel/xmind2testcase:1.5.0
```

## 验证

1. 查看jenkins容器运行情况

```shell
docker ps | grep xmind2testcase
```

2. 访问服务

`http://{server_domain}:8000`

