---
layout: post
title:  "Security and authentication week1 Q&A"
categories: language
tags:  code
author: Leyun Qi
---

* content
{:toc}

### 
##Security and Authentication
###Week 1 Tutorial Q&A
**1.Briefly explain the security services of confidentiality, integrity and availability.** (P19˜20)
	
**Solution key:**

**Confidentiality:** perserving authorised restrictions on information access and disclosure, including means for protecting personal privacy and proprietary information.

**Integrity:** guarding against improper information modification or destruction. A loss of integrity is the unauthorised modification or destruction of information. 

**Availability:** Ensuring timely and reliable access to and use of information. A loss of availability is the disruption of access to or use of information or an information system.
****
**2. Consider a student attendance information system in which the students provide a password for accessing their accounts. Give examples of the security services thr system should provide in terms of confidentiality, integrity, access control and availibility.**

**Solution key:**
  
  The system must keep all passwords and account information confidential, both in the server and during the transaction.   
  It must protect the integrity of data records from unauthorised changes. 
  It must also limit access of various levels of data to the right users only; e.g. students can only access their own information, and instructors can access all students attendance records.  
  Availability of the server during the college working hours is important, and needs to withstand DoS attacks.
****
**3. Why is Caesar cipher subsititution technique vulnerable to a brute force cryptanalysis?**

**Solution key:**  
There are only 25 possible keys to try-very easy.
****
**4. Why is one-time pad scheme unbreakable theoretically? What are the practical problems of one-time pad?**

**Solution key:**  
Given a certain ciphertext, there are keys that produces different plaintext. If you did an exhaustive search of all possible keys, you would end up with many legible plaintexts, with no way of knowing which was the intended plaintext. The ciphertext contains no information whatsoever about the plaintext, there is simply no way to break the code.  
Practical problems of one-time pad are:  
1. the difficulty in generating truly random keys.  
2. how to transmit and protect the random key.
****
**5. Construct a Playfair matrix with the key reason. Make a reasonable assumption about how to treat redundant letters in the key. Encrypt the message: See some light in the darkness.**. 

**Solution key:**  
Matrix:  

| R | E | A | S | O |
|---|---|---|---|---|
| N | B | C | D | F |
| G | H |I/J| K | L |
| M | P | Q | T | U |
| V | W | X | Y | Z |

SE ES OM EL IG HT IN TH ED AR KN ES SX   
Cipher text: OA AO RU OH KH KP GC PK SB SE GD AO AY
****
 **6. Using Vigenere Cipher, encrypt the word "examination" using the key grades.**
 ![](file:///Users/leyunqi/Desktop/vigenere.png)
 **Solution key:** 
 
	 key:         g r a d e s g r a d e   
	 plaintext:   e x a m i n a t i o n
	 ciphertext:  KOAPMFGKIRR
****
**7. Define the term "block cipher" and "stream cipher"**

**Solution key:** 

Stream Cipher is an cryptographic method that processes one input element at a time.  
Block Cipher is a cryptographic method that processes a block of elements at a time.

****
**8. Briefly define the terms substitution and permutation.**

**Solution key:**   
In substitution, each plaintext element or group of elements is uniquely replaced by a corresponding ciphertext element or group of elements.  
In permutation, a sequence of plaintext elements is replaced by a permutation of that sequence. That is, no elements are added or deleted or replaced in the sequence, rather the order in which the elements appear in the sequence is changed.
****
**9. What is the purpose of the key expansion algorithm used in AES?**

**Solution key:**   
The AES key is 4 words(128 bits), which is used for round 0. For round 1 - 10, the key expansion algorithm provides a new 4-word round key for each of the 10 rounds.
****
**10. A typical round of AES encryption consists of four stages(Substitution bytes, Shift Rows, Mix Columns and Add Round Key). Describe the functionality of each stage.**  

**Solution key:**  
_Substitute Bytes:_ Uses an S-box to perform block subsstution. Each of the 'state' bytes is split into two 4-bit values; these represent the column and row values of the S-box containing the new substitution value. 
_Shift Rows:_ A simple permutation where the 'state' block is altered by re-arranging the bytes located on each of the four rows.
_Mix Columns_: A substitution that makes used of arithmetic over GF(2ˆ8).
Hence, each of the 'state' elements is updated using the product of elements of one row  and one column.
_Add Round Key_: A simple bitwise XOR of the current block with a portion of the expanded key. The expanded key is obtained through the 'expansion algorithm'.
****

