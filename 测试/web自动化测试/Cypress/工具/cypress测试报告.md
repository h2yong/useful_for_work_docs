对于测试报告，Cypress 缺省支持的是Spec方式。

如果你习惯于[teamcity](https://github.com/cypress-io/mocha-teamcity-reporter)或者[junit](https://github.com/michaelleeallen/mocha-junit-reporter)的报告样式，Cypress 是直接提供的，只需要在 cypress.json 文件中添加：

```json
"reporter": "junit"
//或者
"reporter": "teamcity"
```

而我更习惯于看 HTML 的测试报告，这就需要做点额外的工作了：

```shell
npm install --save-dev mocha mochawesome mochawesome-merge mochawesome-report-generator
```

在 cypress.json 设置相关参数：

```json
{
    "env": {
        "search":"Cypress e2e"
    },
    "reporter": "mochawesome",
    "reporterOptions": {
        "reportDir": "cypress/results",
        "overwrite": false,
        "html": true,
        "json": true
    }
}
```

执行 run 后会看到在当前目录下生成了测试报告。

命令行方式：

```shell
cypress run --reporter mochawesome \
  --reporter-options reportDir="cypress/results",overwrite=false,html=false,json=true
```

参考：

* https://docs.cypress.io/guides/tooling/reporters