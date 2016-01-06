title: Composer和Laravel的一些小技巧
date: 2015-12-21 16:35:58
tags: 快捷笔记
categories: IT技术
---

## Composer 两个小技巧

使用Composer以后，Laravel的开发效率提升了不止一点点

1. composer update foo/bar  // 更新单个库
1. composer update nothing  // 仅更新composer.lock
2. composer require "foo/bar:1.0.0"  // 无需编辑composer.json直接安装库  
2. composer dump-autoload --optimize  // 生产环境中优化自动加载，提升性能
3. composer config -g repo.packagist   // composer http://packagist.phpcomposer.com 设置国内镜像[参考地址](http://pkg.phpcomposer.com)