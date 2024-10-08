# CangqiongTakeOut-toStudy
全栈项目（Web、微信小程序）学习用
苍穹外卖

#### 流程参考

（需求说明书+产品原型） -> （总体设计）UI设计、数据库设计、接口设计 -> 详细设计+编码+单元测试 -> 测试 -> 上线运维

需求说明书+产品原型：
说明技术选型
![1724840801499](https://github.com/user-attachments/assets/8b9b0c40-2b96-4ef7-8dc4-98a81c5a58b4)

#### Maven分模块开发

Sky-common 存放公共类（工具类、常量类、异常类）
Sky-POJO 实体类、VO(视图对象)、DTO(数据传输对象-程序各层间传递数据)
Sky-server 后端服务、配置文件、拦截器、Controller、Server、Mapper

#### JWT

JSON Web Token,是一种基于JSON的开放标准，用于在各方之间作为JSON对象安全地传输信息，常用于身份验证和信息交换。Header-Payload-Signature，

#### 前后端编码开发流程

订制接口->前后端开发->联调->提测

后端测试Swagger

#### 开发注意事项

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

设置redis key的序列化器（new StringRedisSerializer()）-便于使用不同方式查看Redis key

#### Spring Cache

基于注解的缓存功能，底层缓存实现（EHCache、Caffeine、Redis）

@Cacheable-缓存中存在数据，返回缓存数据；缓存中没有数据，调用方法并将方法返回值放到缓存中。

@CacheEvict-从缓存中删除一条或多条数据。

@CachePut-将方法返回值放到缓存中

SpringCache的key生成-@CachePut(cacheNames = "xxxx",key="#形参.属性")-生成的key:cacheNames::形参.属性

删除缓存中的全部键值对-@CacheEvict(cacheNames = "xxxx",allEntries = true)

#### HttpClient

创建HttpClient对象->创建请求方法实例并指定URL（GET/POST）->setEntity设置请求参数->调用execute发送请求返回Response对象->获取响应头/响应体->关闭资源（response/httpclient）

#### 订单支付(微信支付)

JSAPI下单-调用接口在微信支付服务后台生成预支付交易单

小程序调起支付API

#### 内网穿透

将自己的主机作为服务器，使外网能够访问内网。

用途：开发过程中的功能测试

#### Spring Task

定时任务框架，任务调度工具，按约定时间自动执行代码逻辑

cron表达式-定义任务触发的时间

#### WebSocket（长连接）

基于TCP的网络协议

全双工通信（建立连接后可进行持久双向的数据传输）

@OnOpen-连接成功建立调用方法

@OnMessage-收到客户端消息调用方法

#### HTTP组成部分、参数类型、处理方法（短连接、单向（请求响应模式））

请求报文：请求行（请求协议+请求URL地址+请求方法）+请求头（Authorization-token）+请求数据（URL参数/content-type(默认格式、form-data上传文件、json)）

响应报文：状态行（code）+消息报头+响应正文

HTTP参数类型（请求头参数（head）、路径参数（path）、查询参数（query）、请求体参数（body））

路径参数{x}-@PathVariable 映射URL绑定的占位符

Query（HTTP查询参数-？之后）-参数名接收/@RequestParam接收或映射

Body请求体参数（json）-@RequestBody

后端服务器会根据不同的HTTP方法（Post\Put\Get）执行不同的处理函数

#### RESTFUL API:

接口规范

GET（安全且幂等）

POST（不安全且不幂等）

PUT（不安全但幂等）

DELETE（不安全但幂等）

错误码-200（OK）、400（坏请求-参数错误）、401（未授权）、404（资源不存在）、406（服务端不支持-后端返回结果前端无法解析）、500（通用错误响应）

#### Mybatis:

```
useGeneratedKeys="true" keyProperty="id"
```

-插入记录后获取数据库自动生成的主键ID，主键ID保存在实体类中（建立关联表时使用）

分页查询Page（page.getTotal-获取查询结果的记录数，page.getResult-获取查询结果列表，page（long current, long size）-根据当前页码和每页记录数创建分页对象）

resultType从数据库提取数据 parameterType向数据库存入数据

#### lombok注解：

@Slf4j-日志输出（log.info）

#### Hash算法

散列算法-结点key通过散列函数计算得出value的存储地址-实现存储和检索。

#### 设计模式

##### 创建型模式

工厂模式——（简单工厂模式）定义创建对象的类，由此类封装实例化对象的行为。——（工厂方法模式）定义创建对象的接口，由子类决定要实例化的类。（对象的实例化推迟到子类）——（抽象工厂模式）定义接口用于创建相关或有依赖关系的对象族。

##### 结构型模式

装饰器模式——在不改变原有对象的情况下扩展功能（BufferedReader/Reader）

适配器模式——接口互不兼容的类的协调工作（InputStream/InputStreamReader）

##### 行为型模式

观察者模式——文件目录监听服务

#### Spring

IOC

AOP

注入Bean的注解-@Autowired（默认byType）/@Resource（默认byName）

#### 数据库

候选码

主码

E-R图：实体、属性、联系

关系型数据库-

##### 数据库范式

1NF——属性不可再分

2NF——1NF基础上，消除非主属性对于码的部分函数依赖

3NF——2NF基础上，消除非主属性对于码的传递函数依赖

##### 锁

InnoDB支持行级锁和表级锁

##### 事务

ACID

原子性——事务中的操作，全部完成或全部不完成

一致性——数据一致性

隔离性——数据库允许并发事务同时进行数据读写和修改，隔离性防止多个事务并发执行导致数据的不一致

持久性——事务处理结束后，对数据的修改是永久的

##### 索引



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

main.js-整个项目的入口文件

vue.config.js-vueCli配置文件(修改前端项目的端口号、配置代理proxy-解决跨域问题)

vue组件（结构（只有一个根元素 ）、样式、逻辑）

文本插值：绑定data方法返回的对象属性-用法：{{data中的属性名称}}-可对属性进行简单计算（如三目运算符）

属性绑定：v-bind:xxx/:xxx

事件绑定：v-on:xxx/@xxx-为元素绑定对应的事件（函数/方法）

双向绑定：v-model-表单输入项和data方法中的属性绑定-任何一方的改变都会同步给另一方

条件渲染：v-if、v-else、v-else-if

#### Ajax

前后端异步通信，等待响应过程中前端不会阻塞页面。

#### Axios

基于promise的HTTP客户端，从node.js发出http请求，拦截请求和响应。

跨域问题（前端直接根据端口号请求后端失败）

.then(res => {})-请求成功的回调函数 

.catch(error => { console.log(error, reponse)})-请求失败的回调函数

axios.post/axios.get-URL后的参数可通过配置对象设置信息-通过{headers：{}}指定请求头信息

axios统一使用方式

axios({

​	method: 'post/get',

​	url: '/xxx/xxx',

​	headers: { 'xxxx': 'xxxx'},

​	data: {

​		xxx: 'xxx',

​		xxx: 'xxx'

​	}

})
