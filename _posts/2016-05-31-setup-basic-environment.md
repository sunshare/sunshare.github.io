---
layout: post
title: '基础环境搭建'
date: 2016-05-31 20:05
tags: tips
---

基础环境搭建

## Ruby
    // 安装rvm
    curl -sSL https://get.rvm.io | bash -s stable

    // 引入环境定义。 
    // 注意：这个，因系统环境不一致，请根据提示操作。
    source ~/.profile

    // 查看可用的ruby版本
    rvm list known
    
    // 安装 指定版本（这里安装1.9.2）
    rvm install 1.9.2

    // 为特定工作环境定义gemset
    rvm --create 1.9.2@jekyll

    // 使用阿里gem源
    gem source -r https://rubygems.org/
    gem source -a http://mirrors.aliyun.com/rubygems/
    
    // rails项目 使用阿里gem源
    source 'http://mirrors.aliyun.com/rubygems/'
    gem 'rails', '4.0.2'


**参考**

- [RVM](https://rvm.io/rvm/install)
- [阿里gem源站](http://mirrors.aliyun.com/help/rubygems)


## Python

### Virtualenv

    sudo yum install -y python-pip

    sudo pip install virtualenv

    // 创建一个新工作环境 helloworld
    // --no-site-packages 这个选项忽略全局安装的包
    // 所有在此环境需要的包，都会独立安装到此环境下
    virtualenv -p /usr/bin/python2.7 helloworld

    // 激活helloworld环境
    source helloworld/bin/activate
    pip install requests

    // 退出helloworld环境
    deactivate 

    // 导出当前工作环境配置列表
    pip freeze > requirements.txt

    // 重建工作环境
    pip install -r requirements.txt

    // virtualenvwrapper
    // ref : http://virtualenvwrapper.readthedocs.org/en/latest/command_ref.html
    pip install virtualenvwrapper
    export WORKON_HOME=~/pyenv
    source /usr/local/bin/virtualenvwrapper.sh
    mkvirtualenv helloworld

    // 使用国内pip源站
    // http://mirrors.aliyun.com/pypi/simple
    /etc/pip.conf
        [global]
        index-url = http://pypi.douban.com/simple


**参考**

- [安装](http://virtualenv.readthedocs.org/en/latest/installation.html)  
- [国内pip源站](http://www.cnblogs.com/cmsd/p/3677412.html)  
  - [Ali](http://mirrors.aliyun.com/pypi/simple)
  - [Douban](http://pypi.douban.com/simple)
- [pip用户手册](https://pip.pypa.io/en/latest/user_guide.html)  


## 服务器基础环境

    // 系统启动模式，runlevel,init,telinit
    /etc/inittab

    // 系统服务脚本
    /etc/init.d/nginx

    // 启动服务
    service nginx restart

    // 系统启动时，自启动服务
    chkconfig --level 345 nginx on
    chkconfig --list 

## NTP

## Nginx

## PHP

## Jekyll 文档系统


## 系统工具备忘

- *init* 更改系统运行级别 /etc/inittab  
- *iperf3* 网络带宽工具  
- *chkconfig*  
- *service*  
