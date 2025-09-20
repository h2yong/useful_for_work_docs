# linux 防火墙 firewall-cmd 命令详解

`firewall-cmd`命令是用于管理防火墙的命令，该命令可以用于 CentOS/RHEL 7 和更高版本中的防火墙管理。  
以下是一个关于`firewall-cmd`命令用法的完整介绍：

## 基本语法

`firewall-cmd --zone=zone-name --add-service=service-name --permanent`

## 命令参数

- `--zone`：指定要添加服务的区域名称。
- `--add-service`：指定要添加的服务名称。
- `--permanent`：指定该规则永久生效。  
  除此之外，还有其他可选参数：
- `--list-all`：列出所有规则。
- `--reload`：重新加载防火墙规则。
- `--permanent`：将规则保存到永久配置中，以便系统重启后仍然有效。
- `--delete-service`：删除服务。
- `--list-services`：列出当前系统中所有可用服务。
- `--add-source`：添加一个 IP 或 IP 段。
- `--remove-source`：删除一个 IP 或 IP 段。
- `--list-sources`：列出所有已添加的 IP 或 IP 段。
- `--add-port`：添加端口。
- `--remove-port`：删除端口。
- `--list-ports`：列出所有已添加的端口。
- `--add-rich-rule`：添加一个更加复杂的规则。
- `--query-service`：查询服务是否可用。
- `--get-zones`：列出所有可用的区域。
- `--zone=zone-name`：指定一个区域。

## 示例

1. 添加端口  
   `firewall-cmd --zone=public --add-port=80/tcp --permanent`
2. 删除端口  
   `firewall-cmd --zone=public --remove-port=80/tcp --permanent`
3. 添加服务  
   `firewall-cmd --zone=public --add-service=http --permanent`
4. 删除服务  
   `firewall-cmd --zone=public --remove-service=http --permanent`
5. 列出所有规则  
   `firewall-cmd --list-all`
6. 重新加载防火墙规则  
   `firewall-cmd --reload`
7. 列出所有可用的服务  
   `firewall-cmd --list-services`
8. 查询端口  
   `firewall-cmd --zone=public --query-port=8080/tcp`

## 注意事项

- 在修改防火墙规则时，建议使用 --permanent 选项，以便该规则在系统重启后仍然有效。
- 建议使用防火墙决策相关的策略来管理您的防火墙，以确保系统的安全性。
