# Week 2 Lab Report
## Welcome new CSE 15L students!

## Table of Contents:
1. [Introduction](#introduction)
2. [Installing Visual Studio Code](#vscode)
3. [Remotely Connecting](#remote)
4. [Trying Some Commands](#commands)
5. [Moving Files With `scp`](#scp)
6. [Setting an SSH Key](#sshkey)
7. [Optimizing Remote Running](#optimize)

## **Introduction** <a name="introduction"></a>
Here is a guide on how to log on to your respective course-specific account on `ieng6`, which is a tool that you will need for this class! First, however, you will need to install Visual Studio Code.

---
## **Installing Visual Studio Code** <a name="vscode"></a>
To install Visual Studio Code, go to the [download website](https://code.visualstudio.com/) and follow the instructions for your respective operating system.

![Image](screenshots/vscode_download.png)

The webpage should look similar to the screenshot provided. Download the **stable** build for your operating system.

Once you have set up Visual Studio Code, your application should look something like this:

![Image](screenshots/blank_vscode.png)

If your application does not have a Terminal tab open at the bottom like in the screenshot, open a new terminal by going to Terminal on the top left, and click "New Terminal".

![Image](screenshots/terminal.png)

---
## **Remotely Connecting** <a name="remote"></a>
Now that you have Visual Studio Code set up, you need to access your CSE 15L course specific account. If you are on Windows, install OpenSSH, which is a program that allows you to remotely connect to other computers.

[Install OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse)

Follow all of the steps provided **until** the "Start and Configure OpenSSH Server" section.

Once you have OpenSSH installed, find your course-specific account for CSE 15L [here](https://sdacs.ucsd.edu/~icc/index.php). Your username should look something like `cs15lwi22zz`, where `wi22` is the quarter and year, and `zz` is your specific identifier.

Once you have found your username, go back to Visual Studio Code, into your terminal, and type:

`ssh username` where username is your username that you just looked up.

If you have never connected to this server, you will get a message looking like this:

```
The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.
RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

Type in `yes`, press enter, and you will get a prompt to type in your password. Keep in mind, when you type in your password, it will not show up in the terminal, not even as dots. Once you have typed in your password, you should recieve a message looking like this:

```
============================ NOTICE =================================
Authorized use of this system is limited to password-authenticated
usernames which are issued to individuals and are for the sole use of
the person to whom they are issued.

Privacy notice: be aware that computer files, electronic mail and
accounts are not private in an absolute sense.  You are responsible
for adhering to the ETS Acceptable Use Policies, which you can review at:
https://blink.ucsd.edu/faculty/instruction/tech-guide/policies/ets-acceptable-use-policies.html
=====================================================================

*** Problems, Suggestions, or Feedback ***

    For help requests, please create a ticket at:
    https://support.ucsd.edu/its

    You may also report issues, suggestions, or feedback by e-mailing root on any system:
    mail -s "Your subject here" root
    Type your message - Ctrl+D to send

*** Access our Linux ssh terminals or remote desktops via a web browser at: ***
    https://linuxcloud.ucsd.edu

    All accounts must be enrolled in Duo for access. No VPN required.


-------------------------------------------------------

quota: No filesystem specified.
Hello cs15lwi22aqp, you are currently logged into ieng6-202.ucsd.edu

You are using 0% CPU on this system

Cluster Status 
Hostname     Time    #Users  Load  Averages  
ieng6-201   13:00:01   17  3.09,  3.14,  3.22
ieng6-202   13:00:01   10  1.08,  1.08,  1.06
ieng6-203   13:00:01   15  0.03,  0.12,  0.33


Thu Jan 13, 2022  1:00pm - Prepping cs15lwi22
```

Now, you should be connected to the CSE basement computers!

---
## **Trying Some Commands** <a name="commands"></a>
Try running the following commands with different arguments on both your local machine and the server:

- `cd` - navigate through directories

![Image](screenshots/cd.png)

- `ls` - displays contents of current directory

![Image](screenshots/ls.png)

- `pwd` - finds the path of the current working directory

![Image](screenshots/pwd.png)

- `mkdir` - creates a new directory in the current working directory

![Image](screenshots/mkdir.png)

- `cp` - copies a file from the current directory to a different directory

![Image](screenshots/cp.png)

These are some out of the many extremely useful command line commands. Be sure to remember these for future reference!

---
## **Moving Files with `scp`** <a name="scp"></a>
Now, let's try using a command that lets us move files over SSH. This is incredibly important when working remotely so that you are able to copy files over the host and server computers.

First download <a href="WhereAmI.java" download>this file</a> that we will be moving over to your user on the server.

Once you have the file downloaded, go to the directory that contains that file and type:

![Image](screenshots/scp.png)

Your output should look similar to the screenshot.

Once you have your output, run these two commands on the server.

![Image](screenshots/javac.png)

These commands will run WhereAmI.java and tell you exactly where the file is on the server computer. If you get these outputs, congratulations! You have successfully copied a file over SSH.

## **Setting an SSH Key** <a name="sshkey"></a>
Now, is it not annoying typing in your password every time you want to remotely connect to the server? Well have no fear, because you can set an SSH key, which creates a public and private key specific to your computer that allows you to use those keys in place of your password.

To do this, run the command `ssh-keygen` which should give you an output like this:

![Image](screenshots/sshkeygen.png.jpg)

Once the command has run, it would have created two new files, `id_rsa` and `id_rsa.pub`. `id_rsa` is your private key while `id_rsa.pub` is your public key.

Now that you have the two files, go to the server and use the command `mkdir .ssh` to make the .ssh directory, then copy the **public** key over to the .ssh/authorized_keys folder.

![Image](screenshots/sshkey.jpg)

Try using ssh now to log on to your user on the server. You should not need a password now!

## **Optimizing Remote Running** <a name="optimize"></a>
In order to optimize your remote experience, you can make local changes to your file in Visual Studio Code, upload it to the server, and run it using some shortcuts.

These shortcuts include using the up arrow in your Visual Studio Code terminal to re-run previously typed commands like `ssh`, and using `ssh` to run commands on the server without acutally being on the server. For example:

![Image](screenshots/sshrun.jpg)

I just ran `ls` on the server without having to log on. You can also use semicolons to run multiple commands, like so:

![Image](screenshots/multiplecommands.jpg)

And thats all! Try to explore some other ways to run commands on the server remotely in order to find a more optimal workflow! I was able to personally cut down my keystroke count from 66 to 11!