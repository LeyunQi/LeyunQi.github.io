---
layout: post
title:  "Java Socket 编程"
categories: language
tags:  socket 
author: Leyun Qi
---

##  Java Socket 编程
1. OSI七层模型  
应用层、表示层、会话层、传输层、网络层、数据链路层、物理层
2. TCP/IP 四层模型  
应用层 传输层 网际层 主机至网络层  

###  TCP和UDP
**UDP**
   
* 将数据及源和目的封装在数据包中，不需要建立连接  
* 每个数据报的大小限制在64k内 
* 因无连接，是不可靠协议  
* 不需要建立连接，速度快  

**TCP**

* 建立连接，形成传输数据的通道  
* 在连接中进行大数据量传输  
* 通过三次握手完成连接，是可靠协议  
* 必须建立连接，效率会稍低 