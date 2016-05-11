title: Bower常用命令
date: 2016-01-20 16:26:44
tags: 快捷笔记
categories: IT技术
---
1. 安装Bower

    npm install -g bower
    
1. 安装前端库   
   
    bower install <package>
    bower install PACKAGE --save  // 保存到bower.json
    
    bower init // 初始化bower.json
    
示例：    
   
    # registered package
    $ bower install jquery
    # GitHub shorthand
    $ bower install desandro/masonry
    # Git endpoint
    $ bower install git://github.com/user/package.git
    # URL
    $ bower install http://example.com/script.js

3. .bowerrc示例

    {
      "directory": "public/bower_components/",
      "analytics": false,
      "timeout": 120000,
      "registry": {
    
      }
    }