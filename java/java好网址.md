# java 好网址

## 代码构建

- [Apache Maven](http://maven.apache.org/)：Maven 使用声明进行构建并进行依赖管理，偏向于使用约定而不是配置进行构建。
- [Gradle](http://www.gradle.org/)：Gradle 采用增量构建。Gradle 通过 Groovy 编程而不是传统的 XML 声明进行配置。Gradle 可以很好地配合 Maven 进行依赖管理。

## 代码分析

- [Checkstyle](http://checkstyle.sourceforge.net/)：对编程规范和标准进行静态分析。
- [FindBugs](http://findbugs.sourceforge.net/)：通过字节码静态分析找出潜在 Bug。
- [PMD](http://pmd.sourceforge.net/)：对源代码中不良编程习惯进行分析。
- [SonarQube](http://www.sonarqube.org/)：通过插件集成其它分析组件，提供评估最终结果报告

## 覆盖率统计

- [cobertura](https://cobertura.github.io/cobertura/)
- [jacoco](https://www.jacoco.org/jacoco/)

## Web 开发相关框架

- [spring-boot](http://projects.spring.io/spring-boot/)
  > 微服务框架，简化了 Spring 新程序的开发过程。
- [Swagger](http://swagger.io/)
  > Swagger 是一个规范且完整的框架，提供描述、生产、消费和可视化 RESTful Web Service。
- [Apache Shiro](http://shiro.apache.org/)：执行认证、授权、加密和会话管理。
- [Spring Security](http://projects.spring.io/spring-security/)：专注认证、授权和多维度攻击防护框架。

## 网络爬虫

- [Apache Nutch](http://nutch.apache.org/)：可用于生产环境的高度可扩展、可伸缩的网络爬虫。
- [Crawler4j](https://code.google.com/p/crawler4j/)：简单的轻量级爬虫。
- [JSoup](http://jsoup.org/)：抓取、解析、操作和清理 HTML。

## 服务器

- [Apache Tomcat](http://tomcat.apache.org/)：针对 Servlet 和 JSP 的应用服务器，健壮性好且适用性强。
- [Jetty](http://www.eclipse.org/jetty/)：轻量级、小巧的应用服务器，通常会嵌入到项目中。
- [undertow](https://github.com/undertow-io/undertow): 基于 NIO 实现的高并发轻量级的服务器

## 数据库相关

- [druid](https://github.com/alibaba/druid)
- [HikariCP](https://github.com/brettwooldridge/HikariCP)
- [mybatis](http://www.mybatis.org)
  - [MyBatis-Plus(mybatis 插件)](http://mp.baomidou.com/)
  - [fluent-mybatis](https://gitee.com/fluent-mybatis/fluent-mybatis)
- [jooq](https://www.jooq.org/)
- [shardingjdbc](https://shardingsphere.apache.org/document/current/cn/overview/)
- https://www.liquibase.org/
  > 文档：https://www.liquibase.org/documentation/changes/create_table.html
- https://flywaydb.org/

## 定时任务开源框架

- http://www.quartz-scheduler.org/
- http://elasticjob.io/docs/elastic-job-lite/00-overview
- https://github.com/ltsopensource/light-task-scheduler

## java 工具包

- [hutool](https://gitee.com/loolly/hutool)
- json 工具包
  - [Jsonpath](https://github.com/json-path/JsonPath)
  - [fastjson](https://github.com/alibaba/fastjson)
  - [gson](https://github.com/google/gson)
- 高可用工具
  - https://github.com/resilience4j/resilience4j
  - https://github.com/alibaba/Sentinel
- 日志
  - [Apache Log4j2](http://logging.apache.org/log4j/2.x/)：对之前版本进行了完全重写。现在的版本具备一个强大的插件和配置架构。
  - [Logback](http://logback.qos.ch/)：Log4j 原班人马作品。被证明是一个强健的日志函数库，通过 Groovy 提供了很多有意思的配置选项。
  - [SLF4J](http://www.slf4j.org/)：日志抽象层，需要与某个具体日志框架配合使用。
- 网络编程函数库
  - [Netty](http://netty.io/)：构建高性能网络应用程序开发框架。
  - [OkHttp](http://square.github.io/okhttp/) ：一个 Android 和 Java 应用的 HTTP+SPDY 客户端。
- ci/cd client
- [jenkins-client](https://github.com/RisingOak/jenkins-client.git)
- [java-gitlab-api](https://github.com/timols/java-gitlab-api.git)

## 分布式缓存

- [Hazelcast](https://hazelcast.org/)：Highly scalable in-memory datagrid with a free open-source version.

## 微服务脚手架

- [jhipster](http://www.jhipster.tech/)
  > 中文指南：https://www.jhipster-cn.tech，开发笔记：https://jh.jiankangsn.com/
- [阿里出品 nacos](https://qbgbook.gitbooks.io/spring-boot-reference-guide-zh/content/)
- [阿里出品 sofa](https://www.sofastack.tech/)
- https://github.com/thinkgem/jeesite
- http://git.oschina.net/naan1993/guns
- http://git.oschina.net/ixion/NUTZ-ONEKEY
- http://git.oschina.net/babaio/renren-security
- http://git.oschina.net/babaio/renren-security-boot
- https://gitee.com/iBase4J/iBase4J
- [SpringBlade 微服务开发平台](https://gitee.com/smallc/SpringBlade)
  > 配套前端: [Saber](https://gitee.com/smallc/Saber)
- [Mica，Spring Cloud 微服务开发核心包，支持 web 和 webflux](https://gitee.com/596392912/mica)
- [jeecg-boot 低代码开发平台](https://github.com/jeecgboot/jeecg-boot)
- [RuoYi v3.6.3 基于 Vue/Element UI 和 Spring Boot/Spring Cloud & Alibaba 前后端分离的分布式微服务架构](https://gitee.com/y_project/RuoYi-Cloud)
- [pig](https://gitee.com/log4j/pig)
  > 基于 Spring Cloud 、Spring Boot、 OAuth2 的 RBAC 企业快速开发平台  
  > [pig-ui](https://gitee.com/log4j/pig-ui): pig-ui 是一个为 PIGCLOUD 微服务开发平台开发的前端项目
- [fileex 一款基于 netty、http1.1 transfer-encoding:chunked、websocket 实现的大文件分块上传断点续传处理器](https://gitee.com/gaojunjie03/fileex)
- [Cloud-Platform](https://gitee.com/geek_qi/cloud-platform): Spring Cloud 微服务化开发平台
- [eladmin](https://github.com/elunez/eladmin)
  > eladmin jpa 版本：项目基于 Spring Boot 2.7.18、 Jpa、 Spring Security、Redis、Vue 的前后端分离的后台管理系统
- [hsweb](https://github.com/hs-web/hsweb-framework)
  > hsweb (haʊs wɛb) 是一个基于 spring-boot 2.x 开发
- [blade-tool](https://gitee.com/596392912/mica)
- [wecode](https://github.com/is-m/wecode)
- [RuoYi v3.6.3 基于 Vue/Element UI 和 Spring Boot/Spring Cloud & Alibaba 前后端分离的分布式微服务架构](https://gitee.com/y_project/RuoYi-Cloud)
- [mcms](https://gitee.com/mingSoft/MCMS)
- [jeesite4-cloud](https://gitee.com/thinkgem/jeesite-cloud)
  > 功能简单，很多工程为引用开源项目，如 eureka/nacos/sentinel dashboard
- [kt-upms](https://gitee.com/javis_code/kt-upms)
  > 分布式权限中心

## java 内嵌 nodejs

- https://github.com/nodyn/nodyn
- https://github.com/apigee/trireme
- https://github.com/eclipsesource/J2V8

## 全栈虚拟机

https://www.graalvm.org/

## awesome-java

- [awesome-java](https://github.com/akullpp/awesome-java)

## 云服务

- [Heroku](https://www.heroku.com/)
- [appfog](https://www.ctl.io/appfog/)
- [Mendix](https://www.mendix.com/)
  > 低代码开发平台

## 服务编排

- https://github.com/Netflix/conductor

## 单点登录

- [cas](https://github.com/apereo/cas)
  > [cas-overlay-template](https://github.com/apereo/cas-overlay-template)
- https://www.jianshu.com/p/5a8e3417a8f6
- https://segmentfault.com/a/1190000022990791
- https://www.jianshu.com/p/165c54fc91bc

## 文件文档在线预览

- [kkFileView](https://kkview.cn/zh-cn/index.html)
  > [Spring Boot 整合 MinIO 实现文件存储的完整方案](https://mp.weixin.qq.com/s/T0ZmZH8pFcYMVTqntbYzyA)

## spring cloud 快速部署
- 服务发现
  - Spring Cloud Eureka
  - Consul
  - [Nacos Docker 快速开始](https://nacos.io/docs/next/quickstart/quick-start-docker/)
- [Sentinel Dashboard 快速开始](https://sentinelguard.io/zh-cn/docs/dashboard.html)
- 调用链
  - [Zipkin Sever 快速开始](https://zipkin.io/pages/quickstart.html)
    - [docker 启动](https://github.com/openzipkin-attic/docker-zipkin/blob/master/docker-compose.yml)
    - [jar 包启动](https://zipkin.io/pages/quickstart.html)
    - [源码启动](https://zipkin.io/pages/quickstart.html)

## java 基础技术

- [深入理解 JVM 类加载机制](https://juejin.im/post/6844903806468112398)
- [JAVA 线上故障排查完整套路，从 CPU、磁盘、内存、网络、GC 一条龙！](https://mp.weixin.qq.com/s/aqvXXdrJyslXuhXE6IqYfw)
- [记一次 JAVA 的内存泄露分析](https://mp.weixin.qq.com/s/aAJietPQH1XFy2oRDU2d4A)
- [一文掌握开发利器：正则表达式](https://cloud.tencent.com/developer/article/1699584)
- [写一个通用的幂等组件，我觉得很有必要](https://cloud.tencent.com/developer/article/1696842)
- [传说中的 jwt，我们来征服一下](https://juejin.im/post/6883644756736360455)
- [深入浅出反射](https://zhuanlan.zhihu.com/p/21423208)
- [统一异常处理介绍及实战](https://mp.weixin.qq.com/s/K4xb-3apatkABx6PcZj0hw)
- [统一异常处理介绍及实战](https://www.jianshu.com/p/3f3d9e8d1efa)
- [Spring Cache，从入门到真香](https://juejin.im/post/6882196005731696654)
- [对微服务架构设计实践中若干问题的探讨](https://developer.51cto.com/art/202009/626898.htm)
- [SpringBoot 官方支持任务调度框架，轻量级用起来也挺香！](https://juejin.im/post/6885869364180942862)
- [如何优雅的转换 Bean 对象?](https://mp.weixin.qq.com/s/HgtYxb9kfOu8jjxR2SELVQ)
- [几种缓存更新的设计方法，值得一看](https://segmentfault.com/a/1190000037509415)
- [还在用 Guava Cache？它才是 Java 本地缓存之王](https://cloud.tencent.com/developer/article/1697228)
- [Clickhouse 替代 ES 后，日志查询速度提升了 38 倍！](https://mp.weixin.qq.com/s/fzgrs8_dOpv2bB4oQHli5A)
- [20 张图搞懂「分布式事务」](https://juejin.im/post/6874788280378851335)
- [关于分布式锁原理的一些学习与思考-redis 分布式锁，zookeeper 分布式锁](https://cloud.tencent.com/developer/article/1431068)
- [这 9 个 Java 开源项目 yyds](https://mp.weixin.qq.com/s/Ygv3EN788RV-V_NXlxffgg)
- [Spring Boot + Flowable：可视化工作流引擎实战，让复杂业务流程零代码落地！](https://mp.weixin.qq.com/s/ggZj8IhPJLFxJOstJG42jg)
- [SpringBoot+Jasync 异步化改造狂降 90%耗时，百万并发下的性能杀戮](https://mp.weixin.qq.com/s/Svbgcl_q41wGZdpwNAxq1g)
- [使用 Spring Boot 和 Camunda 开发简单的工作流](https://mp.weixin.qq.com/s/mORIpXjNfWQIjOb3tJPt7Q)
- [Spring Boot + MinIO + KKFile：三步搭建企业级文件预览系统](https://mp.weixin.qq.com/s/agcATju7LRf13IURyVudJg)
- [Spring Boot + LiteFlow：可视化规则引擎，让业务逻辑灵动起舞！](https://mp.weixin.qq.com/s/I55h0i655k9BaTzUnyNYVw)
- [Spring Boot + URule：零代码实现复杂业务规则，可视化规则引擎深度实战](https://mp.weixin.qq.com/s/3t8oRTc3D-zxir_AoRdOPA)
- [别再自己造轮子！Spring Boot 内置的 9 个过滤器用法详解（附代码）](https://mp.weixin.qq.com/s/LRlmE5WWoq6I-pRQzYIGXQ)
- [Spring Boot + Flowable：可视化工作流引擎实战，让复杂业务流程零代码落地！](https://mp.weixin.qq.com/s/ggZj8IhPJLFxJOstJG42jg)
- [SpringBoot 启动从 12s 到 1.3s 的性能杀戮，百万级容器启动优化实战](https://mp.weixin.qq.com/s/EQxHwG7Mnj5IVKRlZGL8HQ)
- [Spring Boot 性能优化：这 3 招让吞吐量直接 “起飞”！](https://mp.weixin.qq.com/s/Gld5BTfN5wVDT6mTL0zIyQ)
- [Spring Boot 实现延时任务的 4 种方式：Redis、RabbitMQ、Quartz、时间轮对比](https://mp.weixin.qq.com/s/XxaQa_PgomD_oLNiMFj8ng)
- [使用 spring-boot 封装 j360](https://github.com/xuminwlt/j360-boot)
- [Spring Boot 集成 MyBatis 的基础项目](https://github.com/abel533/MyBatis-Spring-Boot)
- [Spring Boot 参考指南](https://qbgbook.gitbooks.io/spring-boot-reference-guide-zh/content/)
- [Java 通过 URLClassLoader 让程序支持插件扩展](http://xxgblog.com/2013/07/04/java-urlclassloader-plugin/)
- [Spring Cloud Greenwich.RELEASE Reference](https://www.docs4dev.com/docs/zh/spring-cloud/Greenwich.RELEASE/reference/)
- [netty demo](https://github.com/UVliuwei/netty)
- [Java Websocket 获取客户端 IP 地址](https://www.zhangbj.com/p/797.html)
- [springboot2.0 集成 webSocket](https://www.jianshu.com/p/2c9be4641d43)
- [SpringCloud gateway(疯狂创客圈)](https://www.cnblogs.com/crazymakercircle/p/11704077.html)
- [干掉 if-else 噩梦！这四种设计模式太优雅了！！](https://mp.weixin.qq.com/s/gczPz6WXrMrrHWYZ_Mstig)
- [来吧，用设计模式来干掉 if-else](https://cloud.tencent.com/developer/article/1658355)
- [Crazy-SpringCloud 微服务脚手架](https://gitee.com/crazymaker/crazy-springcloud)
- [spring-boot-vuejs](https://github.com/jonashackt/spring-boot-vuejs)
- https://github.com/pjmike/springboot-netty.git

## 权限认证

- https://segmentfault.com/a/1190000038275203
- https://gitee.com/javis_code/kt-upms
- https://gitee.com/choerodon/iam-service
- https://www.jianshu.com/p/5b8aa8f04b2f
- https://casbin.org/docs/zh-CN/tutorials
- https://www.cnblogs.com/vigoz/p/12984556.html
- https://janche.github.io/2019/07/24/Spring-Security-JWT-%E5%AE%8C%E6%88%90RBAC%E5%8A%A8%E6%80%81%E6%8E%88%E6%9D%83/
- https://juejin.cn/post/6995177894850854943
- https://blog.csdn.net/zhenghongcs/article/details/120428172
