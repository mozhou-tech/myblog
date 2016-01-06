title: 来一掌O2O平台技术架构
date: 2015-12-04 17:00:35
tags:
categories: IT技术
---

来一掌CTO还是我人生路上还是比较重要的一个角色。留下技术笔记，供后来回忆，也给大家用来参考。

## 技术框架

后台：CentOS、Nginx、PHP、MySQL
前端：Angularjs
PHP framework：Laravel
选择前端框架的时候，纠结了好一整子，错过了ionicframework。后来发现企查查把这个基于Angularjs的框架用的很好，所以我在自己的另一个“灸法速查”项目中用了起来，效率还是挺高的。

## 说说Modern PHP
后来才知道更多人用的是PHP5.3以前的版本，当时花了很多时间找到这个Laravel框架，14年底刚刚开始在国内流行，但是在国外已经风生水气了。一个最大的好处是借鉴了Linux的包管理机制，在[packagist.org](http://packagist.org)可以找到大多数你需要开发，但是已经有人做好了的功能。所需要做的，就是把包名加入composer.json，执行php composer.phar update，然后参照文档编写。
如果你想更深入的了解Modern PHP，可以Star这个仓库：[https://github.com/laravel-china/php-the-right-way](https://github.com/laravel-china/php-the-right-way)。

## RESTful风格
前端与后端，所有的数据都是Ajax获取，这也造成了页面卡顿需要加载时间，或许引入缓加载可以减轻这个问题。这么做的好处是，在将来开发安卓和iOS端的时候，没必要再重新做一遍后端开发了。其实在年底的时候，已经发现大多数人采用了这种方式，也有人比我们优化的更好。
后来做一个SCM系统时，采用了传统的网页方式，RESTful有以下好处：
> 1. 减少查询次数，提升并发能力，提升访问速度
> 2. 将来可以与iOS和Android兼容
> 1. 简化后台数据存取逻辑，实际是转移到前端去了
> 1. 在结合Angularjs等前端MVVM框架的时候，实现但页面应用

## 基于系统可靠性的考虑
1. 使用事务管理
2. 定期的数据备份（每天一次系统镜像）

## 总结
整个系统没有太大的技术难点，要说比较麻烦的地方，就是时间块的管理吧。每个推拿师的可接单时间，都被划分成块存储在可用时间表里，这部分当时有点过度设计了，但是在做的时候，并不能搞清楚需要做成什么样子。