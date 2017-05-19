---
layout: post
title: "ThinkPHP笔记"
date: 2017-04-14 18:20
---

# ThinkPHP笔记

## 概览
- 路由规则
    - 中定义的路由地址是按照控制器名的实际名称定义（区分大小写）。
    - `url_convert`
- trait
    - 优先级（当前类方法 > trait > 父类方法）
    - 冲突解决（`as`）
- api 调试
    - socket
- 配置
    - 5.0.1开始增加了扩展配置目录的概念，在应用配置目录或者模块配置目录下面增加extra子目录，下面的配置文件都会自动加载，无需任何配置
    - 场景配置`app_status`（加载顺序/覆盖问题）
    - 环境变量配置 application/.env
- 路由
- `Route::rule('new/:id','News/update','POST'); // 路由方法参数：大写 POST`
- 缓存路由请求（~~缓存什么：请求返回结果？路由解析结果？~~）
    - 缓存请求结果（缓存能配置时间。**是否能配置缓存系统？**）
- 资源路由（restful）
- 模型
    - 如果你是在模型内部，请不要使用$this->name的方式来获取数据，请使用$this->getAttr('name') 替代。
- ​

- 模型
    - 关联统计
    ```php
    $list = User::withCount(['cards'=>function($query){
        $query->where('status',1);
    }])->select([1,2,3]);
    foreach($list as $user){
        // 获取用户关联的card关联统计
        echo $user->cards_count;
    }
    ```


## 部署

### Nginx 配置

**thinkphp5**
```
server {
    listen 80;
    server_name    tp.xman.com;

    access_log    /home/xman/log/tp_xman_com_access.log;
    set        $root    /home/xman/work/thinkphp5/public;

    location ~ .*\.(gif|jpg|jpeg|bmp|png|ico|txt|js|css)$
    {
        root $root;
    }

    location / {
        root    $root;
        index    index.html index.php;
        if ( -f $request_filename) {
            break;
        }
        if ( !-e $request_filename) {
            rewrite ^(.*)$ /index.php/$1 last;
            break;
        }
    }

    location ~ .+\.php($|/) {
        fastcgi_pass    127.0.0.1:9000;
        fastcgi_split_path_info ^((?U).+.php)(/?.+)$;
        fastcgi_param PATH_INFO $fastcgi_path_info;
        fastcgi_param PATH_TRANSLATED $document_root$fastcgi_path_info;
        fastcgi_param    SCRIPT_FILENAME    $root$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```

**Thinkphp323**
```
server {
    listen 80;
    #listen 80 default_server;
    #listen [::]:80 default_server ipv6only=on;

    access_log /home/ubuntu/logs/tp_t_com.access.log;

    # Make site accessible from http://localhost/
    server_name tp.t.com;

    location / {
        root /home/ubuntu/workspace/thinkphp323;
        index index.html index.htm;

        if (!-e  $request_filename){
            rewrite ^(.*)$ /index.php$1 last;
        }
    }

    location ~ \.php {   
        root /home/ubuntu/workspace/thinkphp323;

        fastcgi_pass 127.0.0.1:9000;

        #定义变量 $path_info ，用于存放pathinfo信息
        set $path_info "";
        #定义变量 $real_script_name，用于存放真实地址
        set $real_script_name $fastcgi_script_name;
        #如果地址与引号内的正则表达式匹配
        if ($fastcgi_script_name ~ "^(.+\.php)(/.+)$") {
            #将文件地址赋值给变量 $real_script_name
            set $real_script_name $1;
            #将文件地址后的参数赋值给变量 $path_info
            set $path_info $2;
        }

        #配置fastcgi的一些参数
        fastcgi_param SCRIPT_FILENAME $document_root$real_script_name;
        fastcgi_param SCRIPT_NAME $real_script_name;
        fastcgi_param PATH_INFO $path_info;

        fastcgi_index index.php;
        include fastcgi_params;
    }

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    location ~ /\.ht {
        deny all;
    }
}

```

## Keyword
- [PJAX的实现与应用](http://www.cnblogs.com/hustskyking/p/history-api-in-html5.html)
- [Pjax是什么以及为什么推荐大家用](https://my.oschina.net/sub/blog/123447)
