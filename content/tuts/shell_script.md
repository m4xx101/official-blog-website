+++
title = "Shell Script Tutorials"
date = "2019-01-31"
author = "m4xx.!"
cover = "shell_post.png"
description = "Tut 1"
+++

## Shell Scripting - For Beginners

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
This is simple file encryption program made by me.

>Github Link for following program is given below

[Link](https://github.com/m4xx101/Shell-Script)