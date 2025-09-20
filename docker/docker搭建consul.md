# docker搭建consul
## 拉取镜像
```shell
docker pull consul:1.9.10
```

## 运行容器

```shell
docker run -d -p 8500:8500 -v /data/consul:/consul/data -e CONSUL_BIND_INTERFACE='eth0' --name=consul_server_1 consul:1.9.10 agent -server -bootstrap -ui -node=1 -client='0.0.0.0'
```

参考文档：

* https://www.cnblogs.com/lfzm/p/10633595.html


## 访问
Http://localhost:8500

