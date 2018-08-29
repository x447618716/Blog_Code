---
title: 项目部署到github
date: 2017-07-09 19:03:07
category: Hexo
tags: git
photos:
---
![](/images/timg3.jpg)
<!-- more -->
## 准备工作
## 下载git
地址：[https://git-scm.com/downloads](https://git-scm.com/downloads)然后默认安装即可
## 注册账号，创建仓库
首先上[https://www.github.com](https://www.github.com)注册一个账号，然后点击右上角个人头像，点击”profile”，进入界面后。点击”Repositories”进入，仓库界面击右方的”New”即可新建一个新仓库了。
##  配置git
1.设置用户名和邮箱。双击Git Bash，出现命令行界面。输入如下两行命令：
```javascript
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```
2.创建本地的ssh key。双击Git Bash，出现命令行界面。输入 ssh -keygen -t rsa -C "XXXXXX@XXXX.com"。然后把后面的邮箱替换成你的注册邮箱。然后一路回车，采用默认路径和空密码。接着会在默认路径下生成.ssh的文件夹，用编辑器打开id_rsa.pub复制里面的密钥。
3.进入github，点击头像上的”Setting”，左侧有个SSH Keys，点击它，进入页面。点击右侧的”Add SSH key”，自己输入一个标题，然后把密钥赋值进去即可。
4.测试一下是否成功，进入git bash，输入 ssh -T git@github.com。第一次会提示，是否continue，yes后就会看到：You’ve successfully authenticated, but GitHub does not provide shell access。这就说明成功了。
## 仓库初始化
## 第一种本地初始化流程：
1.创建项目，选择你项目所在的文件夹，鼠标右键，“Git Bash Here”，进入。然后输入命令：git init，创建本地git
2.然后给仓库添加远程地址，输入命令： git remote add origin git@github.com:yourName/yourRepo.git yourName是你的用户名，yourRepo是你的仓库名。
3.接着输入命令：git pull --rebase origin master 将github上仓库的文件和本地文件同步。
## 第二种直接克隆github仓库到本地
1.进入需要存放项目的文件夹，鼠标右键，“Git Bash Here”，进入。然后输入命令： git clone git@github.com:yourName/yourRepo.git yourName是你的用户名，yourRepo是你的仓库名
2.然后进入克隆下来的文件夹，在此写入你的代码
## 上传代码
1.输入命令：git add acm.cpp可以选择需要上传的单文件，或者git add -A，将当前目录下的所有文件上传。
2.第一步之后，git commit -m "XXX" 上传文件，双引号内为文件的一些描述，多文件会统一使用这个描述。
3.最后，输入命令：git push -u origin master即可将文件将文件同步到github上了。之后想要上传、更新，重复第五步即可。

