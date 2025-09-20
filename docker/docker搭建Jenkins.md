# docker搭建Jenkins
## 拉取镜像
```shell
docker pull jenkins/jenkins:2.303.1
```

## 运行容器
```shell
docker run -d --name jenkins -p 8081:8080 -p 50000:50000 -v /data/jenkins_home:/var/jenkins_home --env JAVA_OPTS="-Duser.timezone=GMT+08" jenkins/jenkins:2.303.1
```

> -p 50000:50000  打开远程访问
>
> --env JAVA_OPTS="-Duser.timezone=GMT+08"　解决jenkins时间显示和本地时间不一致的问题

## 验证

1. 查看jenkins容器运行情况

```shell
docker ps | grep jenkins
```

2. 访问服务

`http://{server_domain}:8081`

## 安装过程遇到的小问题

### jenkins容器docker run之后状态总是Exited

```shell
查看docker日志：
docker logs jenkins
发现是目前权限问题
因为/data/jenkins_home 目录是root权限
```

**解决方案：**

```shell
chown -R 1000:1000 /data/jenkins_home //用户组改变
```

### 初始密码查看

```shell
在安装完成后，默认生成了一个登录密码，首次登录需要这个密码。
密码路径：/var/jenkins_home/secrets/initialAdminPassword //容器内部
```

## 参考文档

* https://segmentfault.com/a/1190000021566330
* https://github.com/jenkinsci/docker
