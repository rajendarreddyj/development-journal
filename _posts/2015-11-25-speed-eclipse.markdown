---
layout: post
title:  "Speed Up Eclipse for Java Development!"
date:   2015-11-25 22:01:43 +0530
author: rajendarreddy jagapathi
categories: eclipse
---
Follow below steps to speed up your Eclipse IDE; it works on most of my environments (Ubuntu/Windows 7/Windows Server 2008 r2).

- Always make sure you have latest version of Oracle JDK (do not use Open JDK) and eclipse. Below are links to Eclipse and JDK. 
- If you are using Windows with antivirus software installed, make sure you add JDK/Eclipse/workspace/source code directories to Whitelist of antivirus software.
- Clean up history and indexes of Eclipse workspace. This will reduce RAM usage and hard disk usage of workspace.
- To cleanup indexes. Go to below directory and delete files within that directory.
  ```
  workspace_path\.metadata\.plugins\org.eclipse.jdt.core
  ```
- To cleanup indexes. Go to below directory and delete files within that directory.
  ```
  workspace_path\.metadata\.plugins\org.eclipse.core.resources
  ```
- Do not use version control plugins like subclipse/git within work space. It is really hard to stop using integration plugins but removing them will speed up eclipse. Use standalone tools like tortoisesvn/smartgit instead.
- Disable unnecessary validators in Eclipse preferences. Choose validators that suit your project.
