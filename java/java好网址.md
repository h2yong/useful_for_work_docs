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

## 日志

- [Apache Log4j2](http://logging.apache.org/log4j/2.x/)：对之前版本进行了完全重写。现在的版本具备一个强大的插件和配置架构。
- [Logback](http://logback.qos.ch/)：Log4j 原班人马作品。被证明是一个强健的日志函数库，通过 Groovy 提供了很多有意思的配置选项。
- [SLF4J](http://www.slf4j.org/)：日志抽象层，需要与某个具体日志框架配合使用。
- [kibana](https://www.elastic.co/products/kibana)：对日志进行分析并进行可视化。
- [logstash](https://www.elastic.co/products/logstash)：日志文件管理工具。

## 网络编程函数库

- [Netty](http://netty.io/)：构建高性能网络应用程序开发框架。
- [OkHttp](http://square.github.io/okhttp/) ：一个 Android 和 Java 应用的 HTTP+SPDY 客户端。
- [commons-net](https://mvnrepository.com/artifact/commons-net/commons-net) : Apache Commons Net library contains a collection of network utilities and protocol implementations. Supported protocols include: Echo, Finger, FTP, NNTP, NTP, POP3(S), SMTP(S), Telnet, Whois

## 安全

- [Apache Shiro](http://shiro.apache.org/)：执行认证、授权、加密和会话管理。
- [Spring Security](http://projects.spring.io/spring-security/)：专注认证、授权和多维度攻击防护框架。

## 测试

- [assertj](https://assertj.github.io/doc/)：支持流式断言提高测试的可读性
- [truth](https://github.com/google/truth)：来自 Google 用于 Java 单元测试断言/命题框架
- [assertj-db](http://joel-costigliola.github.io/assertj/assertj-db.html)：数据库流式断言
- [junit](http://junit.org/junit4/)：单元测试框架
- [testng](http://testng.org/doc/index.html)：单元测试框架
- [mockito](http://code.google.com/p/mockito/)：在自动化单元测试中创建测试对象，为 TDD 或 BDD 提供支持
- [powermock](https://github.com/powermock/powermock)：PowerMock 扩展了 EasyMock 和 Mockito 框架，增加了对 static 和 final 方法 mock 支持等功能
- [rest-assured](http://rest-assured.io/)：rest 服务测试框架
- [fitnesse](http://www.fitnesse.org/FitNesseFeatures)：使用 wiki 的测试框架
- [cucumber](https://cucumber.io)：行为驱动开发测试框架
- [dbunit](http://dbunit.sourceforge.net/)：junit 插件，用于数据库单元测试
- [spring-test-dbunit](https://github.com/springtestdbunit/spring-test-dbunit)
- [JTester](https://code.google.com/archive/p/java-tester/)：JTester 是站在众多巨人肩膀上的单元测试框架，集成了 Junit4.5，dbunit2.4.3，unitils2.2，JMOCK2.5 和 TestNg5.1 这些优秀的开源框架
- [spock](http://spockframework.org)：Spock 框架是基于 Groovy 语言的测试框架，Groovy 与 Java 具备良好的互操作性，因此可以在 Spring Boot 项目中使用该框架写优雅、高效以及 DSL 化的测试用例
- [nosql-unit](https://github.com/lordofthejars/nosql-unit)：NoSQL Unit is a JUnit extension that helps you write NoSQL unit tests
- [test4j](https://github.com/test4j/test4j): an open source for java test

## web 自动化测试

- [Selenium](http://docs.seleniumhq.org/)：为 Web 应用程序提供可移植软件测试框架
- [htmlunit](http://htmlunit.sourceforge.net/)：HtmlUnit 是 JUnit 的扩展测试框架之一，用于 html 单元测试
- [httpunit](http://httpunit.sourceforge.net/)：HttpUnit 对网络应用程序进行自动完善和测试的 JAVA 类库程序
- [karate](https://github.com/intuit/karate)：Web-Services Testing Made Simple

## 性能测试

- http://naver.github.io/ngrinder/
- http://gettaurus.org/
- http://locust.io

## Web 框架

- [Springmvc](http://projects.spring.io/spring-framework/)：Spring MVC 属于 SpringFrameWork 的后续产品。
- [spring-boot](http://projects.spring.io/spring-boot/)：微框架，简化了 Spring 新程序的开发过程。
- [Swagger](http://swagger.io/)：Swagger 是一个规范且完整的框架，提供描述、生产、消费和可视化 RESTful Web Service。

## 网络爬虫

- [Apache Nutch](http://nutch.apache.org/)：可用于生产环境的高度可扩展、可伸缩的网络爬虫。
- [Crawler4j](https://code.google.com/p/crawler4j/)：简单的轻量级爬虫。
- [JSoup](http://jsoup.org/)：抓取、解析、操作和清理 HTML。

## 服务器

- [Apache Tomcat](http://tomcat.apache.org/)：针对 Servlet 和 JSP 的应用服务器，健壮性好且适用性强。
- [Jetty](http://www.eclipse.org/jetty/)：轻量级、小巧的应用服务器，通常会嵌入到项目中。
- [undertow](https://github.com/undertow-io/undertow): 基于 NIO 实现的高并发轻量级的服务器

## 内存数据库

- [H2](http://h2database.com/html/main.html)：小型 SQL 数据库，以内存操作著称。

## 数据库更新工具

- https://www.liquibase.org/
  > 文档：https://www.liquibase.org/documentation/changes/create_table.html
- https://flywaydb.org/

## 数据库连接池

- [druid](https://github.com/alibaba/druid)
- [HikariCP](https://github.com/brettwooldridge/HikariCP)

## ORM 框架

- [mybatis](http://www.mybatis.org)
- mybatis 插件：http://mp.baomidou.com/
- mybatis 插件：http://www.mybatis.tk/
- [jooq](https://www.jooq.org/)

## 数据库读写分离框架

- [shardingjdbc](https://shardingsphere.apache.org/document/current/cn/overview/)

## java 定时任务开源框架

- http://www.quartz-scheduler.org/

## 分布式定时任务开源框架

- http://elasticjob.io/docs/elastic-job-lite/00-overview
- https://github.com/ltsopensource/light-task-scheduler
- http://code.taobao.org/p/tbschedule/wiki/index
- https://github.com/uncodecn/uncode-schedule

## 内嵌式 NoSQL

- https://github.com/mwarc/embedded-memcached-spring
- https://github.com/kstyrc/embedded-redis

## 分布式缓存

- [Hazelcast](https://hazelcast.org/)：Highly scalable in-memory datagrid with a free open-source version.

## mock-server 框架

- http://www.mock-server.com/
- https://github.com/dreamhead/moco

## 微服务脚手架

- [jhipster](http://www.jhipster.tech/)，中文指南：https://www.jhipster-cn.tech，开发笔记：https://jh.jiankangsn.com/
- [阿里出品 nacos](https://qbgbook.gitbooks.io/spring-boot-reference-guide-zh/content/)
- [阿里出品 sofa](https://www.sofastack.tech/)
- https://github.com/thinkgem/jeesite
- http://git.oschina.net/jeecg/jeecg
- http://git.oschina.net/naan1993/guns
- http://git.oschina.net/ixion/NUTZ-ONEKEY
- http://git.oschina.net/babaio/renren-security
- http://git.oschina.net/babaio/renren-security-boot
- https://www.oschina.net/p/apollo-ctrip
- https://gitee.com/iBase4J/iBase4J

## jsp 布局框架

- https://github.com/sitemesh/sitemesh3

## java 工具包

- https://gitee.com/loolly/hutool
- http://feilong-core.mydoc.io

## json 工具包

- [Jsonpath](https://github.com/json-path/JsonPath)
- [fastjson](https://github.com/alibaba/fastjson)
- [gson](https://github.com/google/gson)

## java 内嵌 nodejs

- https://github.com/nodyn/nodyn
- https://github.com/apigee/trireme
- https://github.com/eclipsesource/J2V8

## 全栈虚拟机

https://www.graalvm.org/

## 高可用工具

- https://github.com/resilience4j/resilience4j
- https://github.com/alibaba/Sentinel

## java 优秀项目

- [jenkins-client](https://github.com/RisingOak/jenkins-client.git)
- [java-gitlab-api](https://github.com/timols/java-gitlab-api.git)
- [mycat：mysql 中间件](http://mycat.io/)
- [cobar：mysql 中间件](https://github.com/alibaba/cobar.git)

## spring 相关文章

- [spring-common-application-properties](https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html)
- [使用 spring-boot 封装 j360](https://github.com/xuminwlt/j360-boot)
- [Spring Boot 集成 MyBatis 的基础项目](https://github.com/abel533/MyBatis-Spring-Boot)
- [Spring Boot 参考指南](https://qbgbook.gitbooks.io/spring-boot-reference-guide-zh/content/)
- [Java 通过 URLClassLoader 让程序支持插件扩展](http://xxgblog.com/2013/07/04/java-urlclassloader-plugin/)

## 单元测试文章

- https://skyao.gitbooks.io/learning-java-unit-test/content/assertj/
- https://skyao.gitbooks.io/learning-java-unit-test/content/powermock/
- https://skyao.gitbooks.io/learning-java-unit-test/content/mockito/
- https://github.com/kkapelon/java-testing-with-spock

## 优秀 java 相关资料

- http://www.mybatis.org/mybatis-3/zh/dynamic-sql.html
- http://git.oschina.net/free/Mybatis_Utils/blob/master/MybatisGeneator/MybatisGeneator.md

## awesome-java

- [awesome-java](https://github.com/akullpp/awesome-java)

## 开源 git web 工具

| 工具名称                                      | Language |
| --------------------------------------------- | -------- |
| [gitlab](https://about.gitlab.com/)           | ruby     |
| [gitblit](http://gitblit.com/)                | java     |
| [gitbucket](https://gitbucket.github.io/)     | java     |
| [gitiles](https://github.com/google/gitiles/) | java     |
| [gerrit](https://www.gerritcodereview.com/)   | java     |

## 云服务

- http://rancher.com/catalog-items/
- [Heroku](https://www.heroku.com/)
- [appfog](https://www.ctl.io/appfog/)
- [cloudbees](https://www.cloudbees.com/)
- [OpenShift](https://www.openshift.com/)
- [Mendix](https://www.mendix.com/)
- [MioSoft](https://www.miosoft.com/)
- [Engine Yard Cloud](http://www.engineyard.com/)

## 接口测试文章收集

- https://www.kancloud.cn/digest/dqappinterface/120089
- [有赞分层自动化测试实践](http://tech.youzan.com/layers_test_automation_practice/)
- [接口测试-分层测试重构之接口层](https://testerhome.com/topics/4284)
- [PhoenixFramework 自动化测试平台](http://www.cewan.la/)
- [自动化测试工具 Fitnesse+RestFixture](https://testerhome.com/topics/1277)

## 移动跨平台开发

- https://github.com/NervJS/taro
- https://github.com/Meituan-Dianping/mpvue
- https://uniapp.dcloud.io/

## PC 跨平台开发

https://electronjs.org/

## 开发工具使用教程

- [猴子都能懂的 GIT 入门](https://backlog.com/git-tutorial/cn/)
- [IntelliJ IDEA 使用教程](http://wiki.jikexueyuan.com/project/intellij-idea-tutorial/)

## devops 平台

- [jenkins](https://jenkins.io/zh/)
- [TFS](https://visualstudio.microsoft.com/zh-hans/tfs/)

## 服务编排

- https://github.com/Netflix/conductor

## 基础设施即代码

- https://www.terraform.io/docs/cli-index.html

## springboot 集成 vuejs

- https://github.com/jonashackt/spring-boot-vuejs

## java 开发框架

- [Mica，Spring Cloud 微服务开发核心包，支持 web 和 webflux](https://gitee.com/596392912/mica)
- [jeecg-boot 低代码开发平台](https://github.com/jeecgboot/jeecg-boot)
- [RuoYi v3.6.3 基于 Vue/Element UI 和 Spring Boot/Spring Cloud & Alibaba 前后端分离的分布式微服务架构](https://gitee.com/y_project/RuoYi-Cloud)
- https://gitee.com/log4j/pig
- [fileex 一款基于 netty、http1.1 transfer-encoding:chunked、websocket 实现的大文件分块上传断点续传处理器](https://gitee.com/gaojunjie03/fileex)

## 测试开源平台

- [MeterSphere 一站式开源持续测试平台](https://github.com/metersphere/metersphere)

## 单点登录

- [cas](https://github.com/apereo/cas)
  > [cas-overlay-template](https://github.com/apereo/cas-overlay-template)

## 文件文档在线预览

- [kkFileView](https://kkview.cn/zh-cn/index.html)
    > [Spring Boot 整合 MinIO 实现文件存储的完整方案](https://mp.weixin.qq.com/s/T0ZmZH8pFcYMVTqntbYzyA)