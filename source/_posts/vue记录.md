---
title: vue记录
date: 2017-11-26 16:59:04
tags: vue
---
# Vue

## Vue的基本概念

### 基本概念
	渐进式 JavaScript 框架，核心功能比较小，如果你要做更强大的功能，就要去集成一些插件和第三方包
	
	核心插件:(全家桶)
		Vue-Router:当触发了页面的超链接之后要渲染出哪个页面(组件)，就得靠路由
		
		Vuex:全局存取数据(状态管理)

<!-- more -->
		
	特点:
		1、已经会了HTML,CSS,JavaScript？即刻阅读指南开始构建应用！
		2、简单小巧的核心，渐进式技术栈，足以应付任何规模的应用。
		3、20kb min+gzip 运行大小 超快虚拟 DOM 最省心的优化
		
### 发展历程&未来趋势
	2014
	
	趋势:https://www.awesomes.cn/rank/
	
	一个用以创建用户接口(UI)的直观、快速、简洁的 MVVM 框架

### 基本步骤
	1：安装node.js(自带npm)
	2：安装cnpm 
	3：安装webpack  帮忙打包前端资源
	4：用vue-cli脚手架构建工具
	

## 如何学习Vue
	Vue的教程:https://cn.vuejs.org/v2/guide/
	
	开源的项目:https://segmentfault.com/p/1210000008583242/read?from=timeline
	
	Vue的专题:https://www.awesomes.cn/subject/vue#应用-框架
	
	bug解决网站:www.stackoverflow.com
	
	文章:知乎专栏 掘金 简书 segmentfault


---------------------

## Vue基础
	MVVM ---> Hello World

	指令
	
	组件(重点)
	
	过滤器
	
	路由
	
	网络请求

---------------------

## MVVM 
	http://www.ruanyifeng.com/blog/2015/02/mvcmvp_mvvm.html
		M:model 模型
		V:view 视图
		VM:view-model 视图模型
	注意：view不能直接找model要数据
	
	
### Vue中是如何体现MVVM的
	步骤:
		1、导入js cdn
		2、写代码
			V:View Vue写在一个id=app的div中，以后开发中，这里面写的	就是Vue的一些指令
				
			VM: 可以认为就是Vue的实例(对象)	
				
			M: 就是Vue实例中data属性对应的值(值是一个对象)
			
	参考:https://cn.vuejs.org/v2/guide/instance.html
		
		

## 指令

	作用:
		渲染页面(组件)
		
	渲染的过程:
		Vue实例通过el:app找到Vue要解析的范围，发现html元素中如果有以v-开头的东西，Vue就去解析这些指令，并且给某些html元素填充上值显示
		
		Vue指令除了显示组件之外，还提供与用户的交互(比如给某些元素绑定单击事件)
		
	指令:
		插值表达式 {{}}
		v-text&v-html 
			v-text纯文本显示 v-html会解析字符串中有的标签
			
		v-bind 缩写为':'
			数据绑定 单向数据绑定(模型--->视图)
		
		v-on 缩写为'@'
			作用:事件绑定，当我们触发了某些事件之后(单击事件)，执行函数，达到和用户交互的目的
			
			注意:
				当没有参数的时候，可以省略`()`
				有参数的时候，如果要传参不能省略`()`
				
			事件类型:
				https://developer.mozilla.org/zh-CN/docs/Web/Events
				
			缩写:
				v-on:事件类型 = "处理函数"
				@事件类型="处理函数"
		
		v-model
			数据的双向绑定，更改了模型更改了会影响视图，视图更改会影响模型 input radio checkbox
			
			Vue.js devtools工具可以看到我们Vue写的项目里面的模型这些东西，但是有一个注意事项，你必须在开发环境中使用才有作用
		
		v-if/v-show
			作用:条件渲染
			参考:https://cn.vuejs.org/v2/guide/conditional.html
			
			注意：
				1、v-if / v-show 只接收boolean值
				2、v-if 值为true 就创建 值为false就不创建
				3、v-show 值为true/false都会创建，当值为false是，设置display:none; 值为true 干掉display
				4、v-if/v-else 要贴在一起
				5:v-if 写判断条件，v-else 则不用
				
			v-if&v-show的区别，实际开发中如何选择?
					一般来说， v-if 有更高的切换开销，而 v-show 有更
					高的初始渲染开销。因此，如果需要非常频繁地切换，
					则使用 v-show 较好；如果在运行时条件不太可能改
					变，则使用 v-if 较好。
			
		v-for
			列表渲染
			
			注意点:
				当我们遍历每一个item的时候，默认是采取`就地复用`的原则，也就是说得直白一点，下一个item可能复用上一个item，可能会导致两个item指向同一块内存空间，当如果更改我们模型，可能会导致几个地方一起改
			
			如何解决：
				v1.x 通过track-by 给遍历到的每一项，设置一个唯一的标识符
				v2.x 通过key 给遍历到的每一项，设置一个唯一的标识符
				
			参考:
				https://cn.vuejs.org/v2/guide/list.html

	参考:https://cn.vuejs.org/v2/api/#指令

---------------------

## 组件

#### 概念：功能相似的代码的集合，组件可以扩展html内容，封装可重用的代码
	参考:https://cn.vuejs.org/v2/guide/components.html

	1、功能模块的代码集合
	2、组件可以扩展 HTML 元素，封装可重用的代码。
	
	总结:
		把一些功能代码写在一个组件中，然后需要的时候，导入进来并且使用
		
	注意点:
		1、组件使用起来就有点类似于使用自定义的html标签
		2、使用了组件化的开发方式，能将一些零散的代码放在不同的组件中去处理，然后在需要的时候对组件的引入
		
### 实现方式(五种)
	前四种【了解、特地别是第二种】 + 单文件组件（https://cn.vuejs.org/v2/guide/single-file-components.html）
	
	前四种定义组件的方式
	1、先定义，再注册，最后使用
	2、注册和定义一步到位，最后使用
	3、通过自定义<template>标签定义组件，最后使用
	4、通过自定义script标签定义组件，最后使用
	
	注意点:
		1、组件要想在id=app的div中使用，必须注册
		2、每个组件都需要有一个根元素
		3、每个组件内部有自己的data，methods
		4、每个组件内部的data是一个函数，并且这个函数必须返回一个对象，这个和根实例要区分
		5、Vue文档中，定义组件就是使用第二种方式
		6、第三种、第四种是对我们第二种中template的简化
	

---------------------

## 过滤器
	作用:对服务器返回的数据进行过滤处理，将它变成符合展示要求的数据
	
	分类:
		私有过滤器
			1、是和每个Vue实例相关的，在实例的filters中先定义好，函数
			```
				filters:{
		            toUpperCase:function(input,name){
		                return input.toUpperCase()
		            }
		        }
			```
			
			2、调用过滤器的方法，进行过滤，使用`|`
		
		全局过滤器
			1，写在跟实例的前面，
			```
				vue.filter('toUpperCase',function(input,name){
					rutern input.toUpperCase()
				})	
			```
			参数：参数一：过滤器的名称，
				 参数二：过滤器的处理函数（匿名函数）
				
		
	注意点:
		1、过滤器中都是一些函数，并且这些函数必须要有返回值
		2、过滤器的函数的第一个参数，就是`|`前面，我们在调用函数的时候，只需要从第二个参数传起


## MVVM
	M:model
	V:view
	VM:view-model
	
## 指令
	v-text/v-html 显示文本/html
	v-bind 单向数据绑定，数据是动态的时候
	v-on 事件，和用户交互
	v-model 双向数据绑定 模型--->视图 视图--->模型
		Vue-dev-Tools 开发版本
	v-if/v-show 条件渲染 
	v-for 为遍历的每一项添加一个:key="唯一的标识"
	
## 组件
	功能代码的集合，把功能相似的代码放入到一个组件中去(.vue)
	
	创建时候的五种方式
	1、先定义，再注册，再使用
	2、定义&注册，再使用
	3、对第二种的template的简化，使用template标签
	4、对第二种的template的简化，使用script标签
	
	5、单文件组件的形式(.vue)
		template【必须】
		style 样式
		script 逻辑
		
## 过滤器
	作用:对服务器返回的数据，进行过滤，将其变成符合展示的数据
	
	分类：
		私有过滤器
			每个Vue对象中filters里面写上函数(注意:函数必须要有返回值)，关于参数，`|`前面的就是第一个参数，后面再作为第二个参数。
		
		全局过滤器
			Vue.filter(函数名称，处理函数)
			函数必须要有返回值，关于参数，`|`前面的就是第一个参数，后面再作为第二个参数。



## 路由
	
	作用:
		当我们触发了某个超链接(a)，决定把哪个页面(组件)呈现在用户面前
		
	参考:
		https://router.vuejs.org/zh-cn/
		
	代码如何写?
		https://router.vuejs.org/zh-cn/essentials/getting-started.html
		
	代码书写分两大块(见代码)
		html(视图) 
			1、router-view 路由占位符，当触发了某个路由之后，将我们router-view替换成真正的组件
			
			2、router-link 触发我们的超链接，路由匹配
			
		script(逻辑)
			1、先创建组件
			
			2、创建路由对象、设置路由规则
			
			3、路由的对象，注入到根实例中
			
	注意:
		1、由于路由功能没有放在它的核心框架(Vue.js)里面，所以我们需要导入vue.js之后，还要导入vue-router.js
		2、进行路由匹配的时候，要注意无参和有参路由的一个匹配方式
		3、如果是有参数，路由规则中要发生响应的更改(动态路由匹配)，在获取值的时候，通过$route.params.xxx

-------------------------

## Vue-Resource  vue1.0
	底层就是对Ajax的封装，就是发送Ajax请求，对我们Vue封装
	
	参考：
		https://github.com/pagekit/vue-resource
		
	使用:
		https://github.com/pagekit/vue-resource/blob/develop/docs/http.md
	
	GET
		见代码
		
	POST
		见代码
		
		注意点:
			post有三个参数，参数1:url 参数2:js对象，放在请求体中数据 
			参数3: {emulateJSON:true}(相当于设置Content-Type为:application/x-www-form-urlencoded)
		
	JSONP
		见代码


-------------------------

## Webpack

### 概念
	Webpack 是当下最热门的前端资源模块化管理和打包工具。它可以将许多松散的模块按照依赖和规则打包成符合生产环境部署的前端资源。还可以将按需加载的模块进行代码分隔，等到实际需要的时候再异步加载。通过 loader 的转换，任何形式的资源都可以视作模块，比如CommonJs 模块、 AMD 模块、 ES6 模块、CSS、图片、JSON、Coffeescript、 LESS 等。
	Webpakc是一个构建和打包工具
	
### 官网:
	1.x https://webpack.github.io/docs/
	2.x https://doc.webpack-china.org/
	
### Webpack的使用之打包单个js文件【入口文件、输出文件】
	1、构建js，默认清情况下，Webpack只能打包.js结尾的文件
	
	切换到项目的根路径 使用 webpack 入口文件 输出文件(bundle.js)
	
	运行：打包出来的bundle.js不能直接在浏览器中运行起来，需要使用一个html包含起来，再运行

----------------------------------------

### Webpack的使用之打包多个js文件【入口文件、输出文件】
	和打包一个文件一样，都是打包入口文件，只是说，Webpack打包的时候会去分析它的依赖关系，然后入口文件中导入(依赖的)其它模块，这个时候Webpack也会把其它模块一起打包

----------------------------------------

### Webpack之Loader的使用
	作用:
		使用不同的loader来打包非js文件
		
	有哪些Loader 
		https://github.com/webpack/webpack
		https://doc.webpack-china.org/loaders/ 【看这个】
		
	打包css
		安装两个loader 
			style-loader 把解析好的css插入到html的header中<style>
			css-loader 解析css
			
		npm i style-loader css-loader --save-dev
		
	打包的时候还得额外的添加一个指令
		第一种方式
			在导入css的地方使用 : require('!style-loader!css-loader!./style.css')
			
		第二种方式
			在导入css的地方，不需要加任何东西，但是在终端里面打包的时候
			webpack --progress entry.js bundle.js --module-bind "css=style-loader!css-loader"
			
			
	注意点：
		所有的laoder的加载规则都是从后往前加载

----------------------------------------

### Webpack之配置文件
	作用:
		简化打包指令，并且防止出错
		
	步骤:
		1、在项目根路径下面，创建一个叫做webpack.config.js的文件【默认】
		
		2、在里面写一些打包配置的指令(属性)
		
	注意:
		如果我们的webpack的配置文件，不叫webpack.config.js，到时候使用webpack打包的时候，必须通过--config指定我们要打包的配置文件

----------------------------------------

### Webpack之插件
	作用:
		能提高我们开发的效率或是能帮我们做一些其它的事情（比如压缩js代码，性能优化）
		
	插件的使用
		安装本地包(webpack)
		npm i webpack --save-dev

----------------------------------------

### Webpack全局包与本地包的一个区别

	区别:
		作用场景不一样
		
		全局包: webpack --progress，在终端中使用，用来读取我们webpack的配置文件，对我们项目的源代码进行打包
		
		本地包: 用在项目中，我们安装webpack本地包的目的是为了使用webpack本地包中自带的一些插件(压缩js的插件，抽离第三方包的插件...)

----------------------------------------
	
### Webpack的参数说明
	webpack 
		--progress 查看打包的进度
		-p 压缩bundle.js，可能需要借助babel
		--watch 监听源代码的更改
		--config 文件名称 指定要打包的配置文件名称
		
	更改了源代码，得重新打包
	
	注意:
		1、Webpack的参数，可以接多个，并且没有先后顺序之分
	
-------------------------

## Webpack1.x和Webpack2.x的区别
	参考：
		https://segmentfault.com/a/1190000008181955
		
	1、关于loader，1.x可以省略-loader 2.x 不能省略



-------------------------


## 项目的搭建(Webpack+Vue)
	步骤:
		1、创建一些必要的文件或是文件夹
			
			src(项目的源代码)
			
			package.json(项目的配置文件)
			
			开发阶段的webpack的配置文件，webpack.develop.config.js
			
		2、在webpack.develop.config.js中写上配置信息
			见代码 entry output module plugins
			
			
		3、Webpack+Vue
			3.1 App.vue
				```
					<template>
						<div>
						</div>
					</template>
				```
				
			3.2 main.js【复杂】
				1、前提:
					安装 vue vue-loader vue-template-compiler css-loader
					
					npm i vue --save
					
					npm i vue-loader vue-template-compiler css-loader --save-dev
			
				2、在main.js中导入进来，并且创建我们的根Vue实例，在根实例中，通过render函数，告知webpack，我第一个呈现出来的组件是谁
					//导入我们要渲染的根组件这个模块
					import App from './App.vue'
					
			3.3、在webpack.developer.config.js中，配置对.vue文件的支持
				```
					loaders: [
			            {
			                test: /\.vue$/, 
			                loader: 'vue-loader'
			            }
			        ]
				```			
				
-------------------------

## 项目的运行
	1、使用 webpack 打包
		webpack --progress --config webpack.develop.config.js

	2、建立一个html文件，导入bundle.js
		注意，在我们的html中，一定要建立一个id=app的div

-------------------------

## webpack与webpack-dev-server 这个全局包的比较
	相同点:
		webpack&webpack-dev-server都是运行在终端，都可以用来打包，并且指令都是一样
			webpack --progress --config webpack.develop.config.js
			webpack-dev-server --progress --config webpack.develop.config.js
			
			
	不同点:
		应用的阶段不一样
			webpack 用在生产阶段，最后打包上线的时候才需要使用它
			webpack-dev-server 用于开发阶段，提高开发效率
			
		webpack-dev-server 是在webpack基础上封装起来的，所以，除了webpack本身有的功能，还有webpack没有的功能，所以更加牛逼
		
	实际开发中:
		开发阶段使用 webpack-dev-server + html-webpack-plugin这个插件使用
		
		生产阶段:webpack压缩打包

--------------------------

## 提高开发阶段效率的工具(目的:更改源代码，直接在浏览器中呈现效果)

	webpack-dev-server + 插件:html-webpack-plugin
	
	
	1、前提:
		1、安装 webpack-dev-server 全局包  npm i webpack-dev-server -g
		2、安装 webpack webpack-dev-server、html-webpack-plugin 本地包
			npm i webpack webpack-dev-server html-webpack-plugin --save-dev
			
	2、在webpack.develop.config.js中，进行插件配置(html-webpack-plugin)
		```
			new HtmlWebpackPlugin({  // Also generate a test.html
	            filename: 'index.html', //内存中生成的文件名称
	            template: './template.html' //模版文件
	        })
		```
		
	3、使用webpack-dev-server 运行我们的项目，我们项目就可以跑起来了
		webpack-dev-server --config webpack.develop.config.js
		
		
	注意点：
		webpack-dev-server 和 html-webpack-plugin要配合起来用
		
--------------------------

## webpack-dev-server
	参考:https://webpack.github.io/docs/webpack-dev-server.html
		webpack-dev-server --open 【打开默认浏览器】
						   --port 6008
						   --hot 实现热重载
						   
						   
	把 webpack-dev-server --progress --config webpack.develop.config.js --port 6008 --open --hot 加入到我们package.json的script中
	
	注意:
		在package.json的script中不要写任何注释，否则有问题

--------------------------

## html-webpack-plugin 有什么作用
	写法参考:https://github.com/jantimon/html-webpack-plugin

	开发阶段：
		它可以以一个模版文件(template.html)为参照，在`内存中`生成一个指定名称的(index.html)的文件，放在内存中的index.html速度快
		
	
	生产阶段：
	
	注意事项
		1、在我们模版文件中，一定要删除导入bundle.js那段代码
		2、运行起来之后，会自动的在index.html中导入<script type="text/javascript" src="bundle.js"></script>

--------------------------# 内容回顾


## Webpack
	作用:构建项目，打包项目，在项目的开发阶段，配合一些插件，可以提高开发阶段效率
	
## Webpack的核心概念
	入口
		项目打包的一个文件，里面就包含(引入)项目中其它文件(js，css，xxx)
		
	输出文件
		项目打包完成之后，最终得到一个文件(bundle.js)
		webpack 入口文件 输出文件
	
	Loader
		能够使用Loader打包非.js文件
		参考:https://doc.webpack-china.org/loaders/

	插件
		提高开发效率，webpack性能优化(压缩、剥离)
	
		
	配置文件
		把需要在终端中输入的东西，写在一个配置文件，到
		时候会自动读取配置文件中的内容，进行打包操作，
		可以减少我们在终端中输入很长指令，造成书写出错

## Webpack指令后面接的参数
	
	--progess 查看打包进度
	--watch 自动监控源代码更改(webpack-dev-server替代他)
	-p 压缩代码，后面会利用webpack提供的插件
	--config 指定我们webpack到时候去读取哪个配置文件，打包
	


## 利用vue.cli搭建项目【补充】
	
	前提:安装vue-cli这个全局包
		npm install -g vue-cli
		cnpm install -g vue-cli
		
	按照文档提示生成我们的项目并且安装项目依赖的第三方包
		生成项目: 
			vue init webpack-simple vue_simple_demo
	
		安装第三方包:
			cnpm install
			
	cross-env 设置环境变量
			
	
-----------------------------------

## App.vue

### mint-ui(头部的标题栏和底部的tarBar)
	官网:https://mint-ui.github.io/#!/zh-cn
	
	介绍:基于 Vue.js 的移动端组件库
	
### mint-ui集成到项目中
	安装包：
		npm install mint-ui -S
	
	集成:
		import Mint from 'mint-ui'
	
		Vue.use(Mint)
	
### 在项目中使用
	css components 直接在我们.vue文件的template中写他的标签即可
	
	`import 'mint-ui/lib/style.min.css'`
	
	导入css的过程中，遇到问题，因为没有配置loader
	1、安装包: npm i style-loader css-loader --save-dev
	2、在webpack.develop.config.js中配置(见代码)
	
	使用tabBar见代码
	
### 中间内容如何实现？
	
	根据观察，我们发现中间这块内容是动态变化，当点击了对应的链接，呈现出来的就是不同的组件，需要使用路由去解决这件事
	
	1、Vue项目中如何集成Vue-Router
		参考:https://router.vuejs.org/zh-cn/installation.html
	
		安装vue-router
			npm i vue-router -S
		
		在main.js中写代码
			import VueRouter from 'vue-router'
			
			Vue.use(VueRouter)
	
	2、写代码实现路由的跳转
		创建home.vue
		
		在 App.vue中间部分，使用<router-view>来占位
		
		在 main.js中，导入home.vue，创建路由对象，设置路由规则，把路由对象注入到我们的Vue跟实例
			见代码...
			
### 点击底部TabBar如何切换路由，显示不同的组件
	步骤:
		1、创建底部TabBar对应的组件
		
		2、在底部的每个item通过router-link触发路由
			声明式导航
			
		3、在main.js中，导入组件，设置相应路由规则

-----------------------------------

## home.vue

### 轮播图
	mint-ui swipe
	
### 如何发送网络请求（vue-resource）
	集成
		安装 npm i vue-resource -S
		
		main.js中写代码
			import VueResource from 'vue-resource'
			
			Vue.use(VueResource)
	
	在home.vue中的created生命周期函数中，调用我们自己写的发送网络请求的函数，在这里面发送网络请求

	拿着服务器返回的数据，赋值给模型，会更新UI
			
### 生命周期钩子
	钩子就是函数
	
	每个组件，都有从创建到销毁的过程
	
	组件中的生命周期函数，都是Vue框架自动调用的，我们自需要实现对应的函数即可
	
	created:一般在这个生命周期钩子里面，发送网络请求

### 九宫格导航
	mui
	官网:http://www.dcloud.io/mui.html
	文档:
	Demo:http://www.dcloud.io/hellomui/
	
	集成:
		导入css，导入ttf
		
		使用file-loader url-loader 加载其它文件
			npm i file-loader url-loader --save-dev
		
		webpack.develop.config.js中配置
			{
                test: /\.ttf$/, 
                loader: 'url-loader'
            }

## home.vue

### 路由重定向
	main.js中的设置路由规则的地方，设置下
		{path:'/',redirect:'/home'}
		
### 轮播图
	vue-resource 
	集成:
		安装包
		在main.js中导入，并且使用Vue.use(xxx)
	
	使用:
		在created方法触发的时候，调用我们自己的方法，发送网路请求
		
	页面渲染
		mt-swipe 渲染轮播图
		
### 生命周期
	created
	
-----------------------

# 今日内容

## 新闻列表

### 跳转到新闻组件
	1、创建newlist.vue
	2、在main.js中导入并且设置路由规则
	3、给home.vue中的新闻咨询添加router-link

### 获取新闻列表的数据
	见代码 vue-resource

### 开发阶段与生产阶段因为IP和端口不一样，抽取IP和端口
	es6导出一个对象的写法
		export default{
    		属性名称：值
		}

### 渲染新闻列表
	使用的mui的图文列表(见代码)
	
### 时间格式化
	过滤器
		过滤器中使用moment
		
		参考：http://momentjs.cn/
		
	步骤:
		1、先把moment集成到项目中
			安装 npm i moment -S
		
		2、在main.js中导入moment
			import moment from 'moment'
			
		3、在main.js中定义全局过滤器，并且在里面使用
		moment格式化时间
		
		4、在需要的地方newslist.vue中通过管道符`|`调用全局的过滤器，对服务器返回的原始时间进行格式化

-----------------------
	
## 新闻详情

### 跳转到新闻详情，并且带上参数id
	1、创建newsinfo.vue
	2、点击新闻列表每一项，通过router-link触发链接
		/news/newsinfo/id号
	3、在main.js中导入组件，并且设置路由规则

### 发送网络请求
	vue-resource
	
### 渲染新闻详情组件

-----------------------

	
### this.$route & this.$router 有什么区别?
	$route 设路径相关
		比如监控路由、获取参数
		
	$router 执行者，执行一个动作。
		写js代码实现路由的前进和回退，也叫做编程式导航
		
		和他对应的有一个概念，声明式导航，事先现在(声明)在template里面

-----------------------

## 评论子组件【父子组件通讯】
	因为我们在新闻详情、图片详情、商品详情中都存在评论，并且都长得差不多，只是数据不一样，这个时候有两种实现方式
	
	方式1：把我们评论组件，在新闻详情、图片详情、商品详情都写一份，发送不同请求，获取不同的数据
	
	方式2：把评论的功能抽成一个子组件(subcomment.vue)，我们把包含评论子组件的新闻详情、图片详情、商品详情称之为父组件
	
### 新闻详情父组件如何集成评论子组件
	步骤:
		1、新建评论子组件(subcomment.vue)
		2、集成到父组件(参考:https://cn.vuejs.org/v2/guide/components.html)	
			2.1 、在父组件中导入子组件
			
			2.2 、在父组件中注册子组件
				```
					components:{
			            subcomment:subcomment 
			        }
				```
			2.3 、在我们父组件的template中使用子组件，就可以将子组件集成进来了
			
### 父组件如何把值传给子组件
	参考:https://cn.vuejs.org/v2/guide/components.html#构成组件
	
	子组件(接收方)
		在Vue对象中，通过props声明，声明它期待获得的数据
		props:['commentId']
	
	父组件(发送发)
		在使用子组件的时候，通过属性名称=值的方式，将值传给子组件
		<subcomment :commentId="this.$route.params.newsId"></subcomment>


## 新闻列表
	
## 评论子组件


### 父组件如何传值给子组件
	接收方:
		子组件的Vue对象，实现props，prpos中的名称就是到时候父组件传值的名称
		
	发送方:
		父组件在template中使用子组件的时候，通过属性名称=值的方式来传递


# 今日内容

## 图片分享列表
	头部的图片分类
		分类数据也是从服务器获取的
		
		步骤：
			1、获取分类数据
			2、渲染(ul > li)
	
	下面是每个分类对应的图片列表
		当点击了头部的分类id去发送请求获取，分类id对应的图片列表
		
		如果我们传递给后台的id=0，那么加载的就是全部数据
		
--------------------------

## 图片详情
	1、跳到详情组件，并且带上id
	2、到了详情组件，发送请求
	3、渲染组件
		集成评论子组件
			1、在父组件中导入评论子组件
			2、在父组件的components中注册子组件
			3、在父组件的template使用子组件，并且传参
	
	注意:
		图片详情中，数据是分两大块，一块是我们的图片详情的数据，另一块是我们详情中缩略图数组数据
	
	缩略图展示及浏览功能的实现
		1、先把缩略图展示出来
			利用了mui的九宫格布局
		
		2、再使用vue-preview当点击每一项的去预览我们当前点击的图片
			基于vue的
			
			参考:https://github.com/LS1231/vue-preview
			
			原生js实现图片预览:https://github.com/dimsemenov/PhotoSwipe
			
			原生:http://photoswipe.com/documentation/getting-started.html
			
		Vue中集成Vue-preview
			前提:
				1、安装 npm i vue-preview -S
				
				2、添加一个loader，打包压缩之前，必须做这件事
				
				3、在main.js中导入并且使用
					import VuePreview from 'vue-preview'
					Vue.use(VuePreview)
					
			项目中使用:
				1、给img添加点击事件
					 @click="$preview.open(index, 模型数组)"
	
			注意点:
				我们上面模型数组中的每个对象，图片的地址必须是src，宽和高，必须是w，h
			
## 组件的生命周期
	
### 什么是组件的生命周期
	1、代码的集合，相同的代码放在一个组件中去实现
	
	2、在Vue中每个组件都有生命周期，大部分组件都有从创建到销毁的这一个过程

### 什么是组件的生命周期钩子(函数)
	组件在运行过程中，会自动调用，一系列生命周期钩子(函数)
	
	beforeCreate : 准备性工作
		加载图片资源
	
	created : 组件创建出来了 this就有了
		一般是发送网络请求
			this.$http.get(xxx)
			提前做这个事情，用户体验会好一些...
			
	beforeMount:挂载之前
	
	mounted:挂在完毕
	
	beforeUpate()
	
	update()
	
	beforeDestory()
	
	destory()
	
	注意事项:
		1、这些生命周期钩子，我们程序员只需要实现即可，Vue底层会自动帮助我们调用
		
		2、我们可以在这些生命周期函数中实现自己的逻辑。。。
		
### 如何解决新闻详情中，评论子组件刚开始就出来，然后闪了一下的用户体验不太好
	1、给我们整个新闻详情组件通过一个isLoading来控制现在显示还是隐藏
	
	2、刚开始隐藏，当数据回来之后，再显示出来
	
### 组件生命周期的应用场景
	created: 发送网络请求
	
	记录上一次滚动到哪里?(以新闻列表为例)
		1、在新闻列表组件即将销毁beforeDestory的时候，记录当前的滚动位置
			window localStorage
		
		2、beforeMount&mounted 取出存储到window localStorage的值设置contentOffset top
	
	记录用户访问的痕迹
		当进入到某个组件的时候(created)，记录一个时间
		当退出某个组件(beforeDestory)，再记录一个时间
		
		当你在退出的时候，把时间戳和哪个组件发送给服务器
		
		App埋点
		
--------------------------------------
	
## 商品列表

### 获取数据
	axios
	
	前提(集成):
		安装包:npm install axios -S
		
	使用:
		axios.get(xxxx)
		



## 商品详情

### 跳转到商品详情组件
	1、创建商品详情组件
	2、跳转到商品详情组件，并且传递商品的id过去

### 抽取轮播子组件
	思路：
		把轮播的功能抽到一个单独的子组件中(subswipe.vue)
		
		在home.vue及goodsinfo父组件中集成进来
		
		在父组件集成子组件的时候，给我们的子组件传参 lunbo_url  lunbo_time
		
	步骤:
		1、定义subswipe.vue
		
		2、完成subswipe的逻辑，props:['lunbo_url','lunbo_time']
		
		3、在父组件中集成并且传值
			导入
			注册
			使用


### 编程式导航另外两种传值方式【了解】
	参考:
		https://router.vuejs.org/zh-cn/essentials/navigation.html
		
		方式1：
			this.$router.push({ name: 'pictureAndTextIntruduction', params: { goodsId: this.$route.params.goodsId }})
			
			还是根据我们params取
			
		方式:
			this.$router.push({path:"/goods/goodscomment" ,query:{goodsId:this.$route.params.goodsId}})
			
			获取值根据query来获取

### 数量选择子组件如何传值给父组件
	选择子组件中的值，当发生更改之后，要传递给我们
	的商品明细父组件，因为当我们点击商品明细父组件
	中的加入购物车按钮，我要知道你选择数量是多少，
	但是我这个商品明细父组件，是不能直接获取到子组
	件中的值的，这个时候，只有子组件当发生更改之
	后，告知父组件
	
	步骤:
		1、创建数量选择子组件
		
		2、在商品明细父组件中集成数量选择子组件
		
		3、当子组件中的值发生改变的时候，把这个值传给父组件
		
### 子组件如何传值给父组件
	方法:使用 v-on 绑定自定义事件
	
	发送方(子组件)
		通过$emit来触发自定义事件，传值
		
		this.$emit('numberChange',this.count)
			
	接收方(父组件)
		父组件可以在使用子组件的地方直接用 v-on 来监听子组件触发的事件，通过一个处理函数来接收子组件传递过来的参数
		
		<subnumber v-on:numberChange="getSubNumberCount"></subnumber>
		
		getSubNumberCount(count){}

-----------------------

## 加入购物车需要做的事情
	1、将数据从goodsinfo.vue中传给App.vue
		非父子组件之间传递值
		
		(和子组件传值给父组件很相似，都是通过自定义事件)

	2、将我们选中的商品和数量存起来?
		Vuex 存在内存中
		
		京东:没登陆，存在cookies中
			 登录后，京东的服务器
			 
		淘宝:存储到淘宝服务器
	
----------------------

## 非父子组件如何传值
	
	1、中央事件总线
		与子组件传值给父组件差不多，都是使用自定义事件，但是因为他们不是父子组件的关系，需要使用一个公共的Vue对象
		
		参考:https://cn.vuejs.org/v2/guide/components.html#非父子组件通信
		
		步骤:
			1、创建一个公共的Vue实例
				
			2、发送方(goodsinfo.vue)
				使用公共的bus，触发事件传值
				bus.$emit('事件名称',值)
				
			3、接收方
				使用公共的bus，监听事件，通过处理函数的参数获取值
				bus.$on('事件名称', 处理函数)

	2、Vuex(状态/数据管理)
		注意点:存在内存
		
---------------------

## Vuex

### 基本概念
	Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。
	实现项目中组件之间数据共享的
	数据是存在一个公共仓库中的，我们可以往仓库里面存值，也可以从这个仓库中取值，这样就达到了数据共享。
	
	一般我们需要`全局`用到的数据，才往仓库里面存
	
	注意点:
		1、不要把不相干的，或者说所有的数据，都尝试存在仓库中去，只需要把很多组件都用到的数据，才往里面存
		
		2、局部数据，放在各自的组件data里面即可，不要往公共的仓库中去存

### 核心概念
	
	一个完整的仓库
		State 存放数据 	商品信息
		
		Getters 专门从仓库中去数据的
		
		Mutations `同步`更改仓库中的数据的
		
		Actions `异步`更改仓库中的数据
			更改：往仓库中添加、修改、删除
			
	注意点:
		1、要往仓库中添加、修改、删除数据，一定要通过，Mutations/Actions去操作，不要直接操作State
		
		2、获取数据，一定要通过Getters去获取，不要直接操作State
		
		3、更改数据的时候
			组件(商品明细) ---> Mutations ---> State
			
			组件(商品明细) ---> Actions ---> Mutations ---> State
			 
		4、获取数据的时候
			State ---> Getters ---> 组件(购物车)

### 在项目中如何使用(加入购物车，购物车组件)
	
	1、前提（准备好仓库），集成Vuex
		参考:https://vuex.vuejs.org/zh-cn/installation.html
	
		安装vuex 
			npm i vuex -S
		
		在main.js中，导入并且Vue.use(xxx)
		
		
		创建一个仓库(store)
			见代码
	
		把我们上面创建好的仓库(store)，注入到根实例中，这样我们整个项目就能使用vuex实现数据管理
			见代码
	
	2、往仓库中存值和取值
		购物车的数据，每次当我们点击加入购物车的时候，其实是将我们此次选择的商品对象，加入到一个数据中
		
		State中定义一个装我们购买的商品对象的数组
		
		每个商品的对象 {goodsId:87,count:3}
		
		最终State存储的应该是这样
			[
				{goodsId:87,count:3},{goodsId:88,count:2},
				{goodsId:87,count:2}
			]
			
		点击购物车之后，如何去往仓库中添加数据
			参考：https://vuex.vuejs.org/zh-cn/mutations.html
			1、我们可以在 mutations 中定义函数
				addGoods(state,goodsObj){
			        state.goodsList.push(goodsObj)
			    }
		    
		    2、调用:
		    	```
		    		const goodsObj = {goodsId:this.$route.params.goodsId,count:this.myCount}

                	this.$store.commit('addGoods',goodsObj)
                	
		    	```
		    
		  注意点:
		  	同步和异步去更改数据
		  	同步 this.$store.commit(函数名称，值)
		  		同步 ---> state ---> goodsList
		  	
		  	异步 this.$store.dispatch(函数名称，值)
		    	异步 ---> 同步 ---> state ---> goodsList
		    	
		   获取值:
		   	写在getters中，都是通过函数返回，一定要return
		   	
		   	可以返回我们整个加入购物车的数组
		   	
		   	可以返回购物车数组中的总数量
		
---------------------# 管理系统

## 原生推荐
	官网:https://adminlte.io/
	
	github的地址:https://github.com/almasaeed2010/AdminLTE

## Vue版本
	https://www.awesomes.cn/repo/fundon/vue-admin
	https://vue-admin.fundon.me/#/
	
	https://github.com/taylorchen709/vue-admin
	https://taylorchen709.github.io/vue-admin
	
## fetch 
	https://segmentfault.com/a/1190000003810652
	
## 非父子组件传值
	1、通过中央事件总线的方式传值(bus)
		步骤:
			1、创建一个公共的bus
			2、发送发，使用bus.$emit(自定义事件的名称,传递的值)
			3、接收方，使用bus.$on(自定义事件的名称,处理函数)
	
	2、Vuex
		
## Vuex
	作用：
		`全局`存取数据
		
	核心概念：
		state 数据(数组、对象、基本数据类型...)
		
		getters
			获取 state 中的数据(暴露数据出去给别人用)
			
		mutations
			`同步`更改 state 中的数据
			
		actions
			`异步`更改 state 中的数据
			
		Modules
			多个仓库
			
	在项目中使用
		集成:
			安装 vuex: npm i vuex -S
			导入并且使用 import Vuex from 'vuex'
						Vue.use(Vuex)
						
			创建仓库 
				const store = new Vuex.Store({})
			
			注入到根实例
		
		使用:(使用购物车)
			思路:goodsList装的是每一个你点击添加到购物车的对象[{goodsId:87,count:3},{goodsId:88,count:2},{goodsId:87,count:2}]
		
			state
				goodsList : []
				
			点击添加到购物车
				1、在mutations中写好对应的方法
				
				2、this.$store.commit(函数名称，值)
				
			点击添加购物车拓展(通过actions)
				1、在actions中写好对应的方法，并且actions内部调用mutations
				
				2、this.$store.dispatch(异步函数名称,值)
				
			购物车展示页面(取)
				getters中的函数返回
				
			更改App.vue底部TabBar购物车徽标的值
				getters，返回当前添加到购物车中的值
	
-------------------------

# 今日内容

## 购物车的展示
	思路:
		1、获取需要展示的数据
		
		2、展示、渲染
		
		3、操作
		
### 获取需要展示的数据
	1、从Vuex中获取
		const goodsList = [
			{goodsId:88,count:2},{goodsId:87,count:3},
			{goodsId:88,count:3}
		]
		
	2、根据需要发送请求，去获取服务器最新的数据
		http://182.254.146.100:8899/api/goods/getshopcarlist/87,88
		
		如何把我们从goodsList变成87,88
		
		步骤:
			1、const tempObj ==> {88:5,87:3} 【除了这里用到，下面还会用到】
			
			2、const tempArray ==> [87,88]
			
			3、tempArray.join(',') ==> 87,88
			
		
	3、要展示之前我们的数据应该是这样
		[
			{id:87,title:'华为',sell_price:2195,thumb_path:'http:www.xxx.com/1.png',count:3},
			{id:88,title:'苹果',sell_price:5780,thumb_path:'http:www.ooo.com/1.png',count:5}
		]

### 操作
	问题：
		我们刚开始，每一项switch都是绑定到 同一个 switchValue : true
		这个时候因为是双向数据绑定，所有改了其中一行的switchValue，其它行，也跟着改
		
	解决办法:
		不要让每一行的switch绑定到同一个模型，应该分开绑定，这个时候我们把我们的模型，搞成一个数组，在绑定的时候，巧妙利用索引取出数组中的每一个值，分别绑定，这样就达到了分别绑定，互相不受影响的目的
		
	1、当我关闭Switch的时候，让对应行的删除按钮不可用
		https://mint-ui.github.io/docs/#/zh-cn2/button
		boolean值和开关的值相反
	
	
	2、当打开或是关闭Swith时候，重新计算我们统计信息
		因为我们改变开关的状态及删除某一行的时候，我们都需要重新计算，所有
		把重新计算的方法单独抽取出来
		
		因为我们switchValues数组的索引和goodsList索引一致
		遍历switchValues ，然后，获取到boolean为true的索引，然后
		根据这个索引去goodsList取出商品信息累加起来
	
	3、但我们删除了某个商品之后，需要做事(统计信息重新算、干掉数组中的值、仓库中的数据干掉)
		前提:获取你要删除那一行的索引值
		
		//1.获取到索引对应的商品id,然后从仓库中干掉
			如果在遍历的过程中，需要边遍历，边删除，从后往前删

        //2.干掉switchValues和goodsList中，对应索引的元素

        //3.重新计算统计信息

-------------------------

## Webpack上线前打包优化

### 我们要给生产阶段的Webpack再单独搞一个配置文件
	1、webpack.publish.config.js (在webpack.develop.config.js的基础上再增加一些代码)
	
	2、使用webpack打包我们的源代码
		webpack --progress --config webpack.publish.config.js
		
### 打包之前，把上一次dist目录下面的东西干掉，再生成新的
	安装 clean-webpack-plugin  npm i clean-webpack-plugin --save-dev
	
	在我们的插件第一个配置项目中，加上一句话
		
		
### 为什么打包出来的bundle.js这么大
	1、没压缩
	
	2、把项目中的其它资源从bundle.js抽离/剥离   达到像百度这样的目的
		抽离图片
		
		抽取第三方包
		
		抽离css
		

	
### 解决办法之压缩JS
	1、压缩(见代码)  webpack自带的压缩【压缩之前把代码用babel从es6转成es5】
		webpack目前只支持一部分es6--->es5
		
		
		
		
		1、使用babel在压缩之前，对代码进行es6--->es5
			参考:https://babeljs.io/
			    https://babeljs.io/docs/setup/#installation
			    
			步骤:
				1、安装包 npm install babel-loader babel-core babel-preset-env --save-dev
				
				2、配置一个babel的配置文件
					在项目根路径下，创建一个.babelrc的文件，写好配置见代码
					
				3、需要在loaders中配置对.js结尾的转换
					{ 
		                test: /\.js$/, 
		                exclude: /node_modules/, //第三方的不管
		                loader: "babel-loader" 
		            }
		            
		         4、因为用了vue-preview，所以还得额外设置
		         	{
		                test: /vue-preview.src.*?js$/,
		                loader: 'babel-loader'
		            }
		
		2、在webpack.publish.config.js的plugins中配置
		
			```
				new webpack.optimize.UglifyJsPlugin({
			      compress: {
			        warnings: false
			      }
			    })
			```
			
		3、压缩升级
			删除版权相关信息
				见代码
				
			把项目设置成生产环境
				new webpack.DefinePlugin({
		            'process.env': {
		                NODE_ENV: '"production"' //加载xxx.min.js
		            }
		        })
		        
		     压缩html
		     	参考:https://github.com/jantimon/html-webpack-plugin
		     		https://github.com/kangax/html-minifier#options-quick-reference
		     		
		     	new HtmlWebpackPlugin({  // Also generate a test.html
		            filename: 'index.html', //内存中生成的文件名称
		            template: './template.html', //模版文件
		            minify:{//压缩html中哪些东西
		                collapseInlineTagWhitespace:true,
		                minifyCSS:true,
		                minifyJS:true,
		                removeComments:true
		            }
		        })
		
		参考:https://cn.vuejs.org/v2/guide/deployment.html
			
### 解决办法之抽离图片
	图片是怎么打包进入bundle.js
	base64 

	给我们的loader配置参数
		{
                test: /\.(ttf)$/, 
                /*limit：
                    表示的是一个阀值,如果当前我们资源中的图片大小
                    4kb就从bundle.js中剥离出来，如果小于4kb打包进bundle.js

                    name:打包出来的图片，放在那个文件夹下，用什么文件名称命名
                    [name]代表你原始的文件名称
                    [hash:5] 让浏览器支持图片的缓存
                    [ext] 图片本身的拓展名
                */
                loader: 'url-loader?limit=4000&name=fonts/[name]-[hash:5].[ext]'
            },
            {
                test: /\.(png|svg|gif)$/, 
                /*limit：
                    表示的是一个阀值,如果当前我们资源中的图片大小
                    4kb就从bundle.js中剥离出来，如果小于4kb打包进bundle.js

                    name:打包出来的图片，放在那个文件夹下，用什么文件名称命名
                    [name]代表你原始的文件名称
                    [hash:5] 让浏览器支持图片的缓存
                    [ext] 图片本身的拓展名
                */
                loader: 'url-loader?limit=4000&name=images/[name]-[hash:5].[ext]'
            }
 
## 抽离第三方包
	1、把第三方包不打包进入 bundle.js，单独打出来(vue.js,vueRouter.js)
	
	2、在我们的index.html中通过script导入bundel.js vue.js vueRouter.js
	
	参考地址:
		http://www.cnblogs.com/answercard/p/6108200.html
	
	步骤:
		1、在entry中改
			entry:{
		        //属性名称代表你打包出来的最终的文件名称
		        //值，代表你要打包的是哪个第三方包(名称看node_modules中)
		        quanjiatong:['vue','vue-router','vuex'],
		        vuePreview:['vue-preview'],
		        vueResource:['vue-resource'],
		        moment:['moment'],
		        mintUI:['mint-ui'],
		        axios:['axios'],
		        jquery:['jquery'],
		        bundle:path.join(__dirname,'src/main.js') //打包自己的业务逻辑代码，别忘记了
		    },
		
		2、在output改
			output: {
		        path: path.join(__dirname,'dist'), //bundle.js放的目录
		        //filename: 'bundle.js' //打包出来的文件名称
		        filename: 'js/[name].js'
		    },
		
		3、在plugins中改
			//这个地方有个小注意点，不要把自己业务逻辑bundle放在这里，
	        //这里只放第三方
	        new webpack.optimize.CommonsChunkPlugin({name:["jquery","axios","mintUI","moment","vueResource","vuePreview","quanjiatong"],minChunks: Infinity})
	        
## 抽离CSS
	参考:https://github.com/webpack/webpack
	https://github.com/webpack-contrib/extract-text-webpack-plugin

	前提:
		安装包 extract-text-webpack-plugin
			npm i extract-text-webpack-plugin --save-dev
		
	步骤:
		1、导入
			const ExtractTextPlugin = require("extract-text-webpack-plugin")
			
		2、css-loader中改
			module: {
			    rules: [
			      {
			        test: /\.css$/,
			        use: ExtractTextPlugin.extract({
			          fallback: "style-loader",
			          use: "css-loader"
			        })
			      }
			    ]
			}

-------------------------