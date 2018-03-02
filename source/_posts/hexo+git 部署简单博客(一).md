---
title: hexo+git 部署简单博客(一)
date: 2018-01-31 16:16:52
tags: 
- hexo
- git
categories: [git]
---
首先,我们要知道一个哲学问题
我是谁,我在哪,我能干什么

hexo出自台湾大学生tommy351之手，是一个基于Node.js的静态博客程序，其编译上百篇文字只需要几秒。hexo生成的静态网页可以直接放到GitHub Pages，BAE，SAE等平台上。

搭建过程你或许觉得有那么点小繁琐，但一旦搭建完成，写文章是极简单，极舒服的。
只需要几个简单命令，你就可以完成一切。

<!--more-->

```
hexo n   #写文章
hexo g   #生成
hexo d   #部署 # 可与hexo g合并为 hexo d -g
```

### 准备工作 ###

 * 安装Node [下载地址](https://nodejs.org/en/),选择系统对应.msi的版本, 打开下载好的.exe,点击安装,一路next,很简单的小操作
 *  安装git,[下载地址](https://git-scm.com/downloads),同样选择对应的版本,安装方法同上
 ### 注册GitHub账号,连接GitHub ###
 在git[地址](https://github.com/)上注册好
 * 建立对应的仓库
 ```
 1.在主页点击 + 
 2.点击 New repository
 3.
 ```
 
 * 添加ssh-key
 *  单击鼠标右键 打开Git Bash,输入下面的命令
 ```
 git config --global user.email "your.email" 
 git config --global user.name "yourname"
 ```
* 继续创建ssh ,输入下面的命令
```
ssh-keygen -t rsa -C "your.email"
```
* 路径和密码
```
Enter file in which to save the key (//.ssh/id_rsa):  这里写路径,也可以不写,后续输入 y 确认就行
Enter passphrase (empty for no passphrase): 这里是你的密码
Enter same passphrase again: 再次输入密码,这两次密码都不显示
```
*  执行成功后, 根据提示找到并打开  id_rsa.pub 复制里面的内容
*  在网页上打开你刚刚注册好的的git,点击头像找到  settings  在打开的页面找到  SSH and GPG keys 
*  完成
### 安装hexo ###
* 很简单,参照 hexo [官网](https://hexo.io/) 
```
npm install hexo-cli -g
```
* 你可以现在本地创建一个文件夹,进入到新建的文件夹 ,单击鼠标右键 打开Git Bash,输入以下命令
```
hexo init
```
* 你就可以看到很多的文件以及文件夹(ps:说明一下)
  * node_modules：是依赖包
  * public：存放的是生成的页面
  * scaffolds：命令生成文章等的模板
  * source：用命令创建的各种文章
  * themes：主题
  *  _config.yml：整个博客的配置
  *   db.json：source解析所得到的
  *  package.json：项目所需模块项目的配置信息
* 生成页面
  * 在你的文件夹内执行下面两条命令
  * 第一条命令是生成静态页面,第二条是本地启动
 ```
 hexo generate 
 hexo server
 ```
 * 浏览
浏览器输入  [http://localhost:4000](http://localhost:4000)就可以看到效果。

### 完成 ####
* 接下来就是一些美化,和部署到  git 上了
