```shell
docker run --name mysql8 -p 3306:3306 -p 33060:33060 -v /data/mysql/mysql_data:/var/lib/mysql -v /data/mysql/conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=123456 -d mysql:8.0.26 --character-set-server=utf8mb4 --collation-server=utf8mb4_unicode_ci
```