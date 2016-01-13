title: Hexo快捷操作笔记
date: 2015-09-02 21:49:48
tags: 快捷笔记
categories: IT技术
---

[Hexo中文文档](https://hexo.io/zh-cn/docs/)
# 服务器和部署
## 本地
启动服务器，指定IP地址。同时watch监视文档更新

    $ hexo server -i 127.0.0.1 -p 8000
    
## 部署
部署至Github

    $ hexo d -g
等同于

    $ hexo generate
    $ hexo deploy
## 写作

    $ hexo new [layout] <title>
    
