---
aliases: []
tags: []
publish: "true"
---

# C语言
## 基础知识
C语言开发于20世纪70年代初，是一种编译语言，是许多其他语言的基础。

## 优点
C语言是一种高效且广泛使用的编程语言。业界估计，80%的嵌入式系统使用C语言编程。

## 缺点
要求开发人员理解并使用可能很复杂的编码技术。

## 注释
注释是给人类阅读的。编译器会忽略它们。在C语言中，有两种添加注释的方法。
```
一种是将注释放在标记/*...*/之间
另一种是将//放在语句前
或者用快捷键 ctrl+/ 注释
```

## 数据类型
![[C语言数据类型.png]]
![[C语言数据类型1.png]]
![[C语言数据类型2.png]]

## 操作符
操作符是一个符号，它告诉编译器执行特定的数学或逻辑功能。
![[C语言操作符.png]]
![[C语言数学运算符.png]]
![[C语言关系运算符.png]]
![[C语言逻辑运算符.png]]

## 条件声明
### 循环语句
![[C语言条件声明.png]]
#### while

	while (loop repetition condition){
		statement
		}

#### for
	for (initialization expression; loop repetition condition; update expression){
		statement
		}

#### do while
	do
		statement
	while (loop repetition condition);

### if语句
	if(expression)
		statement 1
	else
		statement 2

^a38b9d

### switch语句
	switch(i)
	{
		case 0: display = 1; break; 
		case 1: display = 2; break; 
	}

## 函数
	return_type function_name( parameter list ) 
	{ 
		body of the function 
	}