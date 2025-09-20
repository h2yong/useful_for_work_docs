# spring boot快速开发框架

| java开源快速开发框架                                                                                                                                              | 基础框架                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| https://www.jhipster.tech/                                                                                                                                | springboot2.0                    |
| https://www.stylefeng.cn/<br/>https://gitee.com/log4j/pig                                                                                                 | springboot2.0                    |
| https://gitee.com/y_project/RuoYi<br/>https://gitee.com/y_project/RuoYi-Cloud<br/>https://gitee.com/y_project/RuoYi-Vue                                   | springboot2.0                    |
| http://www.jeecg.com/<br>https://gitee.com/thinkgem/jeesite4<br/>https://gitee.com/thinkgem/jeesite4-cloud <br/>https://gitee.com/thinkgem/jeesite4-jflow | 基于代码生成器的JAVA快速开发平台 |
| https://bladex.vip/#/doc/introduction                                                                                                                     | springboot2.0                    |
| https://gitee.com/shuzheng/zheng                                                                                                                          |                                  |
| https://gitee.com/explore/oauth-dev                                                                                                                       |                                  |
| https://gitee.com/geek_qi/cloud-platform                                                                                                                  |                                  |
| https://gitee.com/596392912/mica                                                                                                                          |                                  |
| https://github.com/elunez/eladmin                                                                                                                         | 前后端分离的后台管理系统         |
| https://github.com/hs-web/hsweb-framework                                                                                                                 | 企业后台管理系统的基础项目       |

## [RuoYi-Cloud](https://gitee.com/y_project/RuoYi-Cloud)学习

* 权限认证RequiresPermissions为自定义AOP，没有使用开源的spring security或shiro，舍弃学习此功能。
* ruoyi-monitor没有集成oauth2/jwt等认证机制，待自行开发

## [jeesite4-cloud](https://gitee.com/thinkgem/jeesite4-cloud )学习

* 功能简单，很多工程为引用开源项目，如eureka/nacos/sentinel dashboard

## [Pig](https://gitee.com/log4j/pig)学习

* pig-monitor没有集成oauth2/jwt等认证机制，待自行开发
* 配置中心加密待自行研究
* pig-register（nacos-server）注册中心已源码方式运行，由于公司一般有自己注册中心和配置中心，后续再参考https://www.yuque.com/pig4cloud/pig/nu14gb
* pig-sentinel-dashboard和pig-xxl-job-admin已源码方式运行，直接学习源码即可。
