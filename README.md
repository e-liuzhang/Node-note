# Node.js

## 1. 简介 

### 1.1 为什么要学node

- 企业需求

  + 具有服务器端开发经验更好
  + front-end
  + back-end
  + 全栈开发工程师
    - 全干

  + 基本的网站开发能力
    * 服务端
    * 前端
    * 运维部署

  + [多人社区](cnodejs.org)

### 1.2 node.js是什么

+ Node.js® is a JavaScript runtime built on [Chrome's V8 JavaScript engine](https://v8.dev/).
  + Node.js不是一门语言
  + Node.js不是库、不是框架
  + Node.js是一个JavaScript运行时环境
  + 简单点来讲就是Node.js可以解析和执行JavaScript代码
  + 以前只有浏览器可以解析执行JavaScript代码
  + 也就是说现在的JavaScript可以完全脱离浏览器来执行，一切归功于Node.js

+ 浏览器中的Javascript

  + EcmaScript
    + 基本语法
    + if
    + var 
    + function
    + Object
    + Array

  + BOM
  + DOM

+ Node.js中的JavaScript
  + 没有BOM和DOM
  + EcmaScript
  + 在Node.js这份JavaScript在执行环境中为JavaScript提供了一些服务器级别的操作API
    + 例如文件读写
    + 网络服务的构建
    + 网络通信
    + http服务器
    + 等处理。。。

+ 构建在Chrome的V8引擎之上
  + 代码只是具有特定格式的字符串而已
  + 引擎可以识别它，引擎可以帮你去解析和执行
  + Google Chrome的V8引擎是目前公认的解析执行JavaScript代码最快的
  + Node.js的作者吧Google Chrome中的V8引擎移植了出来，开发了一个独立的JavaScript运行时环境
+ Node.js uses an event-driven,non-blocking I/O model that makes it lightweight and efficient.
  + event-driven:事件驱动
  + non-blocking I/O model：非阻塞IO模型（异步）
  + lightweight and effcient：轻量和高效

+ Node.js' package ecosystem npm, is the largest ecosystem of open source libraries in the world.
  + npm 是世界最大的开源库生态系统
  + 绝大所数javaScript相关的包都存放在npm上，这样做的目的是为了让开发人员更方便的去下载使用 
  + `npm install jquery` 

### 1.3 Node.js能做啥

+ Web服务器后台
+ 命令行工具
  + npm(node)
  + git(c 语言)
  + hexo(node)
  + 。。。

  + 对于前端开发工程师来讲，接触node最多的是他的命令行工具
    		+ 自己写的少，主要使用别人第三方的
      		+ webpack
          		+ gulp
          		+ npm

### 1.4 预备知识

+ HTML 
+ CSS 
+ JavaScript
+ 简单的命令行操作
  + cd
  + dir
  + ls

+ 具有服务端开发经验为佳

### 1.5 一些资源

![image-20200527165028329](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20200527165028329.png)

### 1.6 能学到啥

+ B/S 编程模型
  + Browser-Server
  + back-end
  + 任何服务端技术这种BS编程模型都是一样的，和语言无关
  + Node只是作为我们学习BS编程模型的一个工具而已

+ 模块化编程
  + RequireJS
  + SeaJS
  + `@import('文件路径')`
  + 以前认知的JavaScript只能通过`script`标签来加载（ES6可以）
  + 在Node中可以像`@import()`一样来引用加载JavaScript脚本文件

+ Node常用API
+ 异步编程
  + 回调函数
  + Promise
  + async
  + generator

+ Express开发框架
+ Rcmascript 6
+ 。。。 

## 2. 起步

### 2.1 安装Node环境

+ 确认版本号：打开命令行，输入`node --version`或`node -v`
+ 环境变量

### 2.2 REPL

+ read
+ eval
+ print
+ loop

### 2.2  Hello World

注意：文件名不要使用node.js来命名，最好也不要用中文

+ 解析执行JavaScript
+ 读写文件
+ http

最简单的http服务：

![image-20200527234340848](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\image-20200527234340848.png)

```js
// 1.加载http核心模块
var http=require('http')
//2.使用http.createServer()方法创建一个Web服务器，返回一份Server实例
var server=http.createServer()
//3.服务器要干嘛
//  提供服务：对数据的服务
//  发请求
//  接受请求
//  处理请求
//  给个反馈（发送响应）
//  注册request请求事件
//  当客户端请求过来，自动触发request请求事件，然后执行第二个参数：回调处理
server.on('request',function () {
    console.log('收到客户端的请求')
})
//4.绑定端口号，启动服务器
server.listen(3000,function () {
    console.log('服务器启动成功，可以通过http://127.0.0.1:3000来进行访问')
})
```



## 3. Node中的JavaScript

+ EcmaScript
+ 核心模块
+ 第三方模块
+ 用户自定义模块

### 3.1 EcmaScript

+ 没BOM
+ 没DOM

### 3.2 核心模块

Node为JavaScript提供了很多服务器级别的API

+ 文件操作：`fs`核心模块
+ http服务构建：`http`模块
+ 路径操作：`path` 模块
+ 操作系统信息：`os`模块
+ 。。。

要用模块必须引用它：

```javascript
var fs=require('fs')
var http=require('http')
```

### 3.3 用户自定义模块

+ require
  + 它的作用就是加载模块
  + 在Node中，模块有三种：
    + 具名的核心模块，例如 fs、http
    + 用户自己编写的文件模块
      + 相对路径必须加./ 不能省略否则报错（当成了具名模块）
      + 可以省略后缀名
    + 第三方模块
  + 在node里面，没有全局作用域，只有模块作用域
    + 内部和外部都互相访问不到
    + 默认都是封闭的
+ exports
  + 在每个文件模块中都提供了一个对象：exports
  + exports默认是一个空对象

### 3.3 第三方模块

## 4. Web服务器开发

### 4.1 ip地址和端口号

+ IP地址用来定位计算机
+ 端口号用来定位具体的应用程序
+ 一切需要联网通信的软件都会占用一个端口号
+ 端口号的范围从0-65536之间
+ 在计算机中有一些默认端口号，最好不要去使用
  + 例如http服务的80

+ 在一台计算器中，一个端口号同一时间只能被一个程序占用

### 4.2 Content-Type

+ https://tool.oschina.net/
+ 不同的资源对应的Content-Type是不一样的
+ 图片不需要指定编码，一般只有政府数据需要指定编码

### 4.3 请求对象 Request

### 4.4 响应对象Response

### 4.5 在Node中使用模板引擎（art-template）

+ 安装

  + ```javascript
    npm install art-template
    ```

+ 使用

  + ```javascript
    var template=require('art-template')
    
    var ret=template.render('hello {{name}}',{
        name:'liuzhang'
    })
    console.log(ret)//=>hello liuzhang
    ```

+ each
  + each 是 art-template 的模板语法，专属的，只能在模板字符串中使用
  + 格式：
    + {{each 遍历项}}
    + <li>{{$value}}</li>
    + {{/each}}

### 4.6 统一静态资源

### 4.7 服务器渲染

+ 就是在服务端使用模板引擎
+ 模板引擎最早诞生于服务端，后来才发展到前端

### 4.8 服务器渲染和客户端渲染的区别

1.  客户端渲染不利于SEO搜索引擎优化
2. 客户端渲染最少两次请求，发起ajax在客户端使用模板引擎；而服务端渲染是客户端拿到的就是服务端已经渲染好的
3. 服务器渲染是可以被爬虫抓取到的，客户端异步渲染是很难被爬虫爬取到的

+ 所以真正的网站既不是纯异步也不是纯服务端渲染出来的，而是两者结合来做的
  + 例如京东的商品列表就是服务端渲染，目的是为了SEO搜索引擎优化，而评论列表为了用户体验，而且也不需要SEO优化，所以是客户端渲染
+ 一个简单的区别方法：服务器渲染是会刷新页面的，而客户端渲染是不会刷新页面的

## 5 留言本

+ 掌握如何解析请求路径中的查询字符串

  + url.parse()

  + ```javascript
    var parseObj = url.parse(req.url, true)
    var pathname = parseObj.pathname
    var pathnamequery = parseObj.query
    ```

+ 如何在Node中实现服务器重定向

  + ```javascript
    res.statusCode = 302
    res.setHeader('Location', '/')
    ```

  + 301 永久重定向 浏览器会记住

    + a.com,b.com
    + 访问a时浏览器不会请求a了，直接跳到b

  + 301 临时重定向 浏览器不记忆
    + a.com,b.com
    + 访问a时浏览器还是会请求a，a告诉浏览器像b请求

## 6 Node中的模块系统

使用Node编写应用程序主要就是在使用：

+ EcmaScript语言
  + 和浏览器不一样，在Node中没有BOM和DOM

+ 核心模块
  + 文件操作的fs
  + http服务的http
  + url路径操作模块
  + path路径处理模块
  + os操作系统信息

+ 第三方模块
  + art-template
  + 必须通过npm来下载才可以使用

+ 用户自定义模块
  + 自己创建的文件

### 6.1.1 模块化

+ 文件作用域
+ 通信规则
  + 加载 require
  + 导出 

### 6.1.2 CommonJS 模块规范

在Node 中的JavaScript还有一个很重要的概念：模块系统

+ 模块作用域
+ 使用require方法用来加载模块
+ 使用exports接口对象用来导出模块中的成员

### 6.2.1 加载`require`

语法：

```javascript
var 自定义变量名=require('模块')
```

两个作用：

+ 执行被加载模块中的代码
+ 得到被加载模块中的`exports`导出接口对象

### 6.2.2 导出`exports` 

+ Node中是模块作用域，默认文件中所有的成员只在当前文件模块有效
+ 对于希望可以被其他模块访问的成员，我们就需要把这些公开的成员都挂载到`exports`接口对象中

导出多个成员（必须在对象中）：

```javascript
exports.a=123
exports.b='hello'
exports.c=function(){
    console.log('ccc')
}
exports.d={
    foo:'bar'
}
```

导出单个成员（拿到的就是：函数和字符串）:

```javascript
module.exports='hello'
```

以下情况会覆盖：

```javascript
module.exports='hello'

//以这个为准，后者会覆盖前者
module.exports=fuction(x,y){
    return x+y
}
```

也可以这样来导出多个成员：

```javascript
module.exports={
    add:function(x,y){
        return x+y
    },
    str:'hello'
}
```

### 6.2.3 原理分析

exports和`module.exports`的一个引用：

```javascript
console.log(exports=module.exports)

exports.foo='bar'

//等价于
module.exports.foo='bar'
```

### 6.2.4 exports和module.exports的区别

+ 每个模块都有一个module对象
+ module对象中有一个exports对象
+ 我们可以把需要导出的成员都挂载到module.exports接口对象中
+ 也就是：`module.exports.xxx=xxx`的方式
+ 但是每次都`module.exports.xxx=xxx`很麻烦
+ 所以Node为了方便，同时在每一个模块中都提供了一个成员叫`exports`
+ `exports===module.exports`结果为`true`
+ 所以对于：`module.exports.xxx=xxx`的方式完全可以：`exports.xxx=xxx`
+ 当一个模块需要导出单个成员的时候，这个时候必须使用：`module.exports=xxx`的方式
+ 不要使用`exports=xxx`不管用
+ 因为每个模块最终向外`return`的是`module.exports`
+ 而`exports`只是`module.exports`的一个引用
+ 所以即便你为`exports=xxx`重新赋值，也不会影响`module.exports`
+ 但是有一种赋值方式比较特殊，``exports=module.exports`这个用来重新建立引用关系
+ 了解这个是为了更灵活的使用它

### 6.2.5 require方法加载规则

如果想要了解更多底层细节，可以自行参考：《深入浅出Node.js》中的模块系统章节

+ 核心模块
  + 模块名

+ 第三方模块
  + 模块名

+ 用户自定义
  + 路径

+ 优先从缓存加载
+ 判断模块标识
  + 核心模块
  + 第三方模块
  + 自定义模块

```javascript
blog
	a
    	node_modules
    b
    	main.js

//此时访问不到模块
```

### 6.3 npm

+ node package manager

#### 6.3.1 npm网站

> npmjs.com

#### 6.3.2 npm命令行工具

npm的第二层含义就是一个命令行工具，只要你安装了node就已经安装了npm。

npm也有版本这个概念

可以通过在命令行中输入：

```shell
npm --version
```

升级npm：

```shell
npm install --global npm
```

#### 6.3.3 常用命令

+ npm init
  + npm init -y可以快速跳过向导，快速生成

+ npm install
  + 一次性把dependencies选项的依赖项全部安装
  + npm i

+ npm install 包名
  + 只下载
  + npm i 包名
+ npm install --save 包名
  + 下载并保存依赖项（package.json文件中的dependencies选项）
  + npm i -S 包名

+ npm uninstall 包名
  + 只删除，如果有依赖项会依然保存
  + npm un 包名

+ npm uninstall --save 包名
  + 删除的同时也会把依赖信息也去除
  + npm un -S 包名

+ npm help
  + 查看使用帮助

+ npm命令 --help
  + 查看指定命令的使用帮助
  + 例如忘了uninstall命令的简写，可以输入`npm uninstall --help`来查看使用帮助

#### 6.3.4 解决npm被墙问题

npm存储包文件的服务器在国外，有时候会被墙，速度很慢，所以国内淘宝的开发团队http://npm.taobao.org/把npm在国内做了一个备份

安装淘宝的cnpm:

```shell
#在任意目录执行都可以
# --global表示安装到全局，而非当前目录
# --global 不能省略，否者不能用
npm install --global cnpm
```

接下来安装包的时候把之前的`npm`替换成`cnpm`

举个例子：

```shell
#这里还是走国外的npm服务器，速度比较慢
npm install jquery

#使用cnpm就会通过淘宝的服务器来下载jquery
cnpm install jquery
```

如果不想安装`cnpm`又想使用淘宝的服务器来下载：

```shell
npm install jquery --registry=https://registry.npm.taobao.org
```

但每一次手动这样加参数很麻烦，所以我们可以把这个选项加入配置文件中：

```shell
npm config set registry https://registry.npm.taobao.org

#查看npm配置信息
npm config list
```

只要经过上面命令的配置，则你以后所有的`npm install`都会默认通过淘宝的服务器来下载

### 6.4 package.json

我们建议每一个项目都要有一个`package.json`文件（描述文件，就像产品说明书）

这个文件可以通过`npm init`的方式来自动初始化

对于我们目前来讲，最有用的是那个`dependencies`选项，可以用来帮我们保存第三方包的依赖信息

如果你的`node_modules`删除了也不用担心，我们只需要：`npm install`就会自动把`package.json`中的`dependencies`中所有的依赖项都下载回来

+ 建议每个项目根目录都有一个`package.json`文件
+ 建议执行`npm install`包名的时候都加上`--save`这个选项，目的是用来保存依赖项信息

#### 6.4.1 package.json和package-lock.json

npm 5 以前是不会有`package-lock.json`这个文件的

npm 5 以后才加入这个文件

当安装包时，npm都会生成后更新`package-lock.json`这个文件

+ npm 5 以后的版本安装包不需要加`--save`参数，他会自动保存依赖信息
+ 当安装包时，会生成后更新`package-lock.json`这个文件
+ `package-lock.json`这个文件会保存`node_modules`中所有包的信息（版本、下载地址）
  + 这样的话重新`npm install`的时候速度就可以提升

+ 从文件来看，有一个`lock`称之为锁
  + 这个`lock`是用来锁定版本的
  + 如果项目依赖了`1.1.1`版本
  + 如果重新install，其实会下载最新版本，而不是`1.1.1`
  + 我们的目的是希望锁住`1.1.1`这个版本
  + 所以这个`package-lock.json`这个文件的另一个作用是锁定版本号，防止自动升级新版

## 7 path 路径操作模块

+ path.basename
  + 获取一个路径的文件名（默认包含扩展名）
+ path.dirname
  + 获取一个路径中的目录部分
+ path.extname
  + 获取一个路径中的扩展名部分
+ path.parse
  + 把一个路径转为对象
    + root根路径
    + dir 目录
    + ext 后缀名
    + name 不包含后缀名的文件名
+ path.join
  + 当你需要进行路径拼接的时候，推荐使用这个方法

+ path.isAbsolute 判断一个路径是否是绝对路径

## 8 Express

原生的http在某些方面表现不足以应对我们的开发需求，所以我们就需要使用框架来加快我们的开发效率，框架的目的就是提高效率，让我们的代码高度统一

在Node中，有很多Web开发框架，这里以`express`为主

+ http://expressjs.com/

### 8.1.1 安装

```shell
npm install --save express
```

### 8.1.2 hello world

```javascript
const express=require('express')
const app=express()

app.get('/',(req,res)=>res.send('hello world!'))

app.listen(3000,()=>console.log('Example app listening on port 3000!'))
```

### 8.1.3 基本路由

路由器

+ 请求方法
+ 请求路径
+ 请求处理函数

get：

```javascript
app.get('/',function(req,res){
    res.send('hello world!')
})
```

post:

```javascript
app.post('/',function(req,res){
    res.send('Got a POST request')
})
```

### 8.1.4 静态服务

```javascript
app.use(express.static('public'))
app.use(express.static('files'))

app.use('static',express.static('public'))

app.use('/static',express.static(path.join(__dirname,'public')))
```

### 8.2 在Express中配置使用`art-template`模板引擎

+ [art-template -GitHub仓库](https://github.com/aui/art-template)
+ [art-template官方文档](https://aui.github.io/art-template/)

安装：

```shell
npm install --save art-template
npm install --save express-art-template
```

配置：

```javascript
app.engine('art',require('express-art-template'))
```

使用：

```javascript
app.get('/',function(req,res){
    //express默认回去项目中的views目录找index.html
    res.render('index.html',{
        title:'hello world'
    })
})
```

如果希望修改默认的`views`视图渲染存储目录，可以：

```javascript
//注意：第一个参数views千万不要写错
app.set('views',目录路径)
```

### 8.3 在Express中获取表单GET请求参数

Express内置了一个API，可以直接通过`req.query`来获取

```javascript
req.query
```



### 8.4 在Express获取表单POST请求体数据

在Express中没有内置获取表单POST请求体的API，这里我们需要使用一个第三方包：`body-parser`

安装：

```shell
npm install --save body-parser
```

配置：

```javascript
var express=require('express')
//0. 引包
var bodyParser=require('body-parser')

var app=express()

//配置body-parser
//只要加入这个配置，则在req请求对象上会多一个属性：body
//也就是可以通过req.body来获取表单POST请求数据
//parse application/x-www-form-urlencoded
app.use(bodyParser.urlencoded({extended:false}))
//parse application/json
app.use(bodyParser.json())
```

使用：

```javascript
app.use(function(req,res){
    res.setHeader('Content-Type','text/plain')
	res.write('you posted:\n')
    //可以通过req.body来获取表单POST请求体数据
    res.end(JSON.stringify(req.body,null,2))
})
```

### 8.5 自己编写步骤

+ 处理模板
+ 配置开发静态资源
+ 配置模板引擎
+ 简单路由：/students 渲染静态页面出来
+ 路由设计
+ 提取路由模块
+ 业务操作如果是处理文件则封装student.js
+ 先写好student.js文件结构
  + 查询所有学生列表的API find
  + findById
  + save
  + updateById
  + deleteById

+ 实现具体功能
  + 通过路由接收请求
  + 接收请求中的数据(get、post)
    + req.query
    + res.body
  + 调用数据操作API处理数据
  + 根据操作结果给客户端发送响应

+ 业务功能顺序
  + 列表
  + 添加
  + 编辑
  + 删除

+ find
+ findIndex

### 8.6在Express配置使用`express-session`插件

安装：

```shell
const session=require('express-session')
```

配置：

```javascript
app.use(session({
    secret:'keyboard cat',//配置加密字符串，增加安全性
    resave:false,
    saveUninitialized:true
}))
```

使用：

```javascript
//添加
req.session.user=req.body
//获取
req.session.user
```

提示：默认session数据是内存存储的，服务器一旦重启就会丢失，真正的生产环境会把session持久化存储。

## 9 MongoDB

### 9.1关系型数据库和非关系型数据库

表就是关系

或者说表与表之间存在关系

+ 所有的关系型数据库都要通过`sql`语言来操作
+ 所有的关系型数据库在操作之前都需要设计表结构
+ 而且数据表还支持约束
  + 唯一性
  + 主键
  + 默认值
  + 非空

+ 非关系型数据库非常灵活
+ 有的非关系数据库就是key-value 对
+ 但是MongoDB是长得最像关系型数据库的非关系型数据库
  + 数据库=>数据库
  + 数据表=>集合（数组）
  + 表记录=>（文档对象）

+ MongoDB不需要设计表结构
+ 也就是说可以任意往里面存数据，没有结构性这么一说

### 9.2 安装

+ 下载地址：https://www.mongodb.com/download-center/community
+ 下载
+ 安装
+ 配置环境变量
+ 输入`mongod --version`测试是否安装成功

### 9.3 启动和关闭数据库

启动：

```shell
#mongodb默认使用执行mongod命令所处盘符根目录下的/data/db作为自己的数据存储目录
#所以第一次执行该命令之前先自己手动新建一个/data/db
mongod
```

如果想要修改默认的数据存储目录，可以：

```shell
mongodb --dbpath=数据库存储路径
```

停止：

```shell 
在开启服务的控制台，直接Ctrl+c即可停止
或者直接关闭开启服务的控制台也可以
```

### 9.4 连接和退出数据库

连接：

```shell
#该命令默认连接本机的MongoDB服务
mongo
```

退出：

```shell
#在连接状态输入exit退出连接
exit
```

### 9.5 基本命令

+ `show dbs`
  + 查看显示所有数据库

+ `db`
  + 查看当前操作的数据库

+ `use 数据库名称`
  + 切换到指定的数据库（如果没有会新建）

+ 插入数据

### 9.6 在Node中如何操作MongoDB数据

#### 9.6.1 使用官方的`mogodb`包来操作

> https://github.com/mongodb/node-mongodb-native

#### 9.6.2 使用第三方mongoose来操作MongoDB数据库

第三方包：`mongoose`基于MongoDB官方的`mongodb`包再做一次封装

+ 网址：https://mongoosejs.com/

## 10 异步编程

### 10.1 回调函数

不成立的情况：

```javascript
function add(x,y){
    console.log(1)
    setTimeout(function(){
        console.log(2)
        var ret =x+y
        return ret
    },1000)
    console.log(3)
    //到这里执行就结束了，不会等到前面的定时器，所以直接就发回来默认值undefined
}
console.log(add(10,20))//=>undefined
```

不成立的情况：

```javascript
function add(x,y){
    var ret
    console.log(1)
    setTimeout(function(){
        console.log(2)
        ret =x+y    
    },1000)
    console.log(3)
    return ret
}
console.log(add(10,20))//=>undefined
```

回调函数：

```javascript
function add(x,y,callback){
    //callback 就是回调函数
    //var x=10
    //var y=20
    //var callback=function(a){ }
    console.log(1)
    setTimeout(function(){
        var ret=x+y
        callback(ret)
    },1000)
}

add(10,20,function(a){
    //a才是我们得到的结果
})
```

基于原生XMLHTTPRequest封装get方法：

```javascript
function get(url,callback) {
    var xhr=new XMLHttpRequest();
    xhr.onload=function(){
        callback(xhr.responseText)
    };
    xhr.open('get',url,true);
    xhr.send();
}
get('db.json',function (data) {
    console.log(data)
})
```

### 10.2 Promise

> 参考文档：http://es6.ruanyifeng.com/#docs/promise

callback hell:

​	（自己搜索引擎搜索即可）

基本使用：

```javascript
var fs=require('fs')

var p1=new Promise(function (resolve,reject) {
    fs.readFile('./data/a.txt','utf8',function (err,data) {
        if (err){
            reject(err)
        }else {
            resolve(data)
        }
    })
})
var p2=new Promise(function (resolve,reject) {
    fs.readFile('./data/b.txt','utf8',function (err,data) {
        if (err){
            reject(err)
        }else {
            resolve(data)
        }
    })
})
var p3=new Promise(function (resolve,reject) {
    fs.readFile('./data/c.txt','utf8',function (err,data) {
        if (err){
            reject(err)
        }else {
            resolve(data)
        }
    })
})
p1
    .then(function (data) {
        console.log(data)
        return p2
    },function (err) {
        console.log('读取文件失败',err)
    })
    .then(function (data) {
        console.log(data)
        return p3
    },function (err) {
        console.log('读取文件失败',err)
    })
    .then(function (data) {
        console.log(data)
    },function (err) {
        console.log('读取文件失败',err)
    })
```

封装`promise`版本的`readFile`:

```javas 
const fs=require('fs')

function pReadFile(filePath) {
    return new Promise(function (resolve,reject) {
        fs.readFile(filePath,'utf8',function (err,data) {
            if (err){
                reject(err)
            }else {
                resolve(data)
            }
        })
    })
}

pReadFile('./data/a.txt')
    .then(function (data) {
        console.log(data)
        return pReadFile('./data/b.txt')
    })
    .then(function (data) {
        console.log(data)
        return pReadFile('./data/c.txt')
    }).then(function (data) {
        console.log(data)
    })
```



## 11 其他

### 11.1 代码风格问题

### 11.2 修改完代码自动重启

可以使用一个第三方命令行工具：`nodemon`来帮助我们解决频繁修改代码重启服务器问题。

`nodemon`是一个基于`Node.js`开发的一个第三方命令行工具，我们使用的时候需要独立安装：

```shell
npm install --global nodemon
```

安装完毕后，使用：

```shell
node app.js

#使用nodemon
nodemon app.js
```

只要通过`nodemon app.js`启动的服务，则它会监视你的文件变化，当文件发生变化的时候，自动帮你重启服务器

### 11.3文件操作路径和模块路径

```javascript
//在文件操作的相对路径中
//  ./data/a.txt 相对于当前目录
//  data/a.txt 相对于当前目录
//  /data/a.txt 绝对路径，当前文件模块所处磁盘根目录
//  c:/xx/xx... 绝对路径
fs.readFile('./data/a.txt',function(err,data){
    if(err){
        console.log(err)
        return console.log('读取失败')
    }
    console.log(data.toString())
})
```

模块操作路径：

```javascript
//这里忽略了. 则也是磁盘根目录
require('/data/foo.js')

//相对路径
require('./data/foo.js')

//模块加载的路径中的相对路径不能省略 ./
```

### 11.4 Node中的其他成员

在每个模块中，除了`require`、`exports`等模块相关API之外，还有两个特殊的成员：

+ `__dirname`**动态获取**可以用来获取当前文件模块所属目录的绝对路径
+ `__filename`**动态获取**可以用来获取当前文件的绝对路径
+ `__dirname`和`__filename`是不受执行node命令所属路径影响的

在文件操作中，使用相对路径是不可靠的，因为在Node中文件操作的路径被设计为相对于执行node命令所处的路径（不是bug，这样设计是有使用的场景）。

为了解决这个问题，只需把相对路径变为绝对路径就可以了。

那这里就可以使用`__dirname`或者`__filename`来帮助我们解决这个问题。

在拼接路径的过程中，为了手动避免拼接带来的一些低级错误，所以推荐多使用：`path.join()`来辅助拼接。

所以为了尽量避免刚才所描述的这个问题，以后在文件操作中使用的相对路径都统一转换为**动态的绝对路径**。

> 补充：模块中的路径标识和这里的路径没关系，不受影响（相对于文件模块）