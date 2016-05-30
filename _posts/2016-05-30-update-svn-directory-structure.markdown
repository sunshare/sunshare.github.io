---
layout: post
title:  "调整svn目录结构"
date:   2016-05-30 18:04
categories: server
---


历史原因，目前svn目录结构没有按规范建立分支结构。  
现需要调整。

## 调整目录结构

1. 创建本地svn代码库oldsvn

    cd /data/svn  
    svnadmin create oldsvn  


2. 检出oldsvn，修改，提交 

    cd /data/svn/
    svn co file://localhost/data/svn/oldsvn oldcode  
    
    cd /data/svn/oldcode  
    touch hello.txt  
    svn add hello.txt  
    svn commit -m 'add hello.txt'  


3. 调整目录结构

    cd /data/svn/
    mkdir tags branches trunk  
    svn add tags branches trunk  
    svn commit -m "add structure directory"  
    svn mv hello.txt trunk/  
    svn commit -m 'rebuild directory structure'  


## 代码库迁移

1. 导出旧svn仓库oldsvn

    cd /data/svn  
    svnadmin dump /data/svn/oldsvn > oldsvn.dump 


2. 创建新仓库newsvn  

    cd /data/svn  
    svnadmin create newsvn  


3. 导入就仓库oldsvn到新仓库newsvn

    cd /data/svn  
    svnadmin load newsvn < oldsvn.dump  


## 参考
- https://kromey.us/2011/06/move-an-svn-repository-from-one-server-to-another-433.html  
