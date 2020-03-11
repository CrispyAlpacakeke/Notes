## 目录

[toc]

## HTML

##### 1、什么是HTML？HTML与XHTML的区别？什么是DOCTYPE？为什么HTML5只需写 <  !DOCTYPE HTML >

HTML  - 超文本标记语言（以前的版本是HTML4.01，现在的新版本为HTML5），并不是编程语言，标记语言由一系列标签组成，通过标记标签描述网页。

XHTML - 可扩展超文本标记语言，与HTML4.01几乎相同，但更严谨和纯净

主要体现在：

- XHTML元素必须被关闭

- XHTML元素必须正确嵌套

- 标签名必须小写

- XHTML文档必须拥有根元素

DOCTYPE ：

- 标准通用标记语言的文档类型声明
- 位于HTML文档第一行
- 告知浏览器的（标准通用标记语言）析器使用什么样的DTD解析文档
- 当前有严格模式和过度模式两种风格

是标准通用标记语言的文档类型声明

> DTD：文档类型定义，一组机器可读的语法规则，解析页面时，浏览器利用这些规则检查页面的有效性，并渲染页面
>
> 比如用于XHTML 4.0 的严格型，标签中的引用就叫做DTD
>
> ```html
>  <!DOCTYPE HTMLPUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
> ```

HTML5不基于SGML（标准通用标记语言），不需要对DTD进行引用，但是需要DOCTYPE来规范浏览器的行为

HTML4和XHTML是基于SGML的，需要引用DTD告知浏览器文档所使用的文档类型

##### 2、行内元素、块级元素、行内块元素

行内元素：宽高由内容支撑，不占有独立区域，和相邻行内（行内块）元素排成一行，不可设置宽高，可设置padding，和左右margin，不能设置上下margin，只能嵌套行内元素

span / a / i / em / label / b / u / del / br

块级元素：独占一行，宽度默认容器的100%，可设置宽高和内外边距

1）div / h1~h6 / p / hr

2）nav / header / main / section

3）ul / ol / dl / li / dt / dd

4）table / form / option

行内块元素：宽高由内容支撑，和相邻行内（行内块）元素排成一行，可设置宽高和内外边距，只能嵌套行内和行内块元素

1）img  / audio / vedio

2）input / textarea / button / select 

3）td / tr / tbody / thead / th

##### 3、对HTML语义化的理解

- 当没有css样式的情况下，也能够构架清晰的HTML结构
- 便于团队开发和维护，语义化更具可读性，是下一步吧网页的重要动向，遵循W3C标准的团队都遵循这个标准，可以减少差异化

- 有利于SEO：和搜索引擎建立良好沟通，有助于爬虫抓取更多有效信息：爬虫依赖于标签来确定上下文和各个关键字的权重（比如artical标签，爬虫能够理解标签内的内容是一篇文章，如果全是用无语义的div，没有css样式的时候不好理解）
- 提升用户体验：例如title、alt用于解释名词或解释图片信息、label标签的活用
- 方便其他设备解析：如屏幕阅读器、盲人阅读器、移动设备，以意义的方式渲染页面

##### 4、HTML5有哪些新特性

- 语义化标签

- 增强型表单：[新的输入类型](https://www.w3school.com.cn/html5/html_5_form_input_types.asp) / [新的表单元素](https://www.w3school.com.cn/html5/html_5_form_elements.asp) / [新的表单属性](https://www.w3school.com.cn/html5/html_5_form_attributes.asp)

- 视频和音频

- 地理定位

- 拖放API：在HTML5中任何元素都能拖放，[API](https://developer.mozilla.org/zh-CN/docs/Web/API/HTML_Drag_and_Drop_API)

- Canvas绘图和SVG绘图：[canvas](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial) / [SVG](https://www.w3school.com.cn/svg/index.asp) / [区别](https://www.w3school.com.cn/html5/html_5_canvas_vs_svg.asp)（canvas是位图，svg是矢量图）

- [web worker](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Workers_API/Using_web_workers)：

  - 实现多线程，主线程中把需要处理的数据postMessage发送到worker线程的js脚本中，worker线程在后台运行不受主线程影响，由于不在同一个上下文中，主线程和worker线程的通信需要postMessage完成（worker线程处理好数据后发送回主线程），在主线程中可以绑定 "onmessage"事件监听数据的变化

  - 在主线程中：

    ``````javascript
    let worker = new Worker('work.js'); // work.js ->分配给worker线程的脚本文件
    ``````

- web storage：localStorage、sessionStorage

- web socket：

  > 全双工通讯协议，一次握手后创建持久性的链接，并进行双向数据传递，本质上基于TCP协议，

  > 主要的事件有：
  >
  > open - 和服务器建立链接时触发
  >
  > message - 收到服务端发送的数据时触发
  >
  > close - 链接关闭时触发
  >
  > error - 通信错误时触发
  >
  > 方法：
  >
  > Socket.send() - 发送数据
  >
  > Sokect.close() - 关闭链接

##### 5、表单提交中Get和Post方式的区别

- Get一般是从服务器上获取数据，Post一般是提交数据到服务器上
- Get传输数据的方式是拼接在url链接后面，用户可见，Post传输的数据用户不可见，封装在HTTP的请求体中
- Get传输的数据量较小，不超过2kb，而Post传输的数据相对较大
- Get安全性低，Post相对安全性高
- 在Form表单提交时，不指定method的话，一般默认为Get方式

##### 6、src与href的区别

src 表示引用外部资源，替换当前元素

<script src="script.js"></script>当浏览器解析到这句代码时，页面的加载和解析都会暂停直到浏览器拿到并执行完这个js文件

href 表示引用超文本，是在当前元素和引用资源之间建立联系，而不是替换

`<link href="style.css" rel="stylesheet" />`浏览器加载到这里的时候，`html` 的渲染和解析不会暂停，`css` 文件的加载是同时进行的

##### 7、描述一下 cookie，sessionStorage 和 localStorage 的区别

|     特性     |                            cookie                            |                        sessionStorage                        |      localStorage      |
| :----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :--------------------: |
|   生命周期   |             默认浏览器关闭后失效，可设置有效时间（expires字段）             | 会话级存储，仅在当前网页会话下有效，当页面关闭或浏览器关闭后被清除 | 永久有效，只能手动清除 |
| 存放数据大小 |                           4kb左右                            |                           5MB左右                            |5MB左右|
|   http请求   | 每次请求携带在HTTP请求头中，如果使用cookie保存过多数据会带来性能问题 | 本地存储（在浏览器中保存），不参与和服务器的通信 ||

##### 8、HTML5的离线存储怎么使用，解释一下工作原理

使用HTML5中的cache manifest缓存机制

manifest就是文件后缀名为appchache或者manifest的文件

在这个文件中定义哪些文件在从服务器上首次下载后会被缓存

并且在index.html根页面的根标签中指定manifest配置文件

``````html
<html manifest = "manifest.appcache">
``````

优势：

- 离线浏览：用户在离线状态下也能使用应用
- 速度：已缓存的资源加载速度更快
- 减小服务器负载：浏览器只需向服务器请求下载更改过或更新的资源

##### 9、可跨域的三个标签

- <img src="">

- <link href="">

- <script src="">

## CSS

了解clip-path、grid布局

## JavaScript

#### 一、什么是 JS？

#### 二、基本语法

##### 1、变量

##### 2、数据类型

2.1 基本数据类型：String / Number / Boolean / Null / Undefined

2.2 引用（复杂）数据类型：Object / Array / Function

2.3  typeof 会返回哪些数据类型？

- Number：包括NaN
- String
- Object：包括Null 和 Array
- Function
- Boolean



## W3C标准

HTML / XHTML / HTML5  -> 显示数据

XML -> 传输和存储数据

CSS / CSS3 / 

TCP / IP

## ECMAScript标准

ES5 / ES6

JS -> ES + DOM +BOM

Node.Js -> ES

## 浏览器

##### 1、常见的浏览器内核有哪些，介绍一下你对浏览器内核的理解

常见浏览器内核：

- Trident 内核：IE
- Presto 内核：Opera7及以上（现为Blink）
- Webkit 内核：Safari、Chrome（现为Blink）
- Gecko  内核：FireFox、NETSCAPE6及以上
- Blink 内核：Chrome和Opera一起开发

浏览器内核分为渲染引擎和JS引擎：

渲染引擎：负责获取网页内容（HTML、XML、图像等），整理讯息（例如加入CSS），计算页面的显示方式（因此不同内核的浏览器对网页解析存在一定差异，需要做兼容）

JS引擎：解析和执行javascript来实现页面的动态效果

##### 2、如何实现浏览器内多个标签页（不同页面）之间的通信

- localStorage：浏览器多个标签公用存储空间，onstorage 监听localStorage变化，但只有在非当前页修改localstorage，以及对原有数据的值进行修改时才触发

- web socket

- web worker：sharedworker（前提是这些标签页必须同源）实现，由于时不同的标签页，因此在sharedWorker线程上的js脚本中需要监听消息的变化

  ``````javascript
  // sharedWorker所要用到的js文件，不必打包到项目中，直接放到服务器即可
  let data = ''
  onconnect = function (e) {
    let port = e.ports[0]
    port.onmessage = function (e) {
      if (e.data === 'get') {
        port.postMessage(data)
      } else {
        data = e.data
      }
    }
  }
  ``````





## 注

escape() 字符串编码

``````javascript
escape("羊驼")   // 输出：%u7F8A%u9A7C
``````