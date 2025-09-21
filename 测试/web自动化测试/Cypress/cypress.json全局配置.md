# cypress.json配置项

Cypress Test Runner 初始化项目后，默认会创建`cypress.json` 配置文件，此 JSON 文件用于存储您提供的任何配置值。

>  更改cypress.json配置文件
>  可使用`--config-file flag`来更改配置文件或关闭配置文件的使用。

**常见配置内容如下**

| 选项                 | 默认值                          | 描述                                                                                                                                                        |
| -------------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| baseUrl              | null                            | 命令 [cy.visit()](https://docs.cypress.io/api/commands/visit)或[cy.request()](https://docs.cypress.io/api/commands/request)的前缀URL                        |
| clientCertificates   | []                              | 可选的[client certificates](https://docs.cypress.io/guides/references/client-certificates)                                                                  |
| env                  | {}                              | 环境变量通过Cypress.env 调用，参考[environment variables](https://docs.cypress.io/guides/guides/environment-variables)                                      |
| includeShadowDom     | false                           | 是否遍历隐藏DOM边界并在查询命令的结果中包含隐藏DOM内的元素                                                                                                  |
| numTestsKeptInMemory | 50                              | 快照和命令数据保存在内存中的测试次数。如果您在测试运行期间在浏览器中遇到高内存消耗，请减少此数字。                                                          |
| port                 | null                            | 用于托管Cypress的端口，通常这是一个随机生成的端口                                                                                                           |
| redirectionLimit     | 20                              | 被测应用程序在出错前可以重定向的次数                                                                                                                        |
| reporter             | spec                            | [测试报告格式](https://docs.cypress.io/guides/tooling/reporters)                                                                                            |
| reporterOptions      | null                            | [测试报告参数](https://docs.cypress.io/guides/tooling/reporters#Reporter-Options)                                                                           |
| retries              | { "runMode": 0, "openMode": 0 } | 重试失败测试的次数。可以配置为应用`cypress run`或`cypress open`单独应用。有关详细信息，请参阅[测试重试](https://docs.cypress.io/guides/guides/test-retries) |
| watchForFileChanges  | true                            | 设置Cypress是否监视文件修改来重新运行测试                                                                                                                   |

还可以在测试中，通过[Cypress.config()](https://docs.cypress.io/api/cypress-api/config)在测试运行时进行配置。

更多配置项请参考[configuration](https://docs.cypress.io/guides/references/configuration#cypress-json)

