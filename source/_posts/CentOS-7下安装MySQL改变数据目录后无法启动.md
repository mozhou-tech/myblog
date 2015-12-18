title: CentOS 7下安装MySQL改变数据目录后无法启动
date: 2015-12-18 09:16:49
tags: MySQL
categories: IT技术
---

部署环境：CentOS下安装MySQL5.6.28。一开始安装MySQL5.7.10也是遇到这个问题。

倒腾了一天，最后执行了一个软连接命令就解决了。至于原因到底是什么，还不清楚，但是这种方法解决了问题。

       ln -s /alidata/mysqldata mysql
       #ln -s 源目录 目录或连接名

嗯，就是这样。
       