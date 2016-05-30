---
layout: post
title:  "SQL操作条件字段包含NULL值情况"
date:   2016-05-30 17:58
categories: jekyll update
---


**所有与`NULL`值进行的 `比较` 运算，结果都是 `NULL`.**

这条sql **不会** 返回 `CODE` 值为 `NULL`的记录：  

`SELECT * from hello_table where CODE!='C'`


正确的方式是这样：    

`SELECT * from hello_table where CODE IS NULL OR CODE!='C'`



参考
----
- http://stackoverflow.com/questions/9608639/mysql-comparison-with-null-value
- http://dev.mysql.com/doc/refman/5.7/en/working-with-null.html
