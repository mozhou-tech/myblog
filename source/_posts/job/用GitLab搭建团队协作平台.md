title: 用GitLab搭建团队协作平台
date: 2017-06-21 23:13:51
tags:
categories:
---
在这之前，公司的项目代码都放在Bitbucket，但随着团队人数的增加，Bitbucket每个项目5个人的免费额度很快就不够用了，于是打起了GitLab的主意。
搭建的过程还算简单，在阿里云购买了一台双核4G的云主机，使用官方提供的[Omnibus package](https://about.gitlab.com/installation/)很快就装好了。最早使用的是单核，但操作是卡的不行。迁移过程中，有这样几个要点：
1. 购买2核以上的主机，否则会卡的没法用
1. GitLab支持Bitbucket、Github、自建Git仓库的迁移
1. 我基于访问权限，把项目放到apple、cucumber、tomato等几个members，以求保持项目一定的保密性
### 里程碑 & issue
目前，我们采用里程碑制定版本计划，issue的提出是跟着版本计划走的。issue的种类包括：
1. Bug（约占80%以上）
1. 改进意见（约占10%）
1. 需求（约占10%）
提出的issue必须在当前的里程碑关闭之前解决，在未来，绩效的考核会与issue挂钩。因为在以OKRs作为内部考核制度的研发团队中，issue可以看做最小单位的"Key Results"。
### Pull Requests
"Merge Request"在代码审查工作中可以起到重要作用，但具体的用法还在研究中，待更...


