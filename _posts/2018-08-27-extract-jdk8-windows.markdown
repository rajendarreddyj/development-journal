---
layout: post
title:  "Extract Oracle JDK 8 in Windows(post 8u102)"
date:   2018-08-27 11:21:43 +0530
author: rajendarreddy jagapathi
categories: java
---

I would like to extract jdk from exe and point to it in eclipe.

## Extract JDK bin

### Download JDK from oracle(http://www.oracle.com/technetwork/java/javase/downloads/index.html).

### Extract exe file using 7-zip. It will be extracted to .rsrc directory.  
    
### Open command prompt and go to .rsrc directory.

### Goto 1033\JAVA_CAB10 directory in .rsrc directory.

### Run below command to extract cab.

```
extrac32 111
```

### it is extracted to tools.zip in 1033\JAVA_CAB10.

### Extract tools.zip using 7-zip. It will be extracted to tools directory.

### Go to tools directory in 1033\JAVA_CAB10 directory.

### Run below command to extract jar.

```
for /r %x in (*.pack) do .\bin\unpack200 -r "%x" "%~dx%~px%~nx.jar"
```

## Extract src

### Goto 1033\JAVA_CAB9 directory in .rsrc directory.

### Run below command to extract cab.

```
extract 110
```
### it is extracted to src.zip in 1033/JAVA_CAB9.

### move src.zip to tools directory in 1033\JAVA_CAB10.

### Rename tools directory in 1033\JAVA_CAB10 to JDK8

### Add JDK8 to eclipse in installed JREs
