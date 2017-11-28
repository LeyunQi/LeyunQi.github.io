---
layout: post
title:  "Security and Authentication Week2 Q&A"
categories: security&&authentication 
tags:  security
author: Leyun Qi
---
##  Security and Authentication Week2 Q&A

#### What is the difference between the public and private keys?
* A user's private key is kept private and known only to the user. The private key can be used to encrypt a signature that can be verified by anyone with the public key.
* The user's public key is made available to others to use. The public key can be used to encrypt information that can only be decrypted by the possessor of the private key.

#### If 20 people want to communicate using conventional encryption, how many keys are needed? And if they want to use public-key encryption, how many keys are needed?
* For conventional encryption: 20 * 19/2 or (N * (N-1)/2) [190 keys]
* For public key encryption:40 keys(or a 20 pairs of keys per individual).

#### Briefly describe the Diffie-Hellman key exchange.
* Two parties each create a public-key, private-key pair and communicate the public key to the other party.
* The keys are designed in such a way that both sides can calculate the same unique secret based on each side's private key and the other side's public key.

* #### User A and B use the Diffie-Hellman key exchange technique with a common prime q = 31 and a primitive root α = 3
* #### If user A has private key XA = 4, what is A's public key YA?
* #### If user B has private key XB = 2, what is B's public key YB?
* #### What is the shared secret key B?
Ya = 81 mod q = 19
Yb = 9
19^2 mod q = 20
9^4 mod q = 20

#### List the principle elements of a public-key encryption. Briefly explain each of them.
* _Plaintext:_ Unencrypted text/data that is fed into the algorithm as input.
* _Encryption Algorithm:_ Performs various transformations on the plaintext.
* _Public and private keys:_ A pair of keys on the client and server sides, if one is used for encryption, the other is used for decryption.
* _Ciphertext:_ Encrypted version of the plaintext and the key.
* _Decryption algorithm:_ Accepts the ciphertext and the matching key and produces the original plaintext.

#### What are three broad categories of applications of public-key cryptosystems?
* _Encryption/decryption:_ The sender encrypts a message with the recipient's public key.
* _Digital signature:_ The sender "signs" a message with its private key. Signing is achieved by a cryptographic algorithm applied to the message or to a small block of data that is a function of the message.
* _Key exchange:_ Two sides cooperate to exchange a session key.E.g. Diffie-hellman key exchange

#### What is the RSA? What are it's uses?
**Block cipher in which the plaintext and ciphertext are integers between 0 and n-1.**  
	n = p * q where p and q are prime numbers
	Encryption：c = m^e mod(n)
	Decryption: m = c^d mod(n）
				where Public-key k_u = (e,n) and Private--key k_r = (d,n)  
	It can be used for:  
			Confidential communications.  
			Signed electronic documents(signature).

#### What do we mean by one-way hash function?  
A hash is one way cryptographic function and the sender and receiver do not need to share a secret key. A hash function takes a message of a variable length and produces a unique 'fingerprint' of the message.

#### What is the difference between a message authentication code and a one-way hash function?
* The difference between a MAC and a Hash is that the sender and receiver of a MAC need to share a secret key.  
* A hash is a one way cryptographic function and the sender and receiver do not need to share a secret key.  

#### What changes are required to replace a HMAC with an underlying hash function?
* To replace a given hash function in an HMAC implementation, all that is required is to remove the existing hash function module and drop in the new  module.

#### Perform Encryption and Decryption using the RSA algorithm for the following:  
p = 3, q = 11, e = 7, M = 5  
p = 5, q = 11, e = 3, M = 9  
p = 7, q = 11, e = 17, M = 8  
Calculate d and ciphertext C  

Solution key:  
d = 3,C = 14  
d = 27, C = 14  
d = 53, C = 57  

* #### User A and B use the Diffie-Hellman key exchange technique with a common prime q = 71 and a primitive root α = 7
* #### If user A has private key XA = 5, what is A's public key YA?
* #### If user B has private key XB = 12, what is B's public key YB?  
* #### What is the shared secret key B?  

Solution key:  
YA = 51
YB = 4  
Shared key B = 30