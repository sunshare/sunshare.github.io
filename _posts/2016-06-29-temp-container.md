---
layout: post
title : "临时记录"
date  : 2016-06-29 09:23
---

## Virtualbox 安装增强工具包
- find `VBoxGuestAdditions.iso` in directory where virtualbox installed.  
- select the `VBoxGuestAdditions.iso` in virual instance CD device.  
- mount in virtual instance : `mount -t auto -o ro /dev/cdrom /mnt/`
- `cd /mnt; sudo ./VBoxLinuxAdditions.run;`


## 编译安装subversion-1.8.16

- [libsqlite3](http://sqlite.org/download.html)

支持http协议访问
- [libserf](http://serf.apache.org/download)
- [scons](http://scons.org/pages/download.html)

  ./configure --with-serf=/usr/local
