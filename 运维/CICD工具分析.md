# CI/CD工具分析

**可选方案：**

| 对比要点     | [Jenkins](https://www.jenkins.io/)                           | [gitlab ci/cd](https://gitlab.dm-ai.cn/)                     | [argo](https://argoproj.github.io/)                          | [tekton](https://tekton.dev/)                             | [Ansible](https://www.ansible.com/)    |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------------------- | -------------------------------------- |
| 配置文件格式 | Jenkinsfile                                                  | YAML                                                         | YAML                                                         | YAML                                                      | playbook                               |
| 优点         | 大量插件库 <br>自托管，例如对工作空间的完全控制<br>容易调试运行，由于对工作空间的绝对控制<br>容易搭建节点<br>容易部署代码<br>非常好的凭证管理<br>非常灵活多样的功能<br>支持不同的语言<br>非常直观<br>白盒化 | 更好的 Docker 集成<br>运行程序扩展或收缩比较简单<br>阶段内的作业并行执行<br>有向无环图 pipeline 的机会<br>由于并发运行程序而非常易于扩展收缩<br>合并请求集成 容易添加作业<br>容易处理冲突问题<br>良好的安全和隐私政策 | 一个基于 kubernetes CRD 实现的一个 Workflow工具<br>代码即配置（py实现）<br>轻量级<br/>白盒化 | Kubernetes 原生CI/CD 系统<br>灵活扩展<br>轻量级<br>白盒化 | 自动化化运维工具，开发语言为python<br> |
| 缺点         | 插件集成复杂<br>对于比较小的项目开销比较大，因为你需要自己搭建<br>缺少对整个 pipeline 跟踪的分析 | 需要为每个作业定义构建并上传 / 下载<br>在实际合并发生之前测试合并状态是不可能的<br>还不支持细分阶段 | 对k8s的支持比较少<br>API开放的功能比较少，做集成比较难度较高 | 插件较少                                                  | web UI端为商业版本<br>不支持CI<br>     |

参考文档：

* https://blog.csdn.net/oqqYuan1234567890/article/details/104271124#j1
* https://cloud.tencent.com/developer/article/1814788
* https://developer.jdcloud.com/article/1195

## 代码扫描

* [Sonarqube](https://docs.sonarqube.org/latest/)：支持多种语言代码扫描，支持多种插件（以下举出部分例子）

| 语言       | 插件        | 说明 |
| ---------- | ----------- | ---- |
| java       | findbugs    |      |
| java       | Checkstyle  |      |
| java       | PMD         |      |
| nodejs     | JSHint      |      |
| javascript | eslint      |      |
| python     | Pylint      |      |
| python     | Flake8      |      |
| python     | pycodestyle |      |


## 基础设施即代码

**应用变更和资源编排现状：**

* 配置中心为[apollo](http://apollo/)，由运维导入执行配置项变更
* 应用部署：原生Gitlab
* 数据库变更由DBA手工执行
* 资源编排使用[k8s](http://dev.k8s/)

**基础设施即方案**

> 见名知意，基础设施即代码以代码的方式来设置基础设施。基础设施即代码包含资源编排、数据库变更、配置中心变更、脚本变更、依赖系统变更和应用部署等，可以使用以下基础设施即代码工具。

| 对比要点                                                     | [Pulumi](https://www.pulumi.com/)                            | [Terraform](https://www.terraform.io/)                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ | -------------------------------------------------------- |
| [Language Support](https://www.pulumi.com/docs/intro/vs/terraform/#languagesupport) | Python, TypeScript, JavaScript, Go, C#, F#                   | Hashicorp Configuration Language (HCL)                   |
| [State Management](https://www.pulumi.com/docs/intro/vs/terraform/#statemanagement) | Managed through Pulumi Service by default, self-managed options available | Self-managed by default, managed SaaS offering available |
| [Provider Support](https://www.pulumi.com/docs/intro/vs/terraform/#providersupport) | Native cloud providers with 100% same-day resource coverage plus Terraform-based providers for additional coverage | Support across multiple IaaS, SaaS, and PaaS providers   |
| [OSS License](https://www.pulumi.com/docs/intro/vs/terraform/#license) | Apache License 2.0                                           | Mozilla Public License 2.0                               |

**参考文档：**

* https://www.pulumi.com/docs/intro/vs/terraform/
* https://phoenixnap.com/blog/pulumi-vs-terraform
* https://julie.io/writing/arm-terraform-pulumi-infra-as-code/
* https://blog.51cto.com/kaliarch/2563580