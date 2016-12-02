---
layout: post
title: "Linux环境笔记"
date: 2016-12-02
---

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
    
    
    // trace into all fpm threads  
    ps -ef | grep fpm | awk '{print "-p " $2}' | xargs strace

    // virtualbox共享文件夹 挂载为指定用户  
    work.src    /media/sf_work.src    vboxsf    gid=500,uid=500,umask=022,rw    0   0

    // Timestamp
    date +%s --date='2015-11-10 15:16:12'
    date -d '@1372993650'

    // vi save as root in editING
    :w  !sudo   tee  %
