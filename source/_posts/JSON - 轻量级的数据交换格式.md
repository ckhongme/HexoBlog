---
title: JSON 轻量级的数据交换格式
date: 2019-11-17
tags: [JSON, JavaScript, Web开发, 数据交换格式]
categories: 标记语言
---

在了解一样新事物时，应该从它的起源开始了解，去理解它为什么被创造出来，有什么意义；

## JSON的起源

在Json出现之前，网络传输主要通过纯文本格式（便于网络传输）的XML，然而XML不太适合数据交换；

XML的定位是标记语言，面向的是文档，它的一系列规范，例如DTD，XSD，XPath等就使得学习成本大大增加了，很难简单使用，它的内容有很多尖括号和冗长的标签，难以定位实际要传输的信息；于是，有JavaScript的大宗师(Yoda)之称的Douglas Crockford，就设计了一种同样基于文本的数据交换格式Json；


## 什么是JSON
Json（JavaScript Object Notation）是一种轻量级的数据交换格式。
JavaScript对象标记语言， 是JS对象的字符串表示法，它使用文本表示一个 JS 对象的信息，本质是一个字符串；采用完全独立于语言的文本格式；

## JSON的作用
Json可以将 JavaScript对象 中表示的一组数据转换为字符串，然后就可以在网络或者程序之间轻松地传递这个字符串，并在需要的时候将它还原为各编程语言所支持的数据格式。

## JSON的优点

1. 定位是数据交换格式，设计目的就是在应用程序间传递结构化信息；
2. 具有更加清晰的层次结构，语法少，结构可预测，更容易被人类和计算机理解；
3. **超轻量级**：具有更加简单的语法格式，没有严格的闭合标签，所以在结构上少了很多字符，有效数据率更高，减少了在同等数据流量的情况下，网络的传输压力，节约了传输数据所占用的带宽，因此给网络传输带来了很大的便利； 
4. 使用方便，有JavaScript解析器就可以直接使用JSON；


## JSON的语法规则

- 数据在**键值对**中 
- 数据由**逗号**分隔
- 大括号保存**对象**
- 中括号保存**数组**

## JSON值的类型
- number（整数或浮点数）
- boolean
- string
- null
- 数组
- 对象

## JSON的结构
#### 对象
在js中表示为“{}”括起来的内容，数据结构为 {key：value, key：value,...}的键值对的结构；
在面向对象的语言中，key为对象的属性，value为对应的属性值，取值方法为 对象.key 获取属性值；
键名可以用整数和字符串来表示，值的类型可以是任意类型；

#### 数组
数组在js中是中括号“[]”括起来的内容，数据结构为 ["java","javascript","vb",...]；
取值方式和所有语言中一样，使用索引获取；


## JSON的其他信息

- 最初的命名为JSML（JavaScript Markup Language），但是缩写被JaveSpeech的标记语言先用了，所以才使用 JaveScript Object Notation 命名；
- 曾被指责“JSON只是重新发明 XML”，对此， Douglas Crockford的回应是：“重造轮子的好处是可以得到一个更好的轮子”；
- 刚开始JSON信息与JS解析器是有冲突的，因为JSON有可能会使用了一些JS的关键字，为此，所有的JSON键名都被加上了引号；
- 目前JSON 是应用程序在网络之间通信的首选协议格式；



对JSON起源有兴趣的可以查看：[JSON 的兴起与崛起](https://linux.cn/article-10440-1.html)
JSON的官方说明：[JSON: The Fat-Free Alternative to XML](http://www.json.org/xml.html)