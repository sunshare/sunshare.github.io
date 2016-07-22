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


## LISP学习点滴

- [LISP](https://common-lisp.net/)  
- [Get Start](http://cliki.net/Getting%20Started)  
- [Getting going with modern Common Lisp on Mac OS X](http://www.jonathanfischer.net/modern-common-lisp-on-osx/)  
- [Common Lisp implementation](http://cliki.net/Common%20Lisp%20implementation)
- [SBCL](http://www.sbcl.org/)
- [quicklisp lisp库管理工具](https://www.quicklisp.org/beta/)
- LISP学习资料参考
  - [ANSI Common Lisp 中文版 ](http://acl.readthedocs.io/en/latest/zhCN/ch1-cn.html)
  - [Lisp 入门](https://zh.wikibooks.org/wiki/Lisp_%E5%85%A5%E9%96%80)
  - [Lisp之根源](http://daiyuwen.freeshell.org/gb/rol/roots_of_lisp.html)
  - [LISP的本质(THE NATURE OF LISP)](http://www.cnblogs.com/Leap-abead/articles/762180.html)


### Install SBCL && quicklisp

    // Install SBCL
    $ tar xjf sbcl-1.0.29-x86-darwin-binary-r2.tar.bz2
    $ cd sbcl-1.0.29-x86-darwin
    $ sudo sh install.sh
    $ sbcl


    // Install quicklisp
    // https://www.quicklisp.org/beta/#installation
    $ curl -O https://beta.quicklisp.org/quicklisp.lisp
    $ sbcl --load quicklisp.lisp
    * (quicklisp-quickstart:install)
    * (ql:add-to-init-file)
    * (quit)
