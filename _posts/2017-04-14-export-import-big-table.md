---
layout: post
title: 数据库导入导出大表相关问题
date: 2017-04-14 18:40
---

# 导入/导出 大表相关问题

## TODO
- 补充“问题”描述
- 优化脚本

## 问题
Todo

## 分析
从线上数据库导出数据，如果 **记录集较大**（100万+），就需要考虑，对线上服务的影响。  

记录集较大，这个数值，需要根据实际情况调整。  
具体可以在数据库做导出测试。

为描述方便，下文 “导出” 场景，适用于“导出/导入”场景，可以参考。

从数据库导出大数据集，会给线上数据库造成瞬时压力。  
根据数据库服务器配置情况，导出大记录集，可能需要持续占用数据库几秒，甚至几分钟。  
期间，正常线上服务，都会收到影响。  

## 方法
为此，可以考虑IT界银弹—— **“拆分”** ！  

> **将大记录集“导出”操作，“拆分”为多个小记录操作。**  


**导出** 操作参考：

```shell
#!/bin/bash

# 如果需要查看执行详情，可以取消注释
# set -x

# 每次导出记录条数
size=50000

# 多少次完成，需要预先查询到导出记录总数
#
# select count(*) from test.user;
# 加入记录总数 2000000，那么times = 2000000 / size，等于40
times=40

# 并行导出进程数
# 建议不要过大，数据库服务器压力太大，会阻塞线上服务查询进程。
workers=4

for i in `seq 1 $times`
do
    while [ `ps aux | grep -v 'mysqld' | grep -c 'mysql'` -gt $workers ]
    do
        sleep 4
    done

    offset=$(($i * $size))
    mysql -hlocalhost -udbuser -phello123 test \
        -e "select * from user limit ${size} offset ${offset}" | gzip --fast > user.${i}.gz &
done
```

**导入** 操作参考：
```shell
#!/bin/bash

# set -x

workers=4

# 导入压缩sql数据文件
times=40

# 文件列表
# 需要自行适配sql
# for i in `echo file1.sql \
# file2.sql \
# file3.sql`

for i in `seq 1 $times`
do
    while [ `ps aux | grep -v 'mysqld' | grep -c 'mysql'` -gt $workers ]
    do
        sleep 4
    done

    gzip -d -c user.${i}.gz | mysql -hlocalhost -udbuser -phello123 test

    # 如果是sql文件
    # mysql -hlocalhost -udbuser -phello123 test < user.${i}.sql
done
```
