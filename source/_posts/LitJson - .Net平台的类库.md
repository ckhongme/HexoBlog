---
title: LitJson - .Net平台的类库
date: 2019-11-18
tags: [JSON, C#]
categories: 标记语言
---

LitJson是Json的一个开源项目，是针对C#的相关库；在.Net平台下处理Json格式数据的类库；
Git地址： [https://github.com/LitJSON/litjson](https://github.com/LitJSON/litjson)

## 最基础的操作

将json字符串转成对象：`JsonMapper.ToObject<T>()`
将对象转成json字符串：`JsonMapper.ToJson()`


## 创建Json，和Json数组
创建Json，主要通过JsonWriter类；
```
JsonWriter jw = new JsonWriter();
jw.WriteObjectStart();
jw.WritePropertyName("user");
jw.Write("K");
jw.WritePropertyName("age");
jw.Write(20);

//复合Json
jw.WritePropertyName("city");
jw.WriteObjectStart();
jw.WritePropertyName("name");
jw.Write("深圳");
jw.WritePropertyName("info");
jw.Write("someInfo");
jw.WriteObjectEnd();

//Json数组
jw.WriteArrayEnd ();
jw.Write ("张三");
jw.Write (1);
jw.Write ("法师");
jw.Write (1.1);
jw.WriteArrayEnd ();

jw.WriteObjectEnd();

string jsonStr = jw.ToString();
Debug.Log(jsonStr);
```

## 读取多级Json数据
假设json数据的字符串是 data，它的数据结构如下：
{
    "user" : "K", 
    "age" : 20, 
    "city" : [ 
                    {"name" : "深圳", "info":[{"weather":"晴"}]} ,
                    {"name" : "广州", "info":[{"weather":"阴"}]}
                 ] 
}

读取第一级
```
    JsonData data1 = LitJson.JsonMapper.ToObject(data);
    string user = （string）data1["user"];   //K
```
读取第二级
```
JsonData data2 = data1["city"];
string cityName = data2[0]["name"];   //深圳
```
读取第三级
```
JsonData data3 = data2[0];
string weather = data3["info"][0]["weather"];   //晴
```

## 报错

在用ToObject将字符串转换为对象时，报错：
```
MissingMethodException: Method not found: 'Default constructor not found...ctor() of XXX'.
```
是因为转化为对象时找不到构造函数，无法创建实例，所以解决方案是，给要转化的类加上一个无参构造函数；