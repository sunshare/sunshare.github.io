---
title: 'Android基础笔记'
layout: post
date: 2016-05-31 19:37
tags: android basic
---

## 文档
- http://wear.techbrood.com/index.html
- http://www.androiddevtools.cn/
- http://android-mirror.bugly.qq.com:8080/
- http://www.android-studio.org/


## 环境搭建
**工具下载**
- <http://android-mirror.bugly.qq.com:8080/AndroidStudio/>

**国内SDK源镜像**
- android-mirror.bugly.qq.com:8080
- mirrors.neusoft.edu.cn:80
- mirrors.opencas.cn:80

**配置国内镜像**

    [Tools] -> [Options] 
        [Proxy Settings]
            [HTTP Proxy Server]      
            [HTTP Proxy Port]    
        [Others]
            [Force ...] checked

    [Packages] -> [Reload]


## 报错

**emulator: ERROR: x86 emulation currently requires**

    emulator: ERROR: x86 emulation currently requires hardware acceleration!Please ensure Intel HAXM is properly installed and usable.CPU acceleration status: HAX kernel module is not installed!

- http://www.cnblogs.com/csulennon/p/4178404.html
