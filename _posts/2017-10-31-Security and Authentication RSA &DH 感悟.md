---
layout: post
title:  "Security and Authentication RSA & Diffie‐Hellman 感悟"
categories: language
tags:  RSA DH key transmission/exchange
author: Leyun Qi
---

###  Security and Authentication RSA & Diffie‐Hellman 感悟 

1. 密钥协商(key establishment)包括“密钥传输”(key transmission)和“密钥交换”(key exchange)。  
	
	* RSA起的作用是Key Transmission，也就是说，用于产生Session Key的“种子”是由客户端决定，用服务器的公钥加密并再次传输到服务器端。  
	* DH起的作用是key exchange，也就是说，用于产生session key的“种子”，是客户端和服务器都参与了的。  
	* RSA是用来加密解密的，DH是用来协商创造密钥的。  
	* 使用RSA进行信息传输是非对称密码体系，使用DH进行密钥交换的下一步使用的一般是对称的密码体系。  
	* **Diffie-Hellman是一种建立密钥的方法，而不是加密方法**
	
2. **模拟用RSA做秘钥交换(key exchange)情况**  
A想和B进行密钥交换，获得一个新的密钥，于是A就通过B的公钥加密了一个密钥K（此处的密钥相当于原文），然后将生成的密文发给B。B接到了这个密文之后使用自己的私钥解密获得密钥K。于是双方就可以愉快的使用这个K来进行后面的加密了~这就是最简单的RSA密钥交换模型了。实际上考虑到前面提到的中间人攻击的问题，因此A往往需要同时加上自己的身份认证信息(A的私钥)。 同时有些复杂点儿的情况下可能还需要B通过A的公钥发送一系列的确认信息。  
引用自知乎，武杰，https://www.zhihu.com/question/25116415/answer/30135284  

3. **Diffie‐Hellman algorithm**  

* 第一步：  设定一质数q, 原始根α，有α<q。  

![](http://oyoz58yqn.bkt.clouddn.com/image/jpg/WX20171031-201031@2x.png)

* 第二步：  A私钥 Xa < q, A公钥 Ya = α^Xa mod q. B同理
	
![](http://oyoz58yqn.bkt.clouddn.com/image/jpg/WX20171031-201116@2x.png)

* 第三步：	 A通过生成的私钥Xa计算出公钥Ya,并发给B。B同理将生成的私钥Xb计算成公钥Yb发送给A。

![](http://oyoz58yqn.bkt.clouddn.com/WX20171031-224702@2x.png)

* 实例：  

![](http://oyoz58yqn.bkt.clouddn.com/WX20171031-224755@2x.png)
  
 可以发现共有的key都为160是相等的，即：
 ![](http://oyoz58yqn.bkt.clouddn.com/WX20171031-232723@2x.png)  
 因此相当于双方已经交换了一个相同的秘密密钥.  
 因为XA和XB是保密的，一个敌对方可以利用的参数只有q,a,YA和YB.因而敌对方被迫取离散对数来确定密钥.例如，要获取用户B的秘密密钥，敌对方必须先计算 XB = inda,q(YB) 然后再使用用户B采用的同样方法计算其秘密密钥K. Diffie-Hellman密钥交换算法的安全性依赖于这样一个事实：虽然计算以一个素数为模的指数相对容易，但计算离散对数却很困难.对于大的素数，计算出离散对数几乎是不可能的.（通过例子也能看出）     
 **那么问题来了，当出现Man-in-the-middle-attack的时候怎么办？**
 一开始我看到中间人攻击的过程也觉得很懵，Information system management只是讲了大致过程和结果，却没有讲具体方式。后来我整理了一下~大致就是这样。与之前不同的是，Eve选取了两个随机数作为private key，从而生成两个public key分别交与Alice and Bob并与之作key exchange。通过例子可以发现中间人攻击并没有办法预防，因此在实际应用中往往采用多种Authentication的方式如：Digital certificate。
 ![](http://oyoz58yqn.bkt.clouddn.com/WX20171101-164853@2x.png)
 