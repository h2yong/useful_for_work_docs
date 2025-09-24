# npm运行时报错“因为在此系统上禁止运行脚本”解决办法

## 表象

在控制台运行npm指令时遇到如下报错信息：“因为在此系统上禁止运行脚本”

```java
.\node_modules\.bin\cypress open
.\node_modules\.bin\cypress : 无法加载文件 .\node_modules\.bin\cypress.ps1，因为在此系统上禁止运行脚本。有关详细信息，请参阅 https:/go.microsoft.com/fwlink/?LinkID=135170 中的 about_Execution_Policies。
所在位置 行:1 字符: 1
+ .\node_modules\.bin\cypress open
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) []，PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

## 原因

首次在计算机上启动 Windows PowerShell 时，现用执行策略很可能是 Restricted（默认设置）。Restricted 策略不允许任何脚本运行，防止执行不信任的脚本。

## 解决办法

1. 以管理员身份运行powershell；

2. 执行命令`set-ExecutionPolicy RemoteSigned`，将计算机上的执行策略更改为 RemoteSigned；

   ```shell
   PS C:\Windows\system32> set-ExecutionPolicy RemoteSigned
   
   执行策略更改
   执行策略可帮助你防止执行不信任的脚本。更改执行策略可能会产生安全风险，如 https:/go.microsoft.com/fwlink/?LinkID=135170
   中的 about_Execution_Policies 帮助主题所述。是否要更改执行策略?
   [Y] 是(Y)  [A] 全是(A)  [N] 否(N)  [L] 全否(L)  [S] 暂停(S)  [?] 帮助 (默认值为“N”): y
   PS C:\Windows\system32> get-ExecutionPolicy
   ```

3. 验证是否更改成功

   ```shell
   PS C:\Windows\system32> get-ExecutionPolicy
   RemoteSigned
   ```