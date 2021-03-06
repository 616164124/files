---
typora-copy-images-to: jpg
---

[TOC]







# 一、Vue.js

## 1 Vue.js 基础

　Vue **不支持** IE8 及以下版本，因为 Vue 使用了 IE8 无法模拟的 ECMAScript 5 特性。但它支持所有[兼容 ECMAScript 5 的浏览器]

### 1.1 MVVM模式

mvvm解释：

- model ：负责数据存储
- view：负责页面展示
- viewModel：负责业务逻辑处理（ajax请求等），对数据进行加工后交给视图展示

MVVM解决了将业务逻辑代码与视图代码进行完全分离，使各自的职责更加清晰，后期代码维护更简单

vue.js入门程序

1. 编写html，引入vue.main.js(vue.js的类库)
2. 编写视图部分的代码（用户界面，只负责展示）
3. 编写vm（viewModel）及其中Model
4. 刷新页面运行程序，vue.js（vm）部分实现将model中的数据在view中展示

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>vue</title>
        <script src=""></script> <!--引入vue包-->        
    </head>
    <body>
        <!--实现body区域展示 -->
        <div id="app">
            {{name}}  <!--相当于mvvm的view视图-->
        </div>
    </body>
    <script>
        //编写mvvm中的model部分及vm（viewmodel）部分
        var vm = new Vue({
            el: '#app', //vm接管了app区域的管理
            data:{// model 数据
                name : 'hello'                
            }         
        });    
    </script>        
</html>



```



## 1.2 vue.js常用指令

### 1.2.1  v-model 指令

1）v-model

实现双向数据绑定：

a、由模型数据绑定到Dom对象，模型数据的值改变，Dom对象的值自动改变

b、由Dom对象绑定到模型数据，Dom对象的值改变，模型数据就改变

```html


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>简单的计算</title>
    <!--引入最新的vue稳定版本-->
    <script type="text/javascript" src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
    
    <!--
<script type="text/javascript" src="https://unpkg.com/vue/dist/vue.min.js"></script>
-->
    
</head>
<body>
<div id = "app">
    {{message}}
	<input type="text" v-model="n1"/>+
	<input type="text" v-model="n2"/>=
	{{Number.parseInt(n1)+Number.parseInt(n2)}}   
</div>
</body>
<script>
    var  vm=new Vue({
        el:'#app',
        data:{
           message:'1111',
			n1:1,
			n2:1
        }
    });
</script>
</html>
```



### 1.2.2 v-text指令

问题：当网速较慢时，页面加载时会将页面源码显示

而v-text解决闪烁的问题





### 1.2.3 v-on 指令

methos中获取数据要用this获取data中的变量

```html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>计算</title>
    <!--引入最新的vue稳定版本-->
    <script type="text/javascript" src="https://unpkg.com/vue/dist/vue.min.js"></script>
</head>
<body>
<div id = "app">
    {{message}}
	<input type="text" v-model="n1"/>+
	<input type="text" v-model="n2"/>=	
	<span v-text="result"></span>
	<button v-on:click="clc">计算</button>
	
</div>
</body>
<script>
    var  vm=new Vue({
        el:'#app',
        data:{
           message:'1111',
			n1:0,
			n2:0,
			result:0
        },
		methods:{
		clc:function(){
		 this.result=Number.parseInt(this.n1)+Number.parseInt(this.n2)
		}
		}				
    });
</script>
</html>


```

### 1.2.3 v-for 和v-if  指令

````html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ss</title>
    <!--引入最新的vue稳定版本-->
    <script type="text/javascript" src="https://unpkg.com/vue/dist/vue.min.js"></script>
</head>
<body>
<div id = "app">
	<ul>
	<li v-for="(item,index) in list":key = "index">{{index}}--{{item}}</li>
	<li v-for="(item,index) in userlist " :key="item.user.age"> 
	<div v-if = "item.user.age == 2" style="background:#00f50c" >{{index}} ---- {{item.user.name}}---{{item.user.age}}</div>
	<div v-else="">{{index}} ---- {{item.user.name}}---{{item.user.age}}</div>
	
	</li>
	</ul>
</div>
</body>
<script>
    var  vm=new Vue({
        el:'#app',
        data:{
		list:[1,2.34,5],
		 userlist:[
		 {user:{name:'hua',age:2}},
		 {user:{name:'hua1',age:522}},
		 {user:{name:'hua3',age:32}}
		 ]
		 }		
    });
</script>
</html>



````



# 二、安装webpack

## 安装前的准备

1. 安装node.js（webpack依赖node）

2. 安装npm(通过npm安装webpack) 修改下载地址 默认到国外下载速度慢

   npm原理： 去远程下载所依赖的js包

3. cnpm 国内的下载

## 安装webpack

***推荐第三中的打包方式***

### 2.1本地安装

参考  https://www.jianshu.com/p/88380e0bfac1

将webpack安装到指定应用程序的目录下	

在用户目录下创建webpacktest：

npm install --save-dev webpack 或者 cnpm install --save-dev webpack

npm install --save-dev webpack-cli(4.0以后版本需要安装webpack-cli)

### 2.2全局安装

将webpack安装npm默认的依赖包的目录()

在任意目录执行命令：

npm install webpack@**版本号** -g 或者cnpm install webpack@**版本号** -g

### 2.3webpack入门程序--打包过程

【参考视频】<https://www.bilibili.com/video/av78225169?p=39>

1. 分模块去定义js

   ​	在js中要导出将来要被打包的方法 module.exports

2. 定义main.js入口文件（主文件）

    在此文件，导入引用的js文件

   var {add} = require（"./model01"）

   可以在main.js中使用导入的js方法

3. 使用webpack命令打包js

4. 在html上引用打包生成的js文件

### 2.4webpack-dev-server打包（推荐使用）

【参考资料】<https://www.bilibili.com/video/av78225169?p=40>

1. 安装webpack-dev-server

   cnpm install webpack@版本号 webpack-dev-server@版本号 html-webpack-plugin@版本号

   安装完成自动创建packjson（记录了本程序所依赖的包信息）

   安装完成自动创建node_modules(存放了本程序所依赖的包)

2. 在package.json中配置script(运行命令)

   "scripts":{"dev": "webpack-dev-server --inline --hot --open --port 5008"},

3. 配置webpack.config.js

   webpack的配置文件，配置了入口文件，输入文件的路径、依赖的插件

4. 使用webpack的命令去运行程序

   npm run dev

### 2.5调试

​	使用debugger进行断点调试



### 2.6开发vue

- 1、在文件目录下打开控制终端：执行 vue init webpack 项目名称
- Project name ：项目名称
- Project description：项目描述
  Author：作者
  Vue build：如何构建项目
  Install vue-router：是否安装路由
  Use ESLint to lint your code：是否使用ESLint来规范我们的代码
  Pick an ESLint preset：选择一个ESLint代码规范
  Set up unit tests：是否需要自动化单元测试
  Setup e2e tests with Nightwatch：是否需要自动化用户界面测试
  Should we run 'npm install' for your after the project has been created?(recommend)：在后续安装依赖包是是否使用npm install安装
- 当根据配置执行完成后会提示Project initialization finished!，代表安装项目初始化完成。
- 2、cd 项目名称
  npm run dev
- 3、项目启动完成 提示Your application is running here: [http://localhost:8080](http://localhost:8080/)

# 三、单页面应用（spa）

##  1、单页面应用就是一张web页面的应用

- 优点

  1、用户操作体验好，不用刷新页面，整个交互过程都是通过Ajax来操作

  2、适合后端分离开发，服务提供http端口，前端请求http接口获取数据，使用js进行客户端渲染

- 缺点

  1、加载慢

  将单页面应用的css、js打包成一个文件，在加载页面显示的时候加载打包文件，如果打包文件较大或者网速慢则用户体验不好

  2、seo（搜索引擎优化）不友好，各大搜索引擎对js不支持，所以单页面应用将大大减少搜索引擎网站的收录。

## 2、element-ui（百度查看使用）

# 四、开发

## 4.1 项目结构

assets ：存放一些静态文件 ，如图片

base：存放基础组件

​	base/api ：基础api接口

​	base/component：基础组件，被各个模块都使用的组件

​	base/router：总的路由配置，加载各模块的路由配置文件。

common：工具类

component：组件目录

mock：存放前端单元测试方法

module：存放各业务模块的页面和api方法

# 五、前后端响应过程

















