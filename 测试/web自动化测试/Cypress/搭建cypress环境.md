# 搭建cypress环境

##  安装NodeJS

如何安装 NodeJS 参考[这里](http://nodejs.cn/download/)，里面有各种平台的安装包，直接下载安装即可。安装完后通过`node -v`指令查看是否安装成功。

## 安装cypress

1. 选择一个目录或新建一个目录作为你 Cypress 项目目录，进入这个目录 (Windows 推荐使用 Power Shell 终端，Mac 和其他 L/Uinux 系统则使用默认的 Terminal)；
2. 使用`npm init`指令来初始化一个本地的 NodeJS 包文件；
3. 运行指令`npm install cypress --save-dev`来安装 Cypress；
4. 运行指令`.\node_modules\.bin\cypress open`来打开 Cypress 应用程序；不出意外，你将会看到这个界面。

![cypress-ide](D:\OneDrive\dmai工作文档\web自动化测试\Cypress\cypress-ide.png)

5. 执行命令`.\node_modules\.bin\cypress open`会在当前目录下创建如下内容
```shell
|-- cypress.json     // 配置文件
|-- cypress
    -- fixtures      // 用于存放自定义的json文件
    -- integration   // 测试代码
        -- examples  // 示例代码
    -- plugins       // 自定义指令时，与support文件夹组合使用
        -- index.js
    -- support       // 用于调整[自定义选项](https://docs.cypress.io/guides/references/configuration)
        -- commands.js
        -- index.js
```

## 通过npm命令运行Cypress IDE

在cypress项目package.json的scripts配置项中添加以下cypress命令：

```json
{
  "scripts": {
    "cypress:open": "cypress open"
  }
}
```
现在您可以从项目根目录调用命令，如下所示：
```shell
npm run cypress:open
```

即可打开Cypress IDE。

## 执行测试用例

在cypress项目package.json的scripts配置项中添加以下cypress命令：

```json
{
  "scripts": {
    "cypress:run": "cypress run"
  }
}
```
现在您可以从项目根目录调用命令执行测试用例，如下所示：
```shell
npm run cypress:run
```

## 参考文档

* [官方安装文档](https://docs.cypress.io/guides/getting-started/installing-cypress)
