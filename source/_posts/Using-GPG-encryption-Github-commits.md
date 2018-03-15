
---
title: Using GPG encryption Github commits
date: 2018-03-15  19:09:21
tags: GPG,Github
---

![gpg.png](https://i.loli.net/2018/03/15/5aaa54df96496.png)

GnuPG (abbreviated as GPG), it is one of the most popular and best open source encryption tools. GPG has many uses, such as encrypting files and messages.
And this article is about how to use GPG to encrypt Github commits. When you look at the commits of some items on Github, you occasionally find the words "this commit is signed with a verified signature.", specifically, the example below.

![gpg](https://i.loli.net/2018/03/15/5aaa551fa21fc.png)

First, install Git and Tortoisegit
For information on how to install Git and tortoisegit under Windows, refer to the "Git Beginners: Msysgit and Tortoisegit" article.
Official website:
Https://git-scm.com

https://tortoisegit.org

Ii. Generating Keys Git brings the GPG command, so you can generate the key directly in Git Bash.

The order is as follows:
`GPG--gen-key`

Enter the message as follows:

`GPG (GnuPG) 1.4.21;
Copyright (C) 2015 free Software Foundation, Inc.
This is the free software:you are and redistribute it.

There is NO WARRANTY and to the extent permitted by.
 Please select what kind of key for you want:
 (1) RSA and RSA (default)
 (2) DSA and Elgamal
 (3) DSA (sign only)
 (4) RSA (sign only)
Your selection?`

Select the encryption algorithm, by default Select the first option, which means that both encryption and signature use the RSA algorithm.

Choose 1, enter.

Select the key length, the default is 2048, and we recommend that you enter 4096.

`RSA keys may between 1024 and 4096 bits long. What keysize do you want?
(2048)`

Enter 4096, carriage return.

Sets the validity period of the key.

 `Please specify how long the key should be valid.
 0 = key does not expire
 <n>= key expires in n days
 <n>W = key expires in n weeks
 <n>m = key expires in n months
<n>y = key expires in n years Key is valid for?
(0)`

If the key is for personal use, it is recommended that you choose the first option that never expires.

Enter 0, carriage return.

The system will ask you if the above settings are correct. 

`Is this correct? (y/n)`

Enter Y, carriage return.

The system will ask you to enter your personal information. 

`You need a user ID to identify your key;
The software constructs the user ID
 From the "real" Name, Comment and Email address into this form:

 "Heinrich Heine (Der dichter) <heinrichh@duesseldorf.de>"
Real name:`

"real name" Fill in your name, it needs to be in English.

Email Address: 
`"email address" `
Fill in your email address.

Comment: 
`"comment"`
can be empty without filling. 

The system will again let you confirm the information that is filled in.
 Selected this user-id:

 `"strwei <i@xxx.com>"
Change (N) AME, (C) omment, (E) mail or (O) kay/(Q) uit? 
Enter O, carriage return.`

The system will let you set a private key password.

`You are need a passphrase to protect your secret key.
Enter Passphrase:
Repeat Passphrase: `

Note Here to leave blank, direct return. 
This is because the tortoisegit does not support 1.4.x containing the private key password. When the system starts to generate the key, you will be asked to do some random action to generate a random number.

You pick up the mouse and hang around until the key is generated. We need to generate a lot of random bytes.
It is a perform
Some other action (type on the keyboard, move the mouse, utilize the Disks) during the prime generation;
This gives the random number
Generator a better chance to gain enough entropy.

Finally, you are prompted to complete the build.
Gpg:key 0ad6c46d marked as ultimately trusted
Public and secret key created and signed.
Iii. List Key

The order is as follows:
GPG--list-keys

The output is as follows:
Gpg:checking the Trustdb
Gpg:3 marginal (s) needed, 1 complete (s) needed, PGP trust model
gpg:depth:0 valid:1 signed:0 trust:0-, 0q, 0n, 0m, 0f, 1u
/c/users/teddysun/.gnupg/pubring.gpg
------------------------------------
Pub 4096r/0ad6c46d 2017-02-22
UID Teddysun <i@xxxx.com>
Sub 4096r/5bb7bb4e 2017-02-22
The first line shows the public key file name (PUBRING.GPG)
The second line shows the public key characteristics (4,096-bit, Hash string, and build time)
The third line shows the user information

Line four shows the private key feature
Iv. Output key

The public key file (. gnupg/pubring.gpg) is stored in binary form, and the armor parameter can convert it to an ASCII display.
GPG--armor--output public-key.txt--export [key ID]

[key ID] Specifies the user's public key, such as the 0ad6c46d,output parameter to specify the output file name, such as Public-key.txt

Also, the Export-secret-keys parameter can convert the private key.
GPG--armor--output private-key.txt--export-secret-keys

Public-key.txt and Private-key.txt are exported to the user directory C:Users<用户名> below.
V. Upload the public key to Github account number
Click on user avatar, open Settings, left menu click SSH and GPG keys, GPG keys there, click New GPG key.
Fill in the input box with the Public-key.txt content you just exported.

Click Add GPG key to complete the upload.
Vi. Setting up Git
Back to Git Bash window, the key ID is known to be 0ad6c46d, based on the results shown just gpg–list-keys.

Set Git to use this key ID to encrypt:
git config--global user.signingkey 0ad6c46d

Set Git to use this key to encrypt globally:
git config--global commit.gpgsign true

Finally, enter the following command to view the Git configuration:
Git config-l

Contains the following information.
user.signingkey=0ad6c46d
Commit.gpgsign=true
At this point, the use of GPG encryption Github commits is officially completed. After you have Git commit, sync to Github, you will find that the commit has shown verified.
