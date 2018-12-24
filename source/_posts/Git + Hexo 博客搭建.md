---
title: Git + Hexo 博客搭建
date: 2018-12-25
tags: [hexo, git]
categories: 搭建git博客
---

搭建博客，一来想着用博客可以记录一下自己的笔记，二来想通过搭建博客熟悉一下GitHub的使用。

## 结合Git和Hexo搭建博客

### NodeJs环境搭建

安装node：[nodejs](https://nodejs.org/en/)

### 安装hexo

选择一个空目录，右键git-bash here，输入以下命令安装hexo到全局：
``` bash
$ npm install -g hexo-cli                        //使用npm全局安装hexo命令行工具
$ hexo init                                      //初始化一个新的博客
$ npm install                                    //安装npm包
```

#### 添加环境变量

找到C:\Users\Administrator\AppData\Roaming\npm\node_modules\hexo\bin\，将此目录添加到环境变量中

#### 部署Github的准备

``` bash
$ npm install hexo-deployer-git --save    	      //安装hexo部署工具
```

### 判断hexo是否安装成功

``` bash
$ hexo -v        //版本号
```

### 修改hexo的配置文件（—config.yml）的部署方式：

``` bash
deploy:
type: git
repo: git@github.com:ckhongme/ckhongme.github.io.git
branch: master
```

#### 本地浏览自己的博客 （在浏览器中输入 http://localhost:4000/ 查看生成的页面效果）

``` bash
$ hexo s                            //server
```

### 传送到Github

在hexo目录， 右键git-bash here，进入bash命令行：

``` bash
$ hexo clean                       //清理生成的博客
$ hexo g                             //生成静态文件：博客文件     generate
$ hexo d                             //部署到github上                 deploy
```

### 拷贝别人的Blog主题

``` bash
$ git clone https://github.com/blogOwner/hexo-theme-name.git themes/name
```

### 设置网站

对整体的设置：只要修改项目目录的_config.yml
对局部的设置：页面展现的全部逻辑都在每个主题中控制，源代码在hexo\themes\主题名_config.yml中

### 写博客
将写好的markdown文件，存放到/source/-posts文件夹中

### 发表新文章

``` bash
$ hexo new "postName "             //新建文章
$ hexo new page "pageName"         //新建页面
```