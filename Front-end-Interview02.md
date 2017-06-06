## javascript对象的几种创建方式

    1，工厂模式

    2，构造函数模式

    3，原型模式

    4，混合构造函数和原型模式

    5，动态原型模式

    6，寄生构造函数模式

    7，稳妥构造函数模式

## javascript继承的6种方法

    1，原型链继承

    2，借用构造函数继承

    3，组合继承(原型+借用构造)

    4，原型式继承

    5，寄生式继承

    6，寄生组合式继承

[JavaScript继承方式详解](http://segmentfault.com/blog/trigkit4/1190000002440502)

## 创建ajax的过程


    (1)创建`XMLHttpRequest`对象,也就是创建一个异步调用对象.

    (2)创建一个新的`HTTP`请求,并指定该`HTTP`请求的方法、`URL`及验证信息.

    (3)设置响应`HTTP`请求状态变化的函数.

    (4)发送`HTTP`请求.

    (5)获取异步调用返回的数据.

    (6)使用JavaScript和DOM实现局部刷新.


    var xmlHttp = new XMLHttpRequest();

    xmlHttp.open('GET','demo.php','true');

    xmlHttp.send()

    xmlHttp.onreadystatechange = function(){

        if(xmlHttp.readyState === 4 & xmlHttp.status === 200){

        }

    }


详情：[JavaScript学习总结（七）Ajax和Http状态字][10]

## 异步加载和延迟加载

    1.异步加载的方案： 动态插入script标签

    2.通过ajax去获取js代码，然后通过eval执行

    3.script标签上添加defer或者async属性

    4.创建并插入iframe，让它异步执行js

    5.延迟加载：有些 js 代码并不是页面初始化的时候就立刻需要的，而稍后的某些情况才需要的。

##`Flash`、`Ajax`各自的优缺点，在使用中如何取舍？

- `Flash`适合处理多媒体、矢量图形、访问机器；对`CSS`、处理文本上不足，不容易被搜索。

-` Ajax`对`CSS`、文本支持很好，支持搜索；多媒体、矢量图形、机器访问不足。

- 共同点：与服务器的无刷新传递消息、用户离线和在线状态、操作DOM

## 请解释一下 JavaScript 的同源策略。


概念:同源策略是客户端脚本（尤其是`Javascript`）的重要的安全度量标准。它最早出自`Netscape Navigator2.0`，其目的是防止某个文档或脚本从多个不同源装载。


这里的同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议。

指一段脚本只能读取来自同一来源的窗口和文档的属性。

## 为什么要有同源限制？

   我们举例说明：比如一个黑客程序，他利用`Iframe`把真正的银行登录页面嵌到他的页面上，当你使用真实的用户名，密码登录时，他的页面就可以通过`Javascript`读取到你的表单中`input`中的内容，这样用户名，密码就轻松到手了。


缺点：

现在网站的`JS` 都会进行压缩，一些文件用了严格模式，而另一些没有。这时这些本来是严格模式的文件，被 `merge` 后，这个串就到了文件的中间，不仅没有指示严格模式，反而在压缩后浪费了字节。


## GET和POST的区别，何时使用POST？


GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符

POST：一般用于修改服务器上的资源，对所发送的信息没有限制。


GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值，

也就是说Get是通过地址栏来传值，而Post是通过提交表单来传值。



然而，在以下情况中，请使用 POST 请求：

无法使用缓存文件（更新服务器上的文件或数据库）

向服务器发送大量数据（POST 没有数据量限制）

发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠


## 事件、IE与火狐的事件机制有什么区别？ 如何阻止冒泡？



 1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为。

 2. 事件处理机制：IE是事件冒泡、firefox同时支持两种事件模型，也就是：捕获型事件和冒泡型事件。；

 3. `ev.stopPropagation()`;注意旧ie的方法 `ev.cancelBubble = true`;


## ajax的缺点和在IE下的问题？

详情请见：[JavaScript学习总结（七）Ajax和Http状态字][14]

>ajax的缺点


      1、ajax不支持浏览器back按钮。

      2、安全问题 AJAX暴露了与服务器交互的细节。

      3、对搜索引擎的支持比较弱。

      4、破坏了程序的异常机制。

      5、不容易调试。
>IE缓存问题

在IE浏览器下，如果请求的方法是`GET`，并且请求的`URL`不变，那么这个请求的结果就会被缓存。解决这个问题的办法可以通过实时改变请求的`URL`，只要URL改变，就不会被缓存，可以通过在URL末尾添加上随机的时间戳参数(`'t'= + new Date().getTime()`)

>Ajax请求的页面历史记录状态问题

可以通过锚点来记录状态，`location.hash`。让浏览器记录Ajax请求时页面状态的变化。



还可以通过`HTML5`的`history.pushState`，来实现浏览器地址栏的无刷新改变


## 谈谈你对重构的理解

网站重构：在不改变外部行为的前提下，简化结构、添加可读性，而在网站前端保持一致的行为。也就是说是在不改变UI的情况下，对网站进行优化，
在扩展的同时保持一致的UI。


    对于传统的网站来说重构通常是：

    表格(table)布局改为DIV+CSS

    使网站前端兼容于现代浏览器(针对于不合规范的CSS、如对IE6有效的)

    对于移动平台的优化

    针对于SEO进行优化

    深层次的网站重构应该考虑的方面


    减少代码间的耦合

    让代码保持弹性

    严格按规范编写代码

    设计可扩展的API

    代替旧有的框架、语言(如VB)

    增强用户体验

    通常来说对于速度的优化也包含在重构中



    压缩JS、CSS、image等前端资源(通常是由服务器来解决)

    程序的性能优化(如数据读写)

    采用CDN来加速资源加载

    对于JS DOM的优化

    HTTP服务器的文件缓存

## 说说你对Promise的理解



依照 `Promise/A+` 的定义，`Promise` 有四种状态：

	pending: 初始状态, 非 fulfilled 或 rejected.

	fulfilled: 成功的操作.

	rejected: 失败的操作.

	settled: Promise已被fulfilled或rejected，且不是pending



另外， `fulfilled` 与 `rejected` 一起合称 `settled`。



`Promise` 对象用来进行延迟(deferred) 和异步(asynchronous ) 计算。



>Promise 的构造函数



构造一个 `Promise`，最基本的用法如下：


```js
	var promise = new Promise(function(resolve, reject) {

	    if (...) {  // succeed

	        resolve(result);

	    } else {   // fails

	        reject(Error(errMessage));

	    }
	});
```


`Promise` 实例拥有 `then` 方法（具有 `then` 方法的对象，通常被称为 `thenable`）。它的使用方法如下：

```js
promise.then(onFulfilled, onRejected)
```

接收两个函数作为参数，一个在 `fulfilled` 的时候被调用，一个在 `rejected` 的时候被调用，接收参数就是 `future，onFulfilled` 对应 `resolve`, `onRejected` 对应 `reject`。

## 说说你对前端架构师的理解


负责前端团队的管理及与其他团队的协调工作，提升团队成员能力和整体效率；
带领团队完成研发工具及平台前端部分的设计、研发和维护；
带领团队进行前端领域前沿技术研究及新技术调研，保证团队的技术领先
负责前端开发规范制定、功能模块化设计、公共组件搭建等工作，并组织培训。

## 说说严格模式的限制



严格模式主要有以下限制：

    变量必须声明后再使用

    函数的参数不能有同名属性，否则报错

    不能使用with语句

    不能对只读属性赋值，否则报错

    不能使用前缀0表示八进制数，否则报错

    不能删除不可删除的属性，否则报错

    不能删除变量delete prop，会报错，只能删除属性delete global[prop]

    eval不会在它的外层作用域引入变量

    eval和arguments不能被重新赋值

    arguments不会自动反映函数参数的变化

    不能使用arguments.callee

    不能使用arguments.caller

    禁止this指向全局对象

    不能使用fn.caller和fn.arguments获取函数调用的堆栈

    增加了保留字（比如protected、static和interface）



设立"严格模式"的目的，主要有以下几个：


- 消除`Javascript`语法的一些不合理、不严谨之处，减少一些怪异行为;

- 消除代码运行的一些不安全之处，保证代码运行的安全；

- 提高编译器效率，增加运行速度；

- 为未来新版本的`Javascript`做好铺垫。



注：经过测试`IE6,7,8,9`均不支持严格模式。

## 说说你对AMD和Commonjs的理解



`CommonJS`是服务器端模块的规范，Node.js采用了这个规范。`CommonJS`规范加载模块是同步的，也就是说，只有加载完成，才能执行后面的操作。AMD规范则是非同步加载模块，允许指定回调函数。

`AMD`推荐的风格通过返回一个对象做为模块对象，`CommonJS`的风格通过对`module.exports`或`exports`的属性赋值来达到暴露模块对象的目的。

>详情：[也谈webpack及其开发模式](https://segmentfault.com/a/1190000004888589)


## document.write()的用法



` document.write()`方法可以用在两个方面：页面载入过程中用实时脚本创建页面内容，以及用延时脚本创建本窗口或新窗口的内容。

`document.write`只能重绘整个页面。`innerHTML`可以重绘页面的一部分

## 编写一个方法 求一个字符串的字节长度

假设：一个英文字符占用一个字节，一个中文字符占用两个字节


 	function GetBytes(str){
        var len = str.length;
        var bytes = len;
        for(var i=0; i<len; i++){
            if (str.charCodeAt(i) > 255) bytes++;
        }
        return bytes;
    }

## git fetch和git pull的区别

	git pull：相当于是从远程获取最新版本并merge到本地
	
	git fetch：相当于是从远程获取最新版本到本地，不会自动merge

## 说说你对MVC和MVVM的理解

>`MVC`

    View 传送指令到 Controller

    Controller 完成业务逻辑后，要求 Model 改变状态

    Model 将新的数据发送到 View，用户得到反馈



所有通信都是单向的。

`Angular`它采用双向绑定（data-binding）：`View`的变动，自动反映在 `ViewModel`，反之亦然。


    组成部分Model、View、ViewModel

    View：UI界面

    ViewModel：它是View的抽象，负责View与Model之间信息转换，将View的Command传送到Model；

    Model：数据访问层

## attribute和property的区别是什么？



`attribute`是`dom`元素在文档中作为`html`标签拥有的属性；


`property`就是`dom`元素在`js`中作为对象拥有的属性。



所以：

对于`html`的标准属性来说，`attribute`和`property`是同步的，是会自动更新的，

但是对于自定义的属性来说，他们是不同步的，

## 说说网络分层里七层模型是哪七层

- 应用层：应用层、表示层、会话层（从上往下）（`HTTP、FTP、SMTP、DNS`）

- 传输层（`TCP`和`UDP`）

- 网络层（`IP`）

- 物理和数据链路层（以太网）



>每一层的作用如下：


1. 物理层：通过媒介传输比特,确定机械及电气规范（比特Bit）
2. 数据链路层：将比特组装成帧和点到点的传递（帧Frame）
3. 网络层：负责数据包从源到宿的传递和网际互连（包PackeT）
4. 传输层：提供端到端的可靠报文传递和错误恢复（段Segment）
5. 会话层：建立、管理和终止会话（会话协议数据单元SPDU）
6. 表示层：对数据进行翻译、加密和压缩（表示协议数据单元PPDU）
7. 应用层：允许访问OSI环境的手段（应用协议数据单元APDU）


>各种协议

1. `ICMP协议`： 因特网控制报文协议。它是TCP/IP协议族的一个子协议，用于在IP主机、路由器之间传递控制消息。
2. `TFTP协议`： 是TCP/IP协议族中的一个用来在客户机与服务器之间进行简单文件传输的协议，提供不复杂、开销不大的文件传输服务。
3. `HTTP协议`： 超文本传输协议，是一个属于应用层的面向对象的协议，由于其简捷、快速的方式，适用于分布式超媒体信息系统。
4. `DHCP协议`： 动态主机配置协议，是一种让系统得以连接到网络上，并获取所需要的配置参数手段。

## 说说mongoDB和MySQL的区别



`MySQL`是传统的关系型数据库，`MongoDB`则是非关系型数据库

 `mongodb`以`BSON`结构（二进制）进行存储，对海量数据存储有着很明显的优势。

对比传统关系型数据库,NoSQL有着非常显著的性能和扩展性优势，与关系型数据库相比，MongoDB的优点有：
①弱一致性（最终一致），更能保证用户的访问速度：
②文档结构的存储方式，能够更便捷的获取数据。

## 讲讲304缓存的原理



服务器首先产生`ETag`，服务器可在稍后使用它来判断页面是否已经被修改。本质上，客户端通过将该记号传回服务器要求服务器验证其（客户端）缓存。
<br>
304是HTTP状态码，服务器用来标识这个文件没修改，不返回内容，浏览器在接收到个状态码后，会使用浏览器已缓存的文件
<br>
客户端请求一个页面（A）。 服务器返回页面A，并在给`A`加上一个`ETag`。 客户端展现该页面，并将页面连同`ETag`一起缓存。 客户再次请求页面`A`，并将上次请求时服务器返回的`ETag`一起传递给服务器。 服务器检查该`ETag`，并判断出该页面自上次客户端请求之后还未被修改，直接返回响应`304`（未修改——`Not Modified`）和一个空的响应体。

## 什么样的前端代码是好的


高复用低耦合，这样文件小，好维护，而且好扩展。










