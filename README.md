# CangqiongTakeOut-toStudy
全栈项目（Web、微信小程序）学习用
苍穹外卖

流程参考：（需求说明书+产品原型） -> （总体设计）UI设计、数据库设计、接口设计 -> 详细设计+编码+单元测试 -> 测试 -> 上线运维

需求说明书+产品原型：
说明技术选型
![1724840801499](https://github.com/user-attachments/assets/8b9b0c40-2b96-4ef7-8dc4-98a81c5a58b4)

Maven分模块开发:
Sky-common 存放公共类（工具类、常量类、异常类）
Sky-POJO 实体类、VO(视图对象)、DTO(数据传输对象-程序各层间传递数据)
Sky-server 后端服务、配置文件、拦截器、Controller、Server、Mapper

JWT:JSON Web Token,是一种基于JSON的开放标准，用于在各方之间作为JSON对象安全地传输信息，常用于身份验证和信息交换。Header-Payload-Signature，

开发流程：

订制接口->前后端开发->联调->提测

后端测试Swagger

开发注意事项：

使用常量类初始化默认信息

ThreadLocal-Tomcat中每次请求都是一个线程，每个线程具有单独的存储空间-可以据此传递变量的值

node.js版本14.20.0（尚存部分前端依赖报错问题，目前无影响）
