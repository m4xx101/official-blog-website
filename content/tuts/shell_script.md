+++
title = "Shell Script Tutorial"
date = "2019-01-31"
author = ".!"
cover = "shell_post.png"
description = "Tut 1"
+++

# Shell Scripting

## File Encryption & Decryption Program

### This is simple program made by me for encrypting & decrypting the files

This is a quick tutorial on shell scripting so won't go in deep about every concepts but the over view and little bit of explaination.

#### Let's get started.!

Alright the first line in the Shell script is called **sha-bang** that is nothing but

>**#!**

anyway we aren't here to discuss about sha-band lol.!

I'm putting wiki link so you can read  about it in detail.

<a href="https://en.wikipedia.org/wiki/Shebang_(Unix)#Purpose" target="_blank">*I'm the wiki link he was talking about*</a>

File extension of Shell scripts are

>**.sh**

Now going furthur,

Just about every programming language in existence has the concept of variables - a symbolic name for a chunk of memory to which we can assign values, read and manipulate its contents.

Almost in every programming language variables are declared as

>VAR_NAME = "Here comes value of the variable"

Also in shell script we declare variables Like that.

Now secondly,

>"echo" (without quotes) is use for printing output to the screen short of a "print" command like any other programming language.

To take input from user we use *"read"* command in shell scripting,

>read VAR_NAME

Now after taking input if we want to access the value of that variable which was given by user, we use "$" (Dollar Sign befor the Variable name) i.e,

>$VAR_NAME  - Like this

Now if we want to print the value which user had given we'll use

>echo $VAR_NAME

and we all know about if else condition, aren't we.?
if NO here is sample program for if else condition

```sh
if [ expression ]
then
   Statement(s) to be executed if expression is true
else
   Statement(s) to be executed if expression is not true
fi
```

#### Little bit about Cryptography

We are going to use GPG (GNU Privacy Guard) which is free encryption software that's compliant with the OpenPGP (RFC4880) standard. Using GPG you can encrypt (and decrypt) files that contain sensitive data, such as protected health information (PHI) regulated by the Health Insurance Portability and Accountability Act (HIPAA) privacy and security rules. For more on GPG, see the GNU Privacy Guard website. 

For more visit this link

<a href="https://kb.iu.edu/d/awio" target="_blank">GPG</a>


### Now putting this all together we can create following program :




```sh
#!/bin/bash

echo "
 _____ _ _        _____                             _            
|  ___(_) | ___  | ____|_ __   ___ _ __ _   _ _ __ | |_ ___ _ __ 
| |_  | | |/ _ \ |  _| | '_ \ / __| '__| | | | '_ \| __/ _ \ '__|
|  _| | | |  __/ | |___| | | | (__| |  | |_| | |_) | ||  __/ |   
|_|   |_|_|\___| |_____|_| |_|\___|_|   \__, | .__/ \__\___|_|   
                                        |___/|_|               
By:m4xX.!
"
echo "version 1.2.0 by m4xX"

function list_dir_enc(){


	if [[ $file_encrypt = "ls" ]]; then
		ls -la --color
		echo ""
		Encrypt_file
		echo ""
	elif [[ $file_encrypt = "exit" ]]; then
			exit
	
	fi
}

function list_dir_dec(){


	if [[ $file_decrypt = "ls" ]]; then
		ls -la --color
		echo ""
		Decrypt_file
		echo ""
	elif [[ $file_decrypt = "exit" ]]; then
			exit
	
	fi
}
function Encrypt_file(){

	echo ""
	echo "Enter File Name to Encrypt: "
	read  file_encrypt;
	list_dir_enc
	#cp $file_encrypt /root/Desktop/backup_$file_encrypt
	gpg -c $file_encrypt
	echo "Done.!"
	rm -r $file_encrypt
	exit
}
function Decrypt_file(){
	echo ""
	echo "Enter File Name to Decrypt: "
	read file_decrypt;
	list_dir_dec
	gpg $file_decrypt
	#cp /root/Desktop/backup_$file_encrypt ./$file_encrypt
	echo "Done.!"
	rm -r $file_decrypt
	exit
}
choose="Encrypt Decrypt"

select opt in $choose;
do
	if [[ $REPLY = 1 || $REPLY = "Encrypt" || $REPLY = "encrypt" || $REPLY = "ENCRYPT" ]]; then
		Encrypt_file
		
	elif [[ $REPLY = 2 || $REPLY = "Decrypt" || $REPLY = "decrypt" || $REPLY = "DECRYPT" ]]; then
		
		Decrypt_file

	else
		echo "Invalid Input.!"
		
	fi
done

```


>Github Link for following program is given below

[Link](https://github.com/m4xx101/Shell-Script)

*Note:- if you're using this website at night or in dark room there's one toggle on the top right-hand side for dark mode.!


Happy Hacking :)

This is m4xX.!


