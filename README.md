# CangqiongTakeOut-toStudy
全栈项目（Web、微信小程序）学习用
苍穹外卖

#### 流程参考：

（需求说明书+产品原型） -> （总体设计）UI设计、数据库设计、接口设计 -> 详细设计+编码+单元测试 -> 测试 -> 上线运维

需求说明书+产品原型：
说明技术选型
![1724840801499](https://github.com/user-attachments/assets/8b9b0c40-2b96-4ef7-8dc4-98a81c5a58b4)

#### Maven分模块开发:

Sky-common 存放公共类（工具类、常量类、异常类）
Sky-POJO 实体类、VO(视图对象)、DTO(数据传输对象-程序各层间传递数据)
Sky-server 后端服务、配置文件、拦截器、Controller、Server、Mapper

#### JWT:

JSON Web Token,是一种基于JSON的开放标准，用于在各方之间作为JSON对象安全地传输信息，常用于身份验证和信息交换。Header-Payload-Signature，

#### 前后端编码开发流程：

订制接口->前后端开发->联调->提测

后端测试Swagger

#### 开发注意事项：

使用常量类初始化默认信息

ThreadLocal-Tomcat中每次请求都是一个线程，每个线程具有单独的存储空间-可以据此传递变量的值

node.js版本14.20.0（尚存部分前端依赖报错问题，目前无影响）

#### 公共字段自动填充

问题：后端存在冗余代码，不便维护

解决：切面拦截（AOP面向切面编程-不修改源代码，为系统中的业务组件添加通用功能）

#### 同时操作多个数据表

@Transactional注解-确保操作的原子性，同时成功或同时失败。

#### 文件上传

OSS对象存储服务器-UUID（通用唯一标识符）实现文件名去重

#### Redis

Spring Data Redis

基于内存的键值对结构数据库

特点：基于内存存储，存储热点数据

数据类型（key-字符串，value-（String、hash（类Java HashMap）、list、set（无序集合）、sorted set））

#### 小知识补充

##### HTTP组成部分、参数类型、处理方法

请求报文：请求行（请求协议+请求URL地址+请求方法）+请求头（Authorization-token）+请求数据（URL参数/content-type(默认格式、form-data上传文件、json)）

响应报文：状态行（code）+消息报头+响应正文

HTTP参数类型（请求头参数（head）、路径参数（path）、查询参数（query）、请求体参数（body））

路径参数{x}-@PathVariable 映射URL绑定的占位符

Query（HTTP查询参数-？之后）-参数名接收/@RequestParam接收或映射

Body请求体参数（json）-@RequestBody

后端服务器会根据不同的HTTP方法（Post\Put\Get）执行不同的处理函数

##### RESTFUL API:

接口规范

GET（安全且幂等）

POST（不安全且不幂等）

PUT（不安全但幂等）

DELETE（不安全但幂等）

错误码-200（OK）、400（坏请求-参数错误）、401（未授权）、404（资源不存在）、406（服务端不支持-后端返回结果前端无法解析）、500（通用错误响应）

##### Mybatis:

```
useGeneratedKeys="true" keyProperty="id"
```

-插入记录后获取数据库自动生成的主键ID，主键ID保存在实体类中（建立关联表时使用）

分页查询Page（page.getTotal-获取查询结果的记录数，page.getResult-获取查询结果列表，page（long current, long size）-根据当前页码和每页记录数创建分页对象）

resultType从数据库提取数据 parameterType向数据库存入数据

##### lombok注解：

@Slf4j-日志输出（log.info）

#### 前端（解耦-存放静态资源）

##### css

块元素-行内元素-行内块元素（三者可通过display互相转换）

盒子模型（控制布局）-网页的每个元素可视作盒子，由于context-内边距-边框-外边距组成

布局方式：

1.标准流

2.浮动（float）-元素顶端对齐同行排列  父元素清除浮动（保障显示正常、无元素重叠，overflow）

3.定位：

3.1相对定位 position:relative + left/right/top/bottom

3.2绝对定位（脱离文档流） position:absolute + 位移

3.3固定定位（脱离文档流） position:fixed

##### Js

var变量-函数作用域 let变量-块作用域 const常量

事件（onClick、onMouseOver鼠标经过）

DOM-Js编程接口(传统用法)

async通过同步的方式执行异步任务

#### 响应式布局（css+Js联合实现）

meta标签	rem单位（font-size倍数）	wh/vh单位

Flex弹性盒子-（main axis\cross axis\main size\cross size）

#### Vue

Js框架 特点（响应式编程-不再操作dom对象-MVVM实现数据的双向绑定、组件化）

生命周期（创建-挂载-更新-销毁）

生命周期钩子

app.vue-主组件，页面入口文件

#### Ajax

前后端异步通信，等待响应过程中前端不会阻塞页面。

#### Axios

HTTP客户端，从node.js发出http请求，拦截请求和响应。
