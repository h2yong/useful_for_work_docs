
jooq系列教程：https://jooq.diamondfsd.com/learn/section-1-how-to-start.html
https://github.com/jasonqu/jooq-cookbook#tip-5-生成接口
https://jooq.diamondfsd.com/learn/section-3-process-result.html
https://spring.hhui.top/spring-blog/2020/12/05/201204-SpringBoot系列Jooq之聚合查询/
https://github.com/liuyueyi/spring-boot-demo
https://developer.aliyun.com/article/711552
https://github.com/pkainulainen/jooq-with-spring-examples


Jooq的优点
1. DSL(Domain Specific Language )风格，代码够简单和清晰。遇到不会写的sql可以充分利用IDEA代码提示功能轻松完成。
2. 保留了传统ORM 的优点，简单操作性，安全性，类型安全等。不需要复杂的配置，并且可以利用Java 8 Stream API 做更加复杂的数据转换。
3. 支持主流的RDMS和更多的特性，如self-joins，union，存储过程，复杂的子查询等等。
4. 丰富的Fluent API和完善文档。
5. runtime schema mapping 可以支持多个数据库schema访问。简单来说使用一个连接池可以访问N个DB schema，使用比较多的就是SaaS应用的多租户场景。
