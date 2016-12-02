---
layout: post
title: '安装Ruby环境'
date: 2016-12-02 20:31
---


{% highlight bash %}
# 安装rvm
curl -sSL https://get.rvm.io | bash -s stable

# 引入环境定义。 
# 注意：这个，因系统环境不一致，请根据提示操作。
source ~/.profile

# 查看可用的ruby版本
rvm list known

# 安装 指定版本（这里安装1.9.2）
rvm install 1.9.2

# 为特定工作环境定义gemset
rvm --create 1.9.2@jekyll

# 使用阿里gem源
gem source -r https://rubygems.org/
gem source -a http://mirrors.aliyun.com/rubygems/
{% endhighlight %}


**参考**

- [RVM](https://rvm.io/rvm/install)
- [阿里gem源站](http://mirrors.aliyun.com/help/rubygems)
