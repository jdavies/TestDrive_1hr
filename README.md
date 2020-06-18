# OCI Fundamentals - Test Drive

The instructions for the 1 hour test drive video that you saw during the webinar. Follow these instructions to build your own load balanced web server.

## Overview

In this set of labs you will learn how to use Oracle Cloud Infrastructure (OCI) to create a redundant, load balanced set of web servers. As a part of this overarching goal, you will learn how to create and configure a virtual cloud network, routing rules, compute instances and more. By the end of this series of labs you will have had experience building a real world solution that is scalable and reliable. This lab aloe will not grant you mastery of OCI and its technologies, but it will take you from "zero to 60" very quickly.

This set of abs may appear daunting at first, due to their sheer number and size. However, it appears long because of all of the screenshots and detailed step-by-stp instructions. Remember, I was able to demnstrate all of this in an hour!

## Prerequisites

To perform these labs you must have the following:

1. A Windows/Mac/Linux machine that can connect to the internet
2. Internet access
3. Basic familiarity with using the command line (aka the terminal). You don't need any coding experience (though it helps) because I will walk you through each step.

## Lab 1 - Creating SSH Keys

To connect to some of our "assets" in OCI, you will need to create your own SSH key. SSH stand for "Secure SHell" and is a protocol nd technology for remotely connecting to computers using the command line. You wont use it alot in this set of labs, but you will need it for some.

The process of creating your own SSH keys varies depending on your platform. Choose your platform below and follow those instructions to create your SSH keys.

### WINDOWS

1. Install git for windows. Download the latest release from [Gitbash](https://github.com/git-for-windows/git/releases) and install.

2. Open Git-bash:

    ![Open GitBash](media/image1.png)

3. Generate ssh-keys by running this command in Gitbash and hit enter for all steps:

```shell
ssh-keygen  
Generating public/private rsa key pair.  
Enter file in which to save the key
(/c/Users/username/.ssh/id\_rsa):  
Created directory '/c/Users/username/.ssh'.  
Enter passphrase (empty for no passphrase):
Enter same passphrase again:  
Your identification has been saved in /c/Users/username/.ssh/id\_rsa.  
Your public key has been saved in /c/Users/username/.ssh/id\_rsa.pub.  
```

**Note**: In Gitbash, the directory `C:\\Users\\username\\` is shown as `/c/Users/username/`

**NOTE**
These instructions will create a minimally secure ssh key for you (***and one well suited for this tutorial***). For production environments we recommend an SSH-2 RSA key with 4096 bits and a passphrase. Here is the sample command format:

```shell
ssh-keygen -t rsa -b 4096 -N "<myPassphrase>" -f <key file name> -C "This is my comment"
```

And for a concrete example:

```shell
ssh-keygen -t rsa -b 4096 -N "MySecretPhrase" -f my_oci_key -C "This is my comment"
```

### MAC/LINUX

1. Enter the following command if you are using MAC or Linux Desktop:

    ```shell
      ssh-keygen -f oci_testdrive -C "My OCI Test Drive SSH key"
    ```

    This will create two files in your current directory. The first file is names **oci_testdrive** and it is your SSH private key. You d not share this key with anyone or any computer system. The second file is named **oci_testdrive.pub**. This is your public SSH key and it is the key you will upload to the OCI compute instances that you will create later in this set o labs.

2. Make sure permissions are restricted, sometimes ssh will fail if private keys have permissive permissions.

    ```shell
        chmod 0700 .
        chmod 0600 oci_testdrive
        chmod 0644 oci_testdrive.pub
    ```
