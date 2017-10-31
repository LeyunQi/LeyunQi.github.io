---
layout: post
title:  "Security and authentication week1 Q&A"
categories: language
tags:  RSA DH key transmission/exchange
author: Leyun Qi
---

###Security and Authentication RSA & Diffie‐Hellman 感悟

1. 密钥协商(key establishment)包括“密钥传输”(key transmission)和“密钥交换”(key exchange)。  
	
	* RSA起的作用是Key Transmission，也就是说，用于产生Session Key的“种子”是由客户端决定，用服务器的公钥加密并再次传输到服务器端。  
	* DH起的作用是key exchange，也就是说，用于产生session key的“种子”，是客户端和服务器都参与了的。  
	* RSA是用来加密解密的，DH是用来协商创造密钥的。  
	* 使用RSA进行信息传输是非对称密码体系，使用DH进行密钥交换的下一步使用的一般是对称的密码体系。  
	
2. **模拟用RSA做秘钥交换(key exchange)情况**  
A想和B进行密钥交换，获得一个新的密钥，于是A就通过B的公钥加密了一个密钥K（此处的密钥相当于原文），然后将生成的密文发给B。B接到了这个密文之后使用自己的私钥解密获得密钥K。于是双方就可以愉快的使用这个K来进行后面的加密了~这就是最简单的RSA密钥交换模型了。实际上考虑到前面提到的中间人攻击的问题，因此A往往需要同时加上自己的身份认证信息(A的私钥)。 同时有些复杂点儿的情况下可能还需要B通过A的公钥发送一系列的确认信息。  
引用自知乎，武杰，[](https://www.zhihu.com/question/25116415/answer/30135284)  

3. { Y }_{ A }\quad =\quad { \alpha  }^{ { X }_{ A } }\quad mod\quad q



