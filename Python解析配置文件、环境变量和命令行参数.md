# Python 解析配置文件、环境变量和命令行参数，获得一组选项

下面例子通过首先解析配置文件，然后检查环境变量，最后再解析命令行参数，来赋值给变量。

```python
import configparser
import os
import argparse

# 创建配置解析器
config = configparser.ConfigParser()

# 加载配置文件
config.read('config.ini')

# 获取选项值
host = config.get('database', 'host')
port = config.getint('database', 'port')
username = config.get('database', 'username')
password = config.get('database', 'password')

# 检查环境变量
host = os.getenv('DB_HOST', host)
port = int(os.getenv('DB_PORT', port))
username = os.getenv('DB_USERNAME', username)
password = os.getenv('DB_PASSWORD', password)

# 创建解析器
parser = argparse.ArgumentParser()

# 添加命令行参数
parser.add_argument('-H', '--host', default=host, help='数据库主机')
parser.add_argument('-P', '--port', type=int, default=port, help='数据库端口')
parser.add_argument('-u', '--username', default=username, help='用户名')
parser.add_argument('-p', '--password', default=password, help='密码')

# 解析命令行参数
args = parser.parse_args()

# 获取命令行参数的值
host = args.host
port = args.port
username = args.username
password = args.password

# 打印选项值
print(f"主机：{host}")
print(f"端口：{port}")
print(f"用户名：{username}")
print(f"密码：{password}")
```