---
layout: post
title:  "PHP源码分析：HashTable"
date:  "2017-03-16 13:18:40 -0700"
category: PHP
tags: tools
keywords: PHP
description: ""
---  

我们知道PHP是一种弱类型语言，相对于C、Java等语言来说，弱类型语言的变量能够接收各种类型的值，例如：  
``` php  
	$var = 10;
	$var = 'this is a string';
	$var = array('score' => 100);
	$var = new MyClass();
```  
从上面可以看出变量`$var`能接整型、字符串、数组、对象等多种类型的值，非常灵活。
但是PHP是用C来实现的，C语言是强类型的语言，PHP底层是如何实现的呢？  


在`Zend/zend.h`文件中，变量实际保存在`zvalue_value`结构中：  
``` c  
	typedef union _zvalue_value {
		long lval;                                      /* long value */
		double dval;                            /* double value */
		struct {
			char *val;
			int len;
		} str;
		HashTable *ht;                          /* hash table value */
		zend_object_value obj;  
	} zvalue_value;
```  
首先`zvalue_value`是一个union的结构。相对于struct，union能够节省更多的内存空间，降低PHP的内存占用。另外，从结构中可以看到：`lval`用来保存整数值，`dval`用来保存浮点数值，`str`用来指向字符串的位置并记录长度。