# OCI Fundamentals - Test Drive

The instructions for the 1 hour test drive video that you saw during the webinar. Follow these instructions to build your own load balanced web server.

## Table of Contents

- [OCI Fundamentals - Test Drive](#oci-fundamentals---test-drive)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Prerequisites](#prerequisites)
  - [Lab 1 - Creating SSH Keys](#lab-1---creating-ssh-keys)
    - [WINDOWS](#windows)
    - [MAC/LINUX](#maclinux)
  - [Lab 2 - Logging into Oracle Cloud Infrastructure](#lab-2---logging-into-oracle-cloud-infrastructure)
    - [Console Overview](#console-overview)
  - [Lab 3: Creating Compartments](#lab-3-creating-compartments)
    - [Compartments Overview](#compartments-overview)

## Overview

In this set of labs you will learn how to use Oracle Cloud Infrastructure (OCI) to create a redundant, load balanced set of web servers. As a part of this overarching goal, you will learn how to create and configure a virtual cloud network, routing rules, compute instances and more. By the end of this series of labs you will have had experience building a real world solution that is scalable and reliable. This lab aloe will not grant you mastery of OCI and its technologies, but it will take you from "zero to 60" very quickly.

This set of abs may appear daunting at first, due to their sheer number and size. However, it appears long because of all of the screenshots and detailed step-by-stp instructions. Remember, I was able to demnstrate all of this in an hour!

[Top](#table-of-contents)

## Prerequisites

To perform these labs you must have the following:

1. A Windows/Mac/Linux machine that can connect to the internet
2. Internet access
3. Basic familiarity with using the command line (aka the terminal). You don't need any coding experience (though it helps) because I will walk you through each step.

[Top](#table-of-contents)

## Lab 1 - Creating SSH Keys

To connect to some of our "assets" in OCI, you will need to create your own SSH key. SSH stand for "Secure Shell" and is a protocol nd technology for remotely connecting to computers using the command line. You wont use it alot in this set of labs, but you will need it for some.

The process of creating your own SSH keys varies depending on your platform. Choose your platform below and follow those instructions to create your SSH keys.

### WINDOWS

1. Install git for windows. Download the latest release from [Gitbash](https://github.com/git-for-windows/git/releases) and install.

2. Run Git-bash:

3. Enter the following command:

    ```shell
    ssh-keygen -f oci_testdrive -C "My OCI Test Drive SSH key"
    ```

    ***When prompted for the passphrase you my leave it blank.***
    
    This will create two files in your current directory. The first file is names **oci_testdrive** and it is your SSH private key. You d not share this key with anyone or any computer system. The second file is named **oci_testdrive.pub**. This is your public SSH key and it is the key you will upload to the OCI compute instances that you will create later in this set o labs.

4. Make sure permissions are restricted, sometimes ssh will fail if private keys have permissive permissions.

    ```shell
    chmod 0700 .
    chmod 0600 oci_testdrive
    chmod 0644 oci_testdrive.pub
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

    ***When prompted for the passphrase you my leave it blank.***
    
    This will create two files in your current directory. The first file is names **oci_testdrive** and it is your SSH private key. You d not share this key with anyone or any computer system. The second file is named **oci_testdrive.pub**. This is your public SSH key and it is the key you will upload to the OCI compute instances that you will create later in this set o labs.

2. Make sure permissions are restricted, sometimes ssh will fail if private keys have permissive permissions.

    ```shell
        chmod 0700 .
        chmod 0600 oci_testdrive
        chmod 0644 oci_testdrive.pub
    ```

**NOTE**
These instructions will create a minimally secure ssh key for you (***and one well suited for this tutorial***). For production environments we recommend an SSH-2 RSA key with 4096 bits and a passphrase. Here is the sample command format:

```shell
ssh-keygen -t rsa -b 4096 -N "<myPassphrase>" -f <key file name> -C "This is my comment"
```

And for a concrete example:

```shell
ssh-keygen -t rsa -b 4096 -N "MySecretPhrase" -f my_oci_key -C "This is my comment"
```

[Top](#table-of-contents)

## Lab 2 - Logging into Oracle Cloud Infrastructure

### Console Overview

In this practice, you sign in to the Oracle Cloud Infrastructure console using your credentials.

1. Open a supported browser and go to the Console URL:  [https://oracle.com](https://oracle.com).

2. Click on the portrait icon in the top-right section of the browser window, then click on the **Sign in to Cloud** link.

   ![Main Sign-in page]( images/SignIn01.png)

3. Enter the name of your tenancy (aka your account name, not your user name), then click on the **Next** button.

   ![Enter tenancy name]( images/SignIn02.png)

4. Oracle Cloud Infrastructure is integrated with Identity Cloud Services, you will see a screen validating your Identity Provider. Enter your username and password. Click **Sign In**.

   ![Username and password fields]( images/SignIn03.png)

5. When you sign in to the Console, the dashboard is displayed.

   ![Dashboard view]( images/SignIn04.png)

## Lab 3: Creating Compartments

### Compartments Overview

A compartment is a collection of cloud assets, like compute instances, load balancers, databases, etc. By default, a root compartment was created for you when you created your tenancy (ie when you registered for the trial account). It is possible to create everything in the root compartment, but Oracle recommends that you create sub-compartments to help manage your resources more efficiently.

1. From the menu, select **Identity** and **Compartments**. You will have to scroll all the way to the bottom of the main menu to find the Identity menu item.

   ![Create a compartment]( images/MenuIdentity01.png)

2. Click on the blue **Create Compartment** button to create a sub-compartment.

   ![Create a compartment]( images/Compartment01.png)

3. Name the compartment **Demo** and provide a short description. Be sure your root compartment is shown as the parent compartment. Press the blue **Create Compartment** button when ready.

   ![Create compartment]( images/Compartment02.png)

4. You have just created a compartment for all of your work in this Test Drive.

[Top](#table-of-contents)
