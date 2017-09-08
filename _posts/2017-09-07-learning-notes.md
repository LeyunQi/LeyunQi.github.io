---
layout: post
title:  "Java语言基础"
categories: language
tags:  java
author: Leyun Qi
---

* content
{:toc}

# Java语言基础
## 2.1 关键字**
- 用于定义访问权限修饰符的关键字
	
		private protected public
- 用于定义类、函数、变量修饰符的关键字

		abstract final static sychronized
- 用于定义类与类之间关系的关键字

		extends implements
- 0开头表示八进制
- 0x开头表示十六进制
- 0b开头表示二进制
- 1 byte字节 = 8 bits二进制位
- 负数的反码符号位不变, 其余位取反
- 变量是内存中的一片区域

**为什么要定义变量**
	
	用来不断的存放同一类型的常量，并可以重复使用
数据类型：
数据类型 变量名 = 初始化值；

	byte short(2 bytes) int(4 bytes) long(8 bytes)
	float(4 bytes) 有效数字8位
	double(8 bytes) 有效数字16位

s+=4和s=s+4的区别：s+=4底层做强转，后者不做强转（overflow)
改成s=(short)(s+4)

^:异或
	
	true^true=false;
	true^false=true;
	false^true=true;
	false^false=false;
- 一个数异或同一个数两次，结果还是这个数
		
	eg.6^3^3=6

**>> <<移位**
最高位是几就补几
	
	2*8=2*2(3)=2<<3

####三元运算符
格式:

- (条件表达式）？表达式1：表达式2
	- 如果条件为True,运算后的结果是表达式1；
	- 如果条件为False,运算后的结果是表达式2；
	eg.int x=3,y=4,z;
	   z=(x>y)?x:y;//z变量存储的就是两个数的大数

####if语句三种格式：
	1. if(条件表达式（判断结构）
	   {
			执行语句;
	   }

	2.if(条件表达式)
	  {
			执行语句;
	  }
      else
	  {
			执行语句;
	  }
	3.if(条件表达式）//设置多条件判断
	  {
			执行语句;
	  }
	  else if
	  {
			执行语句;
	  }
		...
	  else
	  {
			执行语句;
	  }
三元运算符就是if else语句的简化形式
简写格式什么时候用？
当if...else运算后有一个具体的结果时，可以简化成三元运算符

	if(false);
	{ //局部代码块（定义在main函数里）
	System.out,println("Hello world!");
	}
	结果会输出Hello world(if语句没有控制体，所以直接跳过if条件表达式，执行下面的代码块)

	凡是写在主函数里的变量全部是局部变量。
	...
		{//局部代码块可以定义局部变量的生命周期
			int m=89;
			System.out.println("Hello world!"+m);
		}//到这里m在内存中被释放
		System.out.println("m="+m);
	...
	}
执行结果为编译失败，找不到m变量，原因：m在局部代码块中为局部变量，作用域为局部代码块，因此外部访问不到m变量。
局部代码块用于性能优化，释放内存。

###选择结构 Switch
格式：
	
	switch(表达式)
	{
		case 取值1:  //备选答案
			执行语句;
			break;  //如果选择这个答案，跳出循环
		case 取值2:
			执行语句;
			break;
		...
		default:	//每一个选择都不对，请选择其他
			执行语句；
			break;
	}
	
if和switch的应用：
if:
1. 对具体的值进行判断
2. 对区间判断
3. 对运算结果是boolean类型的表达式进行判断

switch:

	1. 对具体的值进行判断
	2. 值的个数通常是固定的
对于几个固定的值判断，建议使用switch进行判断，因为switch语句会将具体的答案都加载进内存，效率相对高一点。

### 循环结构
代表语句：while,do while, for

	while(条件表达式)
	{
		执行语句；
	}

	do
	{
		执行语句；
	}while(条件表达式）

**do while特点：无论条件是否满足，循环体至少执行一次**

	for(初始化表达式;循环条件表达式；循环后的操作表达式)
	{
		执行语句语句; (循环体)
	}
**while和for可以互换，区别在于for为了循环而定义的变量可以在循环结束后在内存中释放，而while循环使用的变量在循环结束后还可以继续使用。**
*最简单的无限循环格式：while(True), for(;;)无限循环存在的原因是因为不知道循环多少次，而是根据某些条件来控制循环*

当对一个条件进行一次判断时，可以使用if语句；
当对一个条件进行多次判断时，可以使用while语句。

**注意：**
	在使用循环时，一定要明确哪些语句需要参与循环，哪些不需要。