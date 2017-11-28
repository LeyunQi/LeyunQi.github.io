---
layout: post
title:  "Security and Authentication Week3 Q&A"
categories: security&&authentication 
tags:  security
author: Leyun Qi
---

* content
{:toc}


<h3>1)What is a replay attcak</h3>

<ul>
	<li>It is when an attacker obtains a copy of an authenticated packet and later transmits it to the intended target.</li>
	<li>The reception of the duplicate, authenticated IP packets may disrupt the service in some way or may lead to some other undersired consequence.</li>
</ul>

<h3>2) What is Kerberos? What does it provide?</h3>
<ul>
	<li>Keberos is a centralised authentication services designed for use in a distributed enviroment.</li>
	<li>it makes use of a trusted third-party authentication service that enables clients and servers to establish authenticated commnication. Also, it provides access control.</li>
</ul>

<h3>3)A simple way for a server to authenticate a client is to ask for a password. In Keberos this authentication is notused, why? How does Keberos authenticate the server and the clients?</h3>
<ul>
	<li>The main security weakness is that the password is transmitted. So anybody eavsdropping can get hold of it.</li>
	<li>A better way is: the client request from the server a "service granting ticket". The client sends the request for using the server, and the user's ID. The server, which knows the users password, creates a session key using the user's password.Using this session key, the server sends the ticket granting a service. The client asks the user for his/her password, generates the session key and recovers the ticket. The password is never transmitted between server-client.</li>
</ul>

<h3>4)What the four requirements are for Kerberos? What mechanisms are used within Kerberos systems to archieve those requirements?
</h3>


<table>
	<style>
		html,body{font-family:Arial, Helvetica, sans-serif; font-size:18px} 
		.tablelist{
			border: 2px solid;
			border-collapse: collapse;
		} 
		.tablelist{
			border:1px solid;
			width:100px;
			text-align:center;
			font-size:12px;
		}
		.odd{
		background-color:#efc3e6
		}
		.even{
		background-color:#9c89b8
		}
	</style>
	<caption>Requirements and Mechanism of Keberos</caption>
		<thead>  
		   <tr class="even">  
		   		<th width="100" onclick="kw.tabSort('tab',0)">Requirement</th>  
		   		<th width="100" onclick="kw.tabSort('tab',1)">Mechanism</th>   
		   </tr>   
	   </thead>  
		<tbody>
			<tr style="background-color:#f0e6ef">
				<th>Secure</th>
				<td>
					Provide by the secure steps, mostly achieved by using 					<ins>conventional encryption</ins>.AUTHENTICATION is an 					alternative answer.
				</td>
			</tr>
			<tr style="background-color:#efc3e6">
				<th>Reliable</th>
				<td>
					Distributed architecture. Uses
					<ins>mirrored system backups<ins>.
				</td>
			</tr>
			<tr style="background-color:#f0e6ef">
				<th>Transparent</th>
				<td>Limitation of user interaction to the authentication with the 					client(password or other methods).
				</td>
			</tr>
			<tr style="background-color:#efc3e6">
				<th>
					Scalable
				</th>
				<td>
					Principle of Kerberos realms.
				</td>
			</tr>
		</tbody>		
</table>	

<h3>5) What is a public-key certificate?</h3>
It is used to authenticate public-keys of users.<br>
A public-key certificate contains a public key, an identifier of the key owner and other information, is signed and acreated by a certificate authority, and is given to the participant. A participant conveys its key information to snother by transmitting its certificate. Other participants can verify that the certificate was created by the authority.
<h3>6) Define the X.509 standard. How is an X.509 certificate revoked?</h3>
<ul>
	<li>
	X.509 defines a framework for the provision of authentication services by the X.500 directory to its users.
	</li>
	<li>
	The directory may serve as a repository of public-key certificates
	</li>
	<li>
	The public key of a user and is signed with the private-key of a trusted certification authority.
	</li>
	<li>
	In addition, X.509 defines alternative authentication protocols based on the use of public-key certificates.
	</li>
	<li>
	Each CA must maintain a certificate revocation list(CRL) consisting of all revoked of all certificates issued by that CA.
	</li>
	<li>
	The list is signed by the issuer and includes the issuer's name, the date the list was created, the date the next CRL is scheduled to be issued, and an entry for each revoked certificate. Each entry consists of the serial number of a certificate and revocation date for that certificate.
	</li>
	<li>
	The user could check the CRL list each time a certificate is received to determine the certificate is not revoked.
	</li>
</ul>

<h3>7) What is IPsec? Why is significant?</h3>
<ul>
	<li>
	IPSec stands for IPSecurity as it protects IP packets
	</li>
	<li>
	It is vital for providing additional security at the IP layer, and protect
	</li>
	<li>
	It provides:confidentiality, authentication, or both for IP packets.
	</li>
</ul>

<h3>8)What are the two modes of operations in IPSec? How can they achieve protection against traffic analysis?</h3>
<ul>
	<li>
	<ins>Tunnel Mode</ins>: protects entire packet.
	</li>
	<li>
	<ins>Transporgt Mode</ins>:protects payload.
	</li><br>
<ins>ESP provides protection against traffic analysis<br>
	<strong>In <ins>tunnel mode</ins> ESP provides protection against traffic analysis where the <ins>host on the internet networks use the Internet transport of data but do not interact with other Internet-based hosts.</ins></strong><br>
	<strong>In Transport Mode, ESP only protects the payload, hence the IP header will not be hidden.</strong>
</ins>
</ul>
<h3>9)List the Services provided by IPSec</h3>
<ul>
	<li>
	Access control
	</li>
	Connectionless intergrity
	<li>
	Data origin authentication
	</li>
	<li>
	Rejection of replayed packets
	</li>
	<li>
	Confidentiality(encryption)
	</li>
	<li>
	Limited traffic flow confidentiality
	</li>
	</ul>

<h3>10)In IPSec, what is the domain of interpretation(DOI)?</h3>
<ul>
	<li>
	Contains values to relate the different specifications of the protocol;
	</li>
	<li>
	Identifiers for encryption and authentication algorithms
	</li>
	<li>
	and operational parameters, key lifetimes, key exchange etc.
	</li>
</ul>
<h3>11)In IPSec, what is the difference between transport mode and tunnel mode?</h3>
<ul>
	<li>
	Transport mode provides protection primarily for upper-layer3 protocols. That is, transport mode protection extends to the payload of an IP packet
	</li>
	<li>
	Tunnel mode provides protection to the entire IP packet.
	</li>
</ul>
<h3>12)What are the parameters used to charactise the nature of a particular SA?</h3>
<ul>
	<li>
	Sequence Number Counter
	</li>
	Sequence Counter Overflow
	<li>
	Anti-Replay Window
	</li>
	<li>
	AH Information
	</li>
	<li>
	ESP Information
	</li>
	<li>
	Lifetime of this Security Association
	</li>
	<li>
	IPSec Protocol Mode
	</li>
	<li>
	Path MTU
	</li>
</ul>
<h3>13)What are the roles of the Oal;ey key determination protocol and ISAKMP in IPSec?</h3>
ISAKMP by itself does not dictate a specific key exchange algorithm; rather, ISAKMP CONSISTS OF A SET of message types that enable the use of key exchange algorithms.Oakley is the specific key exchange algorithm mandated for use with the initial version of ISAKMP.


