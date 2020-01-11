---
title: Git-环境搭建
date: 2019-12-30
tags: [git]
categories: Git相关
---

要使用Git工具，就需要先进行环境设置；

## 安装Git
下载git的客户端：[Git官网](https://git-scm.com/download/)；

### 进行git的环境变量配置
配置Path变量，就可以直接通过cmd界面来调用git了；

1. 复制Git安装目录下cmd文件夹的目录路径；
2. 我的电脑->属性->高级系统设置->高级->环境变量->选中系统变量下的Path->编辑按键->新建->黏贴路径；

### 测试Git是否安装好
1. 使用快捷键win+R，输入cmd，打开Dos命令行； 
2. 输入git或者git --version；

## 配置SSH keys
通过ssh密钥来授权，就可以不用每次连接Github都输入用户名和密码了；

### 检查SSH密钥
找个文件夹，右键 git bash here，输入
```
$ ~/.ssh
```
如果出现以下回复，就表示已经有SSH Key；
```
bash: /c/Users/XX/.ssh: Is a directory
```

### 创建SSH密钥
1. 如果没有ssh密钥，需要生成新的ssh密钥：（需要填上你自己的邮箱，所以需要先到git官网注册一个账号；）
```
$ ssh-keygen -t rsa -C user@email.com
```
2. 保存到默认的位置就好，push文件的时候，我们也不希望每次都输入密码，所以一直回车确认即可，不需要输入什么；
```
Generating public/private rsa key pair. 
# Enter file in which to save the key (/c/Users/you/.ssh/id_rsa): [Press enter]
Enter passphrase (empty for no passphrase): 
# Enter same passphrase again:
```
3. 在电脑C盘的User目录下找到.ssh目录，查看里面是否有 id_rsa（私钥），和id_rsa.pub（公钥）

### 绑定SSH密钥
1. 在浏览器登陆github账号，点击右上角头像，选择下拉菜单中的Settings，再找到SSH and GPG keys，创建一个新的SSH key； 
2. 用文本方式打开公钥，复制里面的内容，粘贴到刚才在github上创建的SSH key中；

### 判断ssh是否能连接到Github
输入以下命令，同样一直回车即可；
```
$ ssh -T git@github.com
```

## 账号设置
因为git是分布式版本控制系统，所以每个机器都必须自报家门；（会把这些信息写入到每一次的提交中）

### 全局账号
设置全局邮箱和全局用户名（邮箱地址和账户名，在一部电脑只需要设置一次即可）
```
$ git config --global user.email 你的github邮箱地址
$ git config --global user.name 你的github用户名
```
### 独立账号
如果对某个仓库有个别需求，需要指定其他用户名和邮箱的，可以在该项目的根目录下进行配置
```
$ git config user.email 你的github邮箱地址
$ git config user.name 你的github用户名
```