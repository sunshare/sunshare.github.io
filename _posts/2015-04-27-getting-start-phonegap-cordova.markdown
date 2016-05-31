---
layout: post
title:  "Phonegap/Cordova 入门笔记"
date:   2015-04-27 11:24:00
tags: html5 mobile tutorial
---

## 简介
Phonegap/Cordova工具，可以帮助开发者，使用html5,css,javascript等常规web技术，开发智能手机应用。  
目前支持苹果iOS，安卓Android，黑莓Blackberry，微软WP等平台。  
Phonegap经过发展，提取、整理了核心代码提交到Apache基金组织管理，重命名为Cordova。  


## 安装
这里主要介绍Android环境搭建，配合Cordova使用。  


### 安装Android ADT
在[Android开发]()上找到 `Develop -> tools -> Dowload`, 单独[下载ADT](http://developer.android.com/sdk/index.html#Other)，选择对应平台，下载安装。  
打开`Android SDK Manager`，安装最新的SDK工具。  
打开`Android SDK Manager -> Tools -> Mange ADVs... `，创建一个模拟器。  

### 安装Eclipse  
[下载Eclipse](http://www.eclipse.org/downloads/)开发套件。  
打开`Help -> Install New Software... -> Available Software Sites`,添加Google Android下载站点`https://dl-ssl.google.com/android/eclipse/`。


安装：  

- Android DDMS
- Android Development Tools
- Android Hierarchy Viewer
- Android Native Development Tools
- ndroid Traceview
- Tracer for OPenGL ES


### 安装Cordova
使用npm安装Cordova。  

- 安装node-0.10.xx  
在[nodejs下载页](https://nodejs.org/download/)找到[other releases](http://nodejs.org/dist/)，下载0.10.xx版本（Cordova要求版本）。

- 安装cnpm，使用淘宝node源  
在[淘宝npm源站](http://npm.taobao.org/),找到安装信息。  
打开命令行终端，安装`cnpm`：  
   `npm install -g cnpm --registry=https://registry.npm.taobao.org`  
之后使用`cnpm`安装node模块，可以从淘宝npm源下载。  

- 安装cordova  
参考[Cordova -> The Command-Line Interface](https://cordova.apache.org/docs/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)。  
   `cnpm install -g cordova`


## 使用示例  

参考[Cordova -> The Command-Line Interface](https://cordova.apache.org/docs/en/4.0.0/guide_cli_index.md.html#The%20Command-Line%20Interface)。  

{% highlight bash %}
cordova create hello com.example.hello HelloWorld
cd hello
cordova platform add android
cordova build android
cordova emulate android
#=> 在模拟器中打开测试项目`HelloWorld`
{% endhighlight %}


## 关键词
- [Cordova](https://cordova.apache.org/)  
- [Eclipse](http://www.eclipse.org)  
- [PhoneGap](http://phonegap.com/)  

