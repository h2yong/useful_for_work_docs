# docker搭建SonarQube

## 修改Linux系统参数

1. `/etc/sysctl.conf`文件中添加以下内容

```
vm.max_map_count = 262144
fs.file-max = 65536
```

2. `/etc/security/limits.conf`文件中添加以下内容

```
* soft nofile 65536
* hard nofile 65536
```

3. 重启

```
reboot
```

## 拉取镜像

```shell
docker pull postgres:13.4
docker pull sonarqube:9.0.1-community
```

## 运行容器

1. 启动postgres，输入如下命令：

```shell
docker run -d \
--name postgres13 \
-p 5432:5432 \
-e POSTGRES_USER=postgres \
-e POSTGRES_PASSWORD=123456 \
-e PGDATA=/var/lib/postgresql/data/pgdata \
-v /data/postgresql:/var/lib/postgresql/data \
postgres:13.4
```

2. 登录postgres，传教数据库实例sonar（此步骤略过）
3. 启动SonarQube，输入如下命令：

```shell
docker run -d \
--name sonarqube9 \
-p 9000:9000 \
--link postgres13 \
-e SONARQUBE_JDBC_URL=jdbc:postgresql://postgres13:5432/sonar \
-e SONARQUBE_JDBC_USERNAME=postgres \
-e SONARQUBE_JDBC_PASSWORD=123456 \
-v /data/sonar/sonarqube_conf:/opt/sonarqube/conf \
-v /data/sonar/sonarqube_extensions:/opt/sonarqube/extensions \
-v /data/sonar/sonarqube_logs:/opt/sonarqube/logs \
-v /data/sonar/sonarqube_data:/opt/sonarqube/data \
sonarqube:9.0.1-community
```

3. 检查容器状态

   ```shell
   # docker ps
   CONTAINER ID   IMAGE                       COMMAND                  CREATED             STATUS          PORTS                                       NAMES
   cbc19a603796   sonarqube:9.0.1-community   "bin/run.sh bin/sona…"   11 minutes ago      Up 11 minutes   0.0.0.0:9000->9000/tcp, :::9000->9000/tcp   sonarqube9
   0fb4cecc0bc9   postgres:13.4               "docker-entrypoint.s…"   About an hour ago   Up 13 minutes   0.0.0.0:5432->5432/tcp, :::5432->5432/tcp   postgres13
   ```

4. 放通防火墙

```
firewall-cmd --zone=public --permanent --add-port=9000/tcp
firewall-cmd --zone=public --permanent --add-port=5432/tcp
firewall-cmd --reload
```

## 验证

输入http://{server_domain}:9000，初始使用 admin/admin 登录

## 参考文档

https://javamana.com/2020/12/20201226171330497O.html

