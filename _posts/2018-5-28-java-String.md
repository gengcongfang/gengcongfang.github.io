---
layout: post
title: Java中String类的方法和相关说明
date: 2018-05-28
tags: Java
---

## 一、构造函数

```java
String( byte[]  bytes );	//通过byte数组构造
String( char[]  value ); //通过char数组构造
String( String  original );	//拷贝一个original
String( StringBuffer  buffer );	//通过StringBuffer数组构造
```

​	其中通过byte和char数组来构造的函数可以加上两个参数，以

```java
String(byte[] bytes,int index,int length);
```

​	index为开始下标，length是从下标处往后的长度，从而截取部分字符串构造。

## 二、方法

```java
int length();	//返回字符串长度

char charAt(int index);		//返回下标为index的字符

int compareTo(String str);		//与str对象进行比较，相等返回0

int compareTo(Object o);		//若o为String对象，则与上条相同功能，否则抛出异常ClassCastException

boolean startsWith(String prefix);	//若以prefix为开头，返回true，否则返回false

boolean endsWith(String suffix);	//若以suffix为结尾，返回true，否则返回false

byte[] getBytes();	//返回对象对应的byte数组

int indexOf(char ch);	//返回第一个ch字符的下标

int indexOf(char ch,int fromIndex);	//从下标fromIndex开始，返回第一个ch字符的下标

int indexOf(String str);

int indexOf(String str,int fromIndex);	//同char
//与indexof有相似功能的有lastIndexOf，不同的是返回最后一个ch字符的下标

static String valueOf(Object o);	//返回该对象的字符类型对象

boolean equalsIgnoreCase(String str);	//忽略大小写判断字符串是否相等

String toUpperCase();	//返回大写字符串

String toLowerCase();	//返回小写字符串

String subString(int beginIndex);	//从下标beginIndex开始，截取字符串

String subString(int beginIndex,int endIndex);	//截取下标beginIndex到endIndex的字符串

String trim();	//去掉开头和结尾的空格字符

String split(String regex);	//按照regex为分隔符进行分隔，返回分隔后的String数组

String replace(char oldCh,char newCh);	//用newCh代替oldCh

String replace(String oldStr,String newStr);	//同上

String replaceAll(String regex,String replacement);	//正则匹配后替换
```

