---
layout: post
title:  "Intall Oracle JDK 10 in Ubuntu"
date:   2017-07-12 14:39:43 -0500
author: rajendarreddy jagapathi
categories: java
---

Ubuntu comes with OpenJDK by default. You may need to remove OpenJDK first and install Oracle JDK as most of Enterprise apps use Oracle JDK.

### To Remove OpenJDK
- To Remove OpenJDK in Ubuntu, use the commands below: 

    ``` 
    sudo apt purge openjdk-*
    ```
    
### To Install Using Personal Package Archives (PPA)    
- To add linuxuprising PPA(webupd8team is not supporting java 9 and above) as there is not official Oracle PPA, use the commands below:

    ``` 
    sudo add-apt-repository ppa:linuxuprising/java && sudo apt update
    ```
- To install Oracle Java Jdk 10, use the commands below and you need to accept Oracle license aggreement when asked :

    ```
    sudo apt install oracle-java10-installer
    ```
    - If you're behind a Enterprise firewall that blocks some of the redirects required to download the Oracle Java archive, you can download the JDK tar.gz archive manually and place it under /var/cache/oracle-jdk8-installer - then, installing the "oracle-java8-installer" package will use the local archive instead of trying it to download it itself.
- To automatically accept the Oracle license, use below command if you did not accept it when you install for first time:

    ```
    echo oracle-java`0-installer shared/accepted-oracle-license-v1-1 select true | sudo /usr/bin/debconf-set-selections  
    ```
- To automatically set up the Java 10 environment variables, you can install the following package using below command:

    ```
    sudo apt install oracle-java10-set-default  
    ```
    - If you've already installed oracle-java8-set-default, they will be automatically removed when installing oracle-java10-set-default (and the environment variables will be set for Oracle Java 10 instead).
- To remove Oracle JDK and Install OpenJDK again, use below command: 

    ```
    sudo apt remove oracle-java10-installer && sudo apt install openjdk-10-jdk
    ```
    
### To Install from Oracle Website Manually

- Download latest version of Oracle JDK from [Oracle Website](http://www.oracle.com/technetwork/java/javase/downloads/index.html).For Java 10 and 64 bit linux, the file name would be: jdk-10.0.1_linux-x64_bin.tar.gz.
- Copy the downloaded JDK file to a directory where you want to install the JDK. I use /apps/java/jdk-10.0.1_linux-x64_bin.tar.gz.
- Open terminal window and navigate to the directory where you copied the downloaded file. Then type the command to Uncompress it

    ```
    tar -xvf jdk-10.0.1_linux-x64_bin.tar.gz
    ```
- The JDK 10 package is extracted into ./jdk-10.0.1. Jdk naming convention changes often. So, Create a softlink to avoid naming issues

    ```
    ln -s jdk-10.0.1 jdk10
    ```
- Now move the JDK 10 directory to /usr/lib

    ```
    sudo mkdir -p /usr/lib/jvm
    sudo mv ./jdk10 /usr/lib/jvm/
    ```
- Now run below commands to assign Oracle JDK a priority of 1, which means that installing other JDKs will replace it as the default. Be sure to use a higher priority if you want Oracle JDK to remain the default.

    ```
    sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk10/bin/java" 1
    ```
    
    ```
    sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk10/bin/javac" 1
    ```
    
    ```
    sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk10/bin/javaws" 1
    ```
- Correct the file ownership and the permissions of the executables:

    ```
    sudo chmod a+x /usr/bin/java
    ```
    
    ```
    sudo chmod a+x /usr/bin/javac
    ```
    
    ```
    sudo chmod a+x /usr/bin/javaws
    ```
    
    ```
    sudo chown -R root:root /usr/lib/jvm/jdk10
    ```

- Run Below commands to select default executables for java/javac/javaws:

    ```
    sudo update-alternatives --config java
    ```
    
    ```
    sudo update-alternatives --config javac
    ```
    
    ```
    sudo update-alternatives --config javaws
    ```
