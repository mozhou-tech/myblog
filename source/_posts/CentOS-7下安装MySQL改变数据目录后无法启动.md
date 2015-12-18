title: CentOS 7下安装MySQL遇到的一些问题
date: 2015-12-18 09:16:49
tags: MySQL
categories: IT技术
---

部署环境：CentOS下安装MySQL5.6.28。一开始安装MySQL5.7.10也是遇到这个问题。

## 改变数据目录后无法启动

倒腾了一天，最后执行了一个软连接命令就解决了。至于原因到底是什么，还不清楚，但是这种方法解决了问题。

       ln -s /alidata/mysqldata mysql
       #ln -s 源目录 目录或连接名

## 数据转移

以前一直使用Navicat通过数据传输的方式转移或备份数据，但是今天转移数据到正式服时，一直报错并显示
       
       Data truncated for column `???` ??? ...
       
看起来Navicat把数据截断了，后来使用mysqldump转移成功
       
       mysqldump -u root qjiatrip > backup.sql
       #mysqldump -u 用户名 数据库名 > 备份名.sql
       
嗯，就是这样。
       