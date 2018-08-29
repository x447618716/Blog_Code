---
title: hexo安装
date: 2017-07-09 18:39:28
category: Hexo
tags: hexo
---
![](/images/timg2.jpg)
<!-- more -->
## 安装准备
1.安装 [Hexo](https://hexo.io/zh-cn/) 相当简单。然而在安装前，您必须检查电脑中是否已安装下列应用程序：
* [Node.js](https://nodejs.org/en/)
* [Git](https://git-scm.com/)

下载安装包，点击安装包，点击下一步直到完成即可，node安装完后在命令行运行 node -v（查看版本），如果成功说明node安装成功，不成功可能是环境变量问题，去配置一下或重新安装下.
同理安装git，安装完后再命令行运行git version（查看版本），如果成功说明git安装成功
## 安装hexo
1.如果您的电脑中已经安装上述必备程序，那么恭喜您！接下来只需要使用 npm 即可完成 Hexo 的安装。
```javascript
npm install -g hexo-cli
```
2安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
```javascript
hexo init <folder>
cd <folder>
npm install
```
会生成如下结构的文件：
>.
├── _config.yml  站点配置文件
├── package.json  站点依赖文件
├── scaffolds  模板文件夹
├── source 资源文件夹
|   ├── _drafts
|   └── _posts
└── themes  主题文件夹

最后一步你npm install不可少，它主要功能是用于安装package.json中的依赖，当有改动package.json中的依赖时都要运行一次
到此hexo安装就算完成了，然后在命令行运行
```javascript
hexo sever
```
就可以看到hexo默认主题效果了
## hexo常用命令
```javascript
hexo init [folder] 新建一个网站
hexo new [layout] <title> 创建一篇新文章
hexo sever或hexo s 启动服务器
hexo clean 清除缓存文件 (db.json) 和已生成的静态文件 (public)
hexo generate或hexo g 生成静态文件
hexo deploy或hexo d 部署网站
hexo migrate <type> 从其他博客系统迁移内容



```
