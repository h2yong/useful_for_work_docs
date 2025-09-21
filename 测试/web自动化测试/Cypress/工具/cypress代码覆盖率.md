# 端到端代码覆盖率

## 安装插件

```shell
npm install -D @cypress/code-coverage
```

然后将下面的代码添加到您的 [supportFile](https://docs.cypress.io/guides/references/configuration#Folders-Files)和 [pluginsFile](https://docs.cypress.io/guides/references/configuration#Folders-Files)。

```js
// cypress/support/index.js
import '@cypress/code-coverage/support'
```

```js
// cypress/plugins/index.js
module.exports = (on, config) => {
  require('@cypress/code-coverage/task')(on, config)
  // include any other plugin code...

  // It's IMPORTANT to return the config object
  // with any changed environment variables
  return config
}
```

