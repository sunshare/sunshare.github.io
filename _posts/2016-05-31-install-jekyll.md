---
layout: post
title: 'Jekyll 文档系统'
date: 2016-05-31 20:05
---

准备好Ruby基础环境。   

**安装Jekyll**    

{% highlight bash %}
rvm --create 2.2.4@jekyll  
rvm use 2.2.4@jekyll  
gem install jekyll  
{% endhighlight %}


**准备Github帐号**   

- 注册Github帐号<https://github.com/>, 帐号名: `eellyphp`    
- 配置密钥到[Github](https://github.com/settings/keys)    
{% highlight bash %}
ssh-keygen -t rsa -b 4096 -C 'eellyphp@eelly.net'  
# copy ~/.ssh/id_rsa.pub  
# 配置到Github
{% endhighlight %}


**创建Jekyll文档系统**  

参考 **<http://jekyll.bootcss.com/>**.  

- 创建文档库<https://github.com/new>  *`eellyphp.github.io`*  
- 检出文档库到本地  
`git clone git@github.com:eellyphp/eellyphp.github.io.git`     

- 创建jekyll文档项目  
{% highlight base %}
cd eelly.github.io/  
jekyll new ./

ls .

[eelly@invo eellyphp]$ ll
total 36
-rw-r--r-- 1 eelly eelly  536 Jun  1 14:20 about.md 	# About Page
-rw-r--r-- 1 eelly eelly  891 Jun  1 14:20 _config.yml 	# Jekyll Config
drwxrwxr-x 2 eelly eelly 4096 Jun  1 14:20 css
-rw-r--r-- 1 eelly eelly 1291 Jun  1 14:20 feed.xml
drwxrwxr-x 2 eelly eelly 4096 Jun  1 14:20 _includes	# 模板文件
-rw-r--r-- 1 eelly eelly  506 Jun  1 14:20 index.html
drwxrwxr-x 2 eelly eelly 4096 Jun  1 14:20 _layouts	# 布局模板
drwxrwxr-x 2 eelly eelly 4096 Jun  1 14:20 _posts	# 默认文章目录
drwxrwxr-x 2 eelly eelly 4096 Jun  1 14:20 _sass
{% endhighlight %}


**启动本地服务**  

`jekyll build`  
`jekyll server -H 192.168.1.10 -P 8080 -B -w --safe -q`

打开浏览器访问<http://192.168.1.10:8080>.


## 系统工具备忘

- *init* 更改系统运行级别 /etc/inittab  
- *iperf3* 网络带宽工具  
- *chkconfig*  
- *service*  
