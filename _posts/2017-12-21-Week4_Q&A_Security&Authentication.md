---
layout: post
title:  "Security and Authentication Week4 Q&A"
categories: security&&authentication 
tags:  security
author: Leyun Qi
---

* content
{:toc}

### 1) Explain the protocols which are included in SSL architecture  
*	Handshake protocol
* 	Change cipher spec protocol
*  Alert protocol
*  Record protocol
 
### 2) What are the definitions of SSL connection and SSL session?   
*	A connection in SSL is a transport that provides a suitable type of service. The connections are peer-to-peer relationships and are transient. Every connection is associated with one session.  
* 	A session in SSL is an association in between a client and a server. They define  the security which can be shared between multiple connections(to avoid expansive renegotiation of security parameters).  

### 3) In security electronic transaction(SET), what sort of authentication is provided by a dual-signature? Use the credit card example to explain.
*	A dual signature is encrypted with the sender private key, so it provides authentication of the sender via a signature. A typical dual signature contatins the hash information about the merchandise, hashed. 
* 	The dual signature can be used to authenticate that the payment and information about the merchandise are concatenated . Usually this is done by sending say the payment request, the dual signature and the hash of  the merchandise.  
*  In this case the bank do not have access to the information about the goods bought however if the bank recreates the dual signature of the buyer (by hashing the payment request, concatenating it with the hash of the merchandiseand hash both again) then it can authenticate that the payment and merchandise are concatenated.  
 
### 4) Explain how dual-signature is achieved. You may want to use diagram to support your answer.      
*	Dual Signature uses the encrypted hash of both order and payment info to link the payment and order(useful if a dispute between customer -merchant occurs).  
![](http://oyoz58yqn.bkt.clouddn.com/WX20171221-235525@2x.png)

### 5) How Does PGP identify public keys?  
PGP assigns an ID to each public key by using the last 64 significant bits of the key. The ID can be used to identify which public key was used.
 
### 6) How does PGP provide authentication and confidentiality? You may want to use a diagram to illustrate it.  
See slide P59  
![](http://oyoz58yqn.bkt.clouddn.com/WX20171221-235841@2x.png)
### 7) How many encryption keys are used/generated in PGP?  
*	Pass-phrase key
* 	Session keys (random keys generated)

### 8) How do PGP manage security keys:  
* PGP uses key rings to manage keys:(first list which key to be use)
* One or more keys stored together constitute a key-ring. There are two classes:  
	*  Private-key ring: Stores the private/public key-ring owned at this node.
	*  Public-key ring: Stores the private key-ring of other users known at this node  

### 9) Name the basic requirements for email security.  
*	Confidentiality
*	Authentication
*	Integrity  

### 10) What are the differences between MIME and S/MIME?  
*	MIME is an extended framework that is intended to address some of the problems and limitations of the use of SMTP(Simple Mail Transfer Protocol) or some other mail transfer protocol and emails.  
* S/MIME is a security enhancement to the MIME Internet e-mail format standard, based on technology from RSA Data Security.

### 11) How does S/MIME process certificates?  
*	Uses public-key certificates that confirm to X.509 v3.
* 	Key management is hybrid between X.509 and PGP's web of trust. 
*  Each client has a list of trusted CA's certificates and own public/private key pairs & certificates.  
*  Certificates must be signed by trusted CA's(e.g. VeriSign)

#### 12) A hospital wants to exchange its internal information electronically. One of the problems they have is the following. Each patient has a record with their name, address and medical condition. 
#### Also in the record is the medication that the patient needs.The hospital wants the pharmacy to provide the right medication to a patient without disclosing the patient's record (only the medication that the patient needs). The pharmacy will provide the medication only if they can be assured that the medication they provide is the one that is contained in the records and matches the patient's details. Explain how would the hospital use a "dual signature" to disclose the relavant information to the pharmacy. (*You may use diagrams to explain it*)    
The hospital creates the dual signature as follows. 
  
  ![](http://oyoz58yqn.bkt.clouddn.com/WX20171222-103404@2x.png)   
  
The phamacy receives the dual signature and the medication request and the Patient record (without medication) message digest. To confirm that the medication and patient record match the pharmacy does the following:  

![](http://oyoz58yqn.bkt.clouddn.com/WX20171222-111112@2x.png)

### 13) In general, confidentiality of data transfer can be provided by using a Session Key together with Public Key of the receiver.
#### (i) Based on the above statement, explain how user A can send confidential data to user B(assuming user A has a trusted Public Key for user B).  
User A generates a random session key, uses the session key to encrypt the message(using conventional encryption), then encrypts the session key with the public key of user B. The encrypted message, with the encrypted session key, and the public key ID are then sent to user B.

#### (ii) Why is better to use conventional encryption(with the session key), and then use the public key to encrypt the session key?
- The use of 'random' session key is more secure for regular transmissions.  
- The use of conventional encryption is much faster than Public key encryption(around 1000 faster)

#### (iii) How could User B ensure that the information received is Integral and Authentic? Explain your answer.  
User A can initially hash the message, sign the hash with the sender's Private key, attach the signed hash with the original message - after that the sender can proceed with the confidentiality process explained in (i)
