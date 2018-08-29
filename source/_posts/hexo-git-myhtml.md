---
title: 使用Hexo和github打造个人博客
date: 2017-07-09 19:04:07
category: Hexo
tags:
- hexo
- github
photos:
---
![](/images/timg1.jpg)
<!-- more -->
## 准备工作
了解[hexo安装](http://xierongsheng.science/hexo-install.html)和[github项目部署](http://xierongsheng.science/hexo-theme-create.html)
## hexo部署到github
```javascript
deploy:
  type: git  部署类别
  repo: git@github.com:yourName/yourRepo.git  你的仓库地址
  branch: master   部署到分支
  message:   说明
```
这时如果直接hexo d  会报找不到git，在项目文件中找到package.json打开添加依赖
```javascript
  "dependencies": {
    "hexo-deployer-git": "^0.3.0"
  }
```
打开命令行安装依赖
```javascript
 npm install
```
这时就可以运行部署命令 hexo d
## 开启github页面
部署成功后，返回部署的仓库地址找到setting,如图：
![](/images/tips1.png)
点击进入找到GitHub Pages，如图：
![](/images/tips2.png)
自定义域名需要到阿里云去申请自己的域名，只需一顿饭的钱，如果不想自定义可以不设，github会给你一个以你账户名开头的域名地址，然后直接点击该域名或你自定义的域名就可以查看你的博客了 