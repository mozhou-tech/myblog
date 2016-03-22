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