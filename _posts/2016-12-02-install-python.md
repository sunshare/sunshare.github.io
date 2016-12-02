---
layout: post
title: '安装Python环境'
date: 2016-12-02 20:53
---

{% highligtht bash %}

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
        
{% endhighlight %}


**参考**

- [安装](http://virtualenv.readthedocs.org/en/latest/installation.html)  
- [国内pip源站](http://www.cnblogs.com/cmsd/p/3677412.html)  
  - [Ali](http://mirrors.aliyun.com/pypi/simple)
  - [Douban](http://pypi.douban.com/simple)
- [pip用户手册](https://pip.pypa.io/en/latest/user_guide.html)  
