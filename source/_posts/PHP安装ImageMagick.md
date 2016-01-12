title: PHP安装ImageMagick
date: 2016-01-12 12:58:54
tags: 快速笔记
categories: IT技术
---

pecl安装PHP组件报错，

        Warning: Invalid argument supplied for foreach() in Command.php on line 259
        Warning: Invalid argument supplied for foreach() in Command.php on line 259

后来发现是php-pear安装版本错误，执行下列命令，删除原有旧版本的安装包，之后，结果如预期。

        yum erase php-pear
        yum install php56w-pear
        pecl install imagick
        
  
