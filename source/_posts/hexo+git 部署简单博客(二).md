---
title: hexo+git 部署简单博客(二)
date: 2018-01-31 16:16:52
tags: [hexo,git]
categories: [git]
---
上一次我们已经搭建好了简易的博客,但是默认的样式是不是不好看呢,还有怎么通过网络来访问我们的博客,废话不多说,接下来我们就开始进行美化和上传吧
### 上传到git  ###
* 首先我们用编辑器打开你的博客,找到  `_config.yml`,打开这个文件,在里面找到
>deploy:
  type: git 
  repo: https://github.com/YourgithubName/YourgithubName.github.io.git   # 替换成你自己的地址
  branch: master
 <!--more-->
* 在你的博客所在文件夹下,鼠标单击右键,打开 `Git Bash Here`输入`npm install hexo-deployer-git --save`只有这样才能让别人通过浏览器浏览到
* 执行以下命令
> hexo clean &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #清除缓存
hexo generate  &nbsp;&nbsp;# 生成静态页面
hexo deploy  	&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# 执行hexo deploy命令部署到GitHub上的内容目录

* 部署成功的话,在浏览器中输入`http://yourgithubname.github.io`,就可以看到你的博客了,这样就大功告成了

#### 绑定域名
* 首先买一个域名,我是在[阿里云](https://wanwang.aliyun.com/?spm=5176.8006371.388261.261.64f9c02ayj6d2q)购买的,也可以去其他的网站购买,比如[GoDaddy](https://sg.godaddy.com/zh/),[腾讯云](https://dnspod.cloud.tencent.com/?from=qcloudProductDns)等等
* 在博客下的`source`文件夹下新建一个**没有后缀的并且大写**的`CNAME`文件,里面放入你的域名,切记**没有www 或者 http**,就比如是`baidu.com`
* 执行下`hexo g` && `hexo d`  上传你的部署
* 接下来去万网解析
> 先添加一个CNAME，主机记录写@，后面记录值写上你的http://xxxx.github.io
再添加一个CNAME，主机记录写www，后面记录值也是http://xxxx.github.io

* 具体实现,参考 知乎的回答 地址:https://www.zhihu.com/question/31377141

### 美化换主题###
* hexo 默认的主题有点不适应,没问题,我们可以换主题 [地址](https://hexo.io/themes/),里面有别人做好的主题,我们只需要克隆下来,做些简单的修改就可以使用了
* 选择你自己看中的主题,点击进去,选择它所提供的命令即可克隆到本地
* 我所使用的是`next`主题
* 安装完成后打开`hexo\_config.yml` 找到`theme: `后面写入你的主题名称即可,冒号后面要有一个空格
* 然后在`themes`文件夹下找到对应的文件夹,在里面配置即可

#### 一些常用命令 ####
>hexo new "postName" &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; #新建文章
hexo g == hexo generate &nbsp;&nbsp;&nbsp;#使用 Hexo 生成静态文件快速而且简单
hexo s == hexo server &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#启动服务预览,本地预览
hexo d == hexo deploy&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#部署到git

#### 上面的详细操作可以参考以下文章链接####
* [hexo从零开始到搭建完整](https://www.cnblogs.com/visugar/p/6821777.html)
* [hexo你的博客](http://ibruce.info/2013/11/22/hexo-your-blog/)