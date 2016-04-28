title: Python Package开发
date: 2016-03-18 17:08:24
tags:
- Python
categories: IT技术
---

今天在尝试开发Python Package的时候，总是Import Error，后来发现是终端找不到这个包，以下是解决方法：

首先需要使用sys.path.append方法将b.py所在目录加入到搜素目录中

        import sys 
        sys.path.append('c:\xxxx\b.py') # 这个例子针对 windows 用户来说的 

使用pth文件，在 site-packages 文件中创建 .pth文件，将模块的路径写进去，一行一个路径，以下是一个示例，pth文件也可以使用注释：

        # .pth file for the  my project
        E:\DjangoWord
        E:\DjangoWord\mysite
        E:\DjangoWord\mysite\polls