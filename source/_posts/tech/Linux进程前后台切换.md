title: Linux进程前后台切换
date: 2016-03-22 15:07:18
tags: Linux
categories: IT技术
---
Linux中前后台进程相关的命令：

        command &   // 将进程放在后台执行
        ctrl-z      // 暂停当前进程 并放入后台
        jobs        // 查看当前后台任务
        bg          // 将任务转为后台执行
        fg          // 将任务调回前台
        kill        // 杀掉任务

假设你发现前台运行的一个程序需要很长的时间，但是需要干其他的事情，你就可以用 Ctrl-Z ，挂起这个程序，然后可以看到系统提示：
[1]+ Stopped /root/bin/rsync.sh
然后我们可以把程序调度到后台执行：（bg 后面的数字为作业号）

###　bg 1
[1]+ /root/bin/rsync.sh &
用 jobs 命令查看正在运行的任务：

### jobs
[1]+ Running /root/bin/rsync.sh &
如果想把它调回到前台运行，可以用

### fg 1
/root/bin/rsync.sh
这样，你在控制台上就只能等待这个任务完成了。

## SSH关闭时，让进程在后台可靠运行
[Linux 技巧：让进程在后台可靠运行的几种方法](https://www.ibm.com/developerworks/cn/linux/l-cn-nohup/)
nohup 无疑是我们首先想到的办法。顾名思义，nohup 的用途就是让提交的命令忽略 hangup 信号。让我们先来看一下 nohup 的帮助信息：
NOHUP(1)                        User Commands                        NOHUP(1)

NAME
       nohup - run a command immune to hangups, with output to a non-tty

SYNOPSIS
       nohup COMMAND [ARG]...
       nohup OPTION

DESCRIPTION
       Run COMMAND, ignoring hangup signals.

       --help display this help and exit

       --version
              output version information and exit
可见，nohup 的使用是十分方便的，只需在要处理的命令前加上 nohup 即可，标准输出和标准错误缺省会被重定向到 nohup.out 文件中。一般我们可在结尾加上"&"来将命令同时放入后台运行，也可用">filename 2>&1"来更改缺省的重定向文件名。