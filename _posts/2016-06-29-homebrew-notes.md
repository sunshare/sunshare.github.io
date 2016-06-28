---
layout: post
title : Homebrew 安装使用笔记
date  : 2016-06-29 03:08
---

# Reference

- http://brew.sh/
- [Chinese Install Doc](http://brew.sh/index_zh-cn.html)
- [Homebrew/services](https://github.com/Homebrew/homebrew-services)
- [Instresting Taps](https://github.com/Homebrew/brew/blob/master/share/doc/homebrew/Interesting-Taps-&-Branches.md)
  - [mac lnmp 环境搭建](http://www.cnblogs.com/RainLi/p/5347252.html)
  - [Mac下用brew搭建PHP(LNMP/LAMP)开发环境](http://yansu.org/2013/12/11/lamp-in-mac.html)



# Install

    brew install nginx

    brew install mysql

    # install PHP
    brew tap Homebrew/php

    brew install php55
    ... # other php55-*

    # services manage scripts
    brew tap Homebrew/services

    brew services start nginx
    
    brew services start mysql
    
    brew services start php55
