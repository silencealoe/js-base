为什么使用webpack?
网页中引入的静态资源太多会出现什么问题？    
（1）网页加载速度慢，因为要发起很多二次请求（浏览器从上往下解析从服务器返回的代码，碰见script等标签会向服务器发起请求，这样的标签多的话，会使网页加载速度变慢）
（2）要处理错综复杂的依赖关系

如何解决上述问题？
合并，压缩，精灵图，图片的base64编码（0次请求适合小图片）
使用webpack可以解决各个包之间的复杂依赖关系

什么是webpack?
前端一个项目构建工具，基于node.js开发

webpack和gulp区别？
gulp:基于任务（小巧,灵活）
webpack:基于项目构建，实现资源的合并，打包，压缩，混淆等功能


webpack可以做：
1.能够处理js之间的互相依赖关系
2.能够处理js兼容问题，把高级浏览器不兼容的语法，转为低级浏览器能识别的语法
3.运行的命令格式 ： webpack 要打包的文件路径 打包好的文件路径

webpack.config.js  配置文件  （配置后直接输入webpack即可）

输入webpack后，
webpack去项目的根目录中查找webpack.config.js配置文件，解析执行这个配置文件，解析执行完，得到配置文件导出的配置对象，拿到配置对象后，就拿到了指定的入口和出口，执行打包和构建

使用webpack-dev-server 实现自动打包编译功能
运行 npm i webpack-dev-server -D 把这个工具安装到项目的本地开发依赖
本地安装的命令不能当做脚本命令在终端运行，只有全局安装的 -g 的工具，才能在终端运行

webpack-dev-server打包生成的bundle.js，并没有存放在实际物理磁盘上，而是托管到了电脑的内存中，所以在项目根目录中找不到。

可以认为webpack-dev-server把打包好的文件以一种虚拟的形式，托管到了项目的根目录中，虽然看不到，但是 和dist,src平级有一个看不见的文件叫做bundle.js
方便打包构建，放入内存中
磁盘转速慢，消耗磁盘

常用命令参数
"dev":"webpack-dev-server --open --port 3000 --contentBase src --hot" 启动项目自动打开浏览器，设置端口为3000
--contentBase src  设置打开浏览器进入的根路径
--hot 减少不必要的代码更新，无刷新加载页面


将html页面放进内存中
npm i html-webpack-plugin -D  在内存中生成html页面的插件
只要是插件就要放到plugins中
作用：1.自动将打包好的bundle.js插入到页面，我们不需要关心依赖的路径
2.自动在内存中，根据页面生成一个内存中的页面


如果要处理非js类型的文件，需要手动安装一些适合第三方loader加载器
打包处理css文件，需要安装npm i style-loader css-loader -D
在webpack.config.js中新增节点module是一个对象，在这个对象上，有个rules属性，是个数组，这个数组中存放所有第三方文件的匹配和处理规则

webpack处理第三方文件类型的过程：
1.发现要处理的文件不是js文件，然后就去配置文件中查找有没有对应的第三方loader规则
2.如果找到对应的规则就会调用对应的loader处理这种文件类型
3.在调用loader的时候是从后往前调用
4.当最后一个loader调用完毕，会把处理的结果，直接交给webpack进行打包合并，最终输出到bundle.js中去

打包处理less文件
npm i less-loader -D

打包处理scss文件
npm i sass-loader -D


webpack基本配置
全局安装webpack
npm i -g webpack

1.创建文件夹，执行npm init -y 生成package.json文件
2.新建文件夹，src和dist,在src下新建index.html和main.js










