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


# 替换国内源

- [知乎问题](http://www.zhihu.com/question/31360766)  
- [中国科学技术大学utsc源](https://lug.ustc.edu.cn/wiki/mirrors/help)  

    // 替换git镜像  
    cd /usr/local  
    git remote set-url origin git://mirrors.ustc.edu.cn/homebrew.git  
    
    // 替换bottles二进制源  
    echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile  
    source ~/.bash_profile  
