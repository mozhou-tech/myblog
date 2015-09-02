title: Git快捷操作笔记
date: 2015-09-02 21:50:07
tags: 快捷笔记
categories: IT技术
---

# 版本管理
版本回退到某一一次commits

    $ sudo -u apache git reset --hard 8d5e87c

测试SSH

    $ sudo -u apache ssh -vT git@bitbucket.org
    
## 分支管理

    $ git branch              //查看分支
    $ git branch  <name>      //创建分支
    $ git checkout  <name>    //切换分支
    $ git merge  <name>       //合并分支到当前分支
    $ git branch -d <name>    //删除分支   
         
[分支管理策略](http://www.ruanyifeng.com/blog/2012/07/git.html)         
     
# Hook 自动部署
[参考文档](http://overtrue.me/articles/2015/01/how-to-deploy-project-with-git-hook.html)