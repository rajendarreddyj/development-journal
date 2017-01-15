---
layout: post
title:  "Prepare development environment for Java in Ubuntu"
date:   2016-08-21 15:18:43 +0530
author: rajendarreddy jagapathi
categories: ubuntu
---
In order to get started developing in Java, we’ll need the following:

-   An OS. MacOS, Windows or Ubuntu (any Linux Distribution).
-   A Java JRE (Java Runtime Environment). Covers most end-users needs. Contains everything required to run Java applications on your system.
-   A Java JDK (Java SE Development Kit). The JDK or Java SDK (Software Development Kit) typically includes a complete JRE plus tools for developing, debugging, and monitoring Java applications.
-   An IDE – Integrated Development Environment. 

I am using Ubuntu distribution so I will use apt to install, if you are using Fedora/CentOS you can use yum/dnf.

-   VirtualBox: is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.

    -   I use virtualbox to isolate development in a clean environment.
    
    -   To add Oracle public key, do
    
        ```
        wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
        ```
        
        ```
        wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
        ```
        
    -   To install VirtualBox, do
        
        ```
        sudo apt update
        ```
        
        ```
        sudo apt install virtualbox-5.1
        ```
        
    -   Ubuntu/Debian users might want to install the dkms package to ensure that the VirtualBox host kernel modules (vboxdrv, vboxnetflt and vboxnetadp)     are properly updated if the linux kernel version changes during the next apt upgrade.
    
        ```
        sudo apt install dkms
        ```
        
    -   To access VirtualBox shared folder across multiple guest operating systems.
    
        ```
        sudo usermod -aG vboxsf <username>
        ```
        
-   Oracle JDK (Java Development Kit):  is typically includes a complete JRE plus tools for developing, debugging, and monitoring Java                 applications.

    -   To add webupd8team PPA as there is not official Oracle PPA, use the commands below:
    
        ```
        sudo add-apt-repository ppa:webupd8team/java && sudo apt update
        ```
        
    -   To install Java 8
        ```
        sudo apt-get install oracle-java8-installer
        ```
        
-   SDKMAN: is a tool for managing parallel versions of multiple Software Development Kits on most Unix based systems. It provides a convenient Command Line Interface (CLI) and API for installing, switching, removing and listing Candidates. Formerly known as GVM the Groovy enVironment Manager.

    -   To install sdkman, do
    
    ``` 
        curl -s "https://get.sdkman.io" | bash
    ```
    
    ```
        source "$HOME/.sdkman/bin/sdkman-init.sh"
    ```
    
    -   To install Gradle (Gradle is a build automation tool that builds upon the concepts of Apache Ant
        and Apache Maven and introduces a Groovy-based domain-specific language (DSL)
        instead of the more traditional XML form of declaring the project
        configuration.)
        
    ```
        sdk install gradle
    ```
    
    -   To install maven (Apache Ant is a Java library and command-line tool whose mission is to drive
        processes described in build files as targets and extension points dependent
        upon each other.)
        
    ```
        sdk install maven
    ```
    
    -   To install ant (Apache Ant is a Java library and command-line tool whose mission is to drive
        processes described in build files as targets and extension points dependent
        upon each other.)
        
    ```
        sdk install ant
    ```
