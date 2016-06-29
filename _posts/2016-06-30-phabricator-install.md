---
layout  : post
title   : 'Phabricator Beginning Notes'
date    : 2016-06-30 00:30
---

## 文档

- **[Phabricator 文档](https://secure.phabricator.com/book/phabricator/)**
- [安装文档](https://secure.phabricator.com/book/phabricator/article/installation_guide/)
- [配置文档](https://secure.phabricator.com/book/phabricator/article/configuration_guide/)
- [翻译](https://secure.phabricator.com/book/phabcontrib/article/internationalization/)
  - https://github.com/wanthings
  - https://github.com/lingochamp/phabricator/tree/simplified-chinese-l10n
  

## 安装

    // 下载代码
    cd /www/phabricator/
    git clone https://github.com/phacility/libphutil.git
    git clone https://github.com/phacility/arcanist.git
    git clone https://github.com/phacility/phabricator.git

    // 配置web server Nginx
    参考“Nginx 配置”
    service nginx restart

    // bin/* 目录工具执行报错，临时修复
    // 确认为VBox共享文件夹造成的。

    bin/config list
    // 报错 ../scripts/setup/manage_config.php: No such file or directory
    // 原因不明
    // 临时方案：创建链接到 对应的php文件，参考“修改bin目录工具，创建链接”. 
    // !!! 已明确是virtualbox共享文件夹问题 !!!

    // 配置数据库
    cd /www/phabricator/phabricator/
    bin/config set mysql.host localhost
    bin/config set mysql.user sunshare
    bin/config set mysql.pass fasdkfja

    // 访问我们的站点 phabircator.example.com

    // 根据提示执行
    # 这一步涉及表结构修改，mysql授权root权限
    bin/config set mysql.user root
    bin/config set mysql.pass faksjdf9823uy1243*F&9

    bin/storage upgrade

    // 后台任务 **想办法弄成开机启动**
    bin/phd start

    // 优化 **通知系统，可以替换为nodejs实时系统**


## nginx 配置

    server {
      server_name phabricator.example.com;
      root        /path/to/phabricator/webroot;

      location / {
        index index.php;
        rewrite ^/(.*)$ /index.php?__path__=/$1 last;
      }

      location = /favicon.ico {
        try_files $uri =204;
      }

      location /index.php {
        fastcgi_pass   localhost:9000;
        fastcgi_index   index.php;

        #required if PHP was built with --enable-force-cgi-redirect
        fastcgi_param  REDIRECT_STATUS    200;

        #variables to make the $_SERVER populate in PHP
        fastcgi_param  SCRIPT_FILENAME    $document_root$fastcgi_script_name;
        fastcgi_param  QUERY_STRING       $query_string;
        fastcgi_param  REQUEST_METHOD     $request_method;
        fastcgi_param  CONTENT_TYPE       $content_type;
        fastcgi_param  CONTENT_LENGTH     $content_length;

        fastcgi_param  SCRIPT_NAME        $fastcgi_script_name;

        fastcgi_param  GATEWAY_INTERFACE  CGI/1.1;
        fastcgi_param  SERVER_SOFTWARE    nginx/$nginx_version;

        fastcgi_param  REMOTE_ADDR        $remote_addr;
      }
    }


## 修改bin目录工具，创建链接 

**!!!可忽略，已明确是virtualbox共享文件夹造成的问题**

    #!/bin/sh

    # 定义phabricator代码目录
    PHABRICATOR_BASE='/home/eelly/work/phabricator/phabricator/'

    CMD_LIST=`ls ${PHABRICATOR_BASE}bin/`

    cd ${PHABRICATOR_BASE}
    cp -rf bin bin.orig

    for CMD in ${CMD_LIST}
    do
      FILE=`cat bin.orig/${CMD}`
      ln -sf ${FILE} bin/${CMD}
    done


## Diffusion

- [Diffusion](https://secure.phabricator.com/book/phabricator/article/diffusion_managing/)
- [代码库管理](https://secure.phabricator.com/book/phabricator/article/diffusion_uris/)


## 代码后审系统 Audit

- **[Audit User Guide](https://secure.phabricator.com/book/phabricator/article/audit/)**
- [自定义业务规则](https://secure.phabricator.com/book/phabricator/article/herald/)
