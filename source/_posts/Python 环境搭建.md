---
title: Python 环境搭建
date: 2019-01-01
tags: [Python]
categories: 脚本语言
---
中途插入一下字符编码的复习~~

## 开发环境搭建
1. 安装[Python](https://www.python.org)
2. Python解析器: 安装好之后直接获得官方的解析器：CPython
3. 文本解析器：Sublime Text (编辑完之后保存为.py 文件)


### 运行Python
Python交互模式的代码是输入一行，执行一行；而命令行模式下直接运行.py文件是一次性执行该文件内的所有代码。

#### Python交互模式的启动和退出：
- 运行：打开命令提示符窗口，输入python，进入python交互式环境（也就是启动了CPython解析器，它的提示符是>>> ）；
- 退出：输入 exit() 并回车；（交互模式主要用于调试）

#### 命令行模式下：（执行.py文件只能在命令行模式下）
1. cd 指定目录
2. 输入以下命令：`python xxx.py`