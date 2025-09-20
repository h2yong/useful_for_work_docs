# 常用docker命令

## 进入docker

```bash
$ sudo docker ps  
$ sudo docker exec -it 775c7c9ee1e1 /bin/bash
```

## docker启动失败如何查看容器日志

通过如下命令来获取容器的日志地址（97069f94437b为容器ID）

```bash
sudo docker inspect --format '{{.LogPath}}' 97069f94437b
```

通过cat命令查看上述命令找到的日志地址

```bash
sudo cat /var/lib/docker/containers/97069f94437b86b50341f8253d85f426884315c3d027f7b7fa975751c7d8e18e/97069f94437b86b50341f8253d85f426884315c3d027f7b7fa975751c7d8e18e-json.log
```

## 重启所有docker容器
```bash
sudo docker restart $(sudo docker ps -a -q)
```