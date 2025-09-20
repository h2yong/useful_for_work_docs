# docker搭建xmind2testlink

## 拉取镜像

```shell
docker pull tobyqin/xmind2testlink
```

## 运行容器

```shell
docker run -d --name xmind2testlink --restart always -p 3000:5001 tobyqin/xmind2testlink
```

## 验证

1. 查看jenkins容器运行情况

```shell
docker ps | grep xmind2testlink
```

2. 访问服务

`http://{server_domain}:3000`

