title: Nodejs NPM的使用
date: 2016-01-05 09:11:59
tags: 快捷笔记
categories: IT技术
---

npm install b --save會幫你安裝並添加依赖

        npm config set strict-ssl false             //关闭npm的HTTPS
        npm config set registry "http://registry.npmjs.org/"    //设置npm的获取地址
        npm config set proxy=http://代理服务器ip:代理服务器端口 
        
        npm config delete http-proxy    // 清除npm代理
        npm config delete https-proxy

[淘宝NPM镜像](https://github.com/nimojs/blog/issues/20)