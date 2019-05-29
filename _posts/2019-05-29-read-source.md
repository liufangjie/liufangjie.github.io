---
layout: post
title: 读源码
---
{{ page.title }}
=============

# Java读取Property文件的默认行为，Stream和Reader的不同

版本1.7
 
源码地址：[Properties.java](https://github.com/openjdk-mirror/jdk7u-jdk/blob/master/src/share/classes/java/util/Properties.java)

参照[Line 69](https://github.com/openjdk-mirror/jdk7u-jdk/blob/f4d80957e89a19a29bb9f9807d2a28351ed7f7df/src/share/classes/java/util/Properties.java#L69)

说明通过load(inputStream)的方式加载Property文件的时候默认使用的是`ISO 8859-1`编码格式。

另外这里也提现了Stream和Reader之间的一个不同，Reader可以指定编码格式，但是Stream无法指定。

从扩展的角度考虑在设计实现PropertyUtil(用于加在Property文件的工具类)时，可以采用load(reader,charset)的方式，并设置一个默认的编码方式，这样调用方也可

以根据自己的需求指定特定的编码格式。

可以参照[JFianl PropKit](https://github.com/jfinal/jfinal/blob/master/src/main/java/com/jfinal/kit/PropKit.java)的实现。
