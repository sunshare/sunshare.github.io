---
layout: post
title: 'Common tips'
date: 2016-05-31 20:58
tags: tips
---


## Snippets  

    // trace into all fpm threads  
    ps -ef | grep fpm | awk '{print "-p " $2}' | xargs strace


    // 挂载为指定用户  
    work.src    /media/sf_work.src    vboxsf    gid=500,uid=500,umask=022,rw    0   0
    

    // Timestamp
    date +%s --date='2015-11-10 15:16:12'
    date -d @1372993650


    // vi
    :w  !sudo   tee  %


**DUMP DATABASE**
{% highlight sql %}
mysqldump -hlocalhost -uhello -pxxxx dbname --tables userinfo | gzip --fast > dbname-userinfo.gz
gzip -d -c dbname-userinfo.gz | mysql -h192.168.1.2 -uhello -pxxxx  dbname
{% endhighlight %}

**CREATE DATABASE**
{% highlight sql %}
create database test default collate 'utf8_general_ci' default character set 'utf8';
grant all on test.*  to 'hello'@'localhost';
set password for 'hello'@'localhost' = password('hello');
{% endhighlight %}

**建表** 
{% highlight sql %}
create table `comment`(
    `id` int unsigned not null auto_increment comment 'primary key',
    `type` tinyint unsigned not null default 0 comment 'xxx',
    `uid` int unsigned not null default 0 comment 'xxx',
    `content` varchar(200) not null default '' comment 'xxx',
    primary key (id),
    index `idx_r` (`uid`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='评论表';
{% endhighlight %}



## IP定位数据  

- 在线查询  
  - [淘宝IP查询](http://ip.taobao.com/ipSearch.php)  
  - [Ip Location](https://www.iplocation.net/)  

- 离线数据  
  - 关键字 `free geolocation database`  
  - <http://dev.maxmind.com/geoip/legacy/geolite/>  
  - **<http://freegeoip.net/>**  
  - **<https://github.com/fiorix/freegeoip>**  
