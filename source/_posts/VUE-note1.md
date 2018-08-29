---
layout: post
title: vue学习笔记一
description: vue学习笔记 记录学习的每一刻 充实自己 超越自己 做非凡的我
keywords: vue 、 渐进式框架 、JavaScript 框架
date: 2018-05-14 15:15:18
updated:
category:
- html
tags:
- vue
photos:
---
![](/images/timg10.png)
<!-- more -->

## Vue兼容性与其所需求的环境

### 在开始学习有必要先了解下vue兼容性问题：

> Vue 不支持 IE8 及以下版本，因为 Vue 使用了 IE8 无法模拟的 ECMAScript 5 特性。但它支持所有兼容 ECMAScript 5 的浏览器。

这就意味着要想能支持ie6，ie7等这中老年人浏览器，你就不得不放弃使用vue的选择了。

### vue所需求的开发环境：

在用 Vue 构建大型应用时推荐使用 NPM 安装。NPM 能很好地和诸如 webpack 或 Browserify 模块打包器配合使用。同时 Vue 也提供配套工具来开发单文件组件。
```shell
# 最新稳定版
$ npm install vue
```

就此本机上就需要安装**[node.js](https://nodejs.org/en/)**

要想做一个基于vue的完整项目，vue官方提供了一个很好的命令行工具，它可用于快速搭建大型单页应用。该工具为现代化的前端开发工作流提供了开箱即用的构建配置。只需几分钟即可创建并启动一个带热重载、保存时静态检查以及可用于生产环境的构建配置的项目：
```shell
# 全局安装 vue-cli
$ npm install --global vue-cli
# 创建一个基于 webpack 模板的新项目
$ vue init webpack my-project
# 安装依赖，走你
$ cd my-project
$ npm run dev
```

如果你只想在项目单页中使用vue进行开发，那你就无需考虑vue开发环境的问题，直接在单页中引入vue.js单文件即可
```html
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.16/dist/vue.js"></script>
```

## 利用vue脚手架工具创建vue项目

* 说完兼容性和开发环境现在正式动手来创建一个vue项目了：

首先打开windows命令行工具（win+R）输入cmd点确定进入命令行输入窗口或熟悉webstorm在其终端输入也是一样的：
```shell
   //安装最新稳定版(已安装就不用咯)
   npm install vue
   //全局安装 vue-cli(已安装就不用咯)
   npm install --global vue-cli
   # 创建一个基于 webpack 模板的新项目( 要想创建其他的模板把webpack替换下就可以了 vue-cli会相应的下载该模板)（前面两步有安装的直接进入这步开始操作）
   vue init webpack my-project
   //等一小段webpack模板下载时间，会出现
   //输入项目名称，不填会默认为 my-project
   ? Project name
   //输入项目说明，不填会默认为 A Vue.js project
   ? Project description A Vue.js project
   //输入作者名称，不填会默认为 x447618716 <447618716@qq.com>
   ? Author (x447618716 <447618716@qq.com>)
   //vue构建会让我们选择
   ? Vue build (Use arrow keys)
   Runtime + Compiler: recommended for most users  运行时+编译器：推荐给大多数用户(我选择)
   Runtime-only: about 6KB lighter min+gzip, but templates (or any Vue-specific HTML) are ONLY allowed in .vue files - render functions are required elsewhere   运行时：大约6KB较轻MI+GZIP，但是模板（或任何特定于VUE的HTML）只允许在.VUE文件中-在其他地方需要渲染函数
   //是否安装路由(我选择y)
   ? Install vue-router? (Y/n)
   //是否使用ESLint管理或规范代码 代码一步规范就会报错（一个空格错误都会哦），不开启，避免不必要的麻烦(我选择n)
   ? Use ESLint to lint your code? (Y/n)
   //是否设置单元测试（我选择n）
   ? Set up unit tests (Y/n)
   //是否用Nightwatch设置E2E测试（我选择n）
   ? Setup e2e tests with Nightwatch? (Y/n)
   //项目创建后，我们应该为您运行“NPM安装”吗？（我选择npm）
   Yes, use NPM 是的 使用npm
   Yes, use Yarn  是的 使用Yarn
   No, I will handle that myself 不  我自己处理。
```

等一段时间下载及安装依赖完成后如图：

![](/images/tips3.png)

然后在控制台或终端输入：
```shell
  //进入项目目录
  cd my-project
  //运行vue
  npm run dev
```

![](/images/tips4.png)

打开浏览器输入得到的地址：http://localhost:8081

能看到如下说明vue项目创建成功

![](/images/tips5.png)



