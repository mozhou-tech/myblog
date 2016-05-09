title: 用Weka进行数据挖掘
date: 2016-05-08 10:01:26
tags:
- 算法
- 机器学习
- 数据挖掘
- 软件
categories:
- 机器学习
---

Weka是由新西兰怀卡托大学用Java开发的数据挖掘常用软件。Weka限制在GNU通用公众证书的条件下发布，它几乎可以运行在所有操作系统平台上，包括Linux、Windows、OS X等。Weka非常适合初学者的工具，基于GUI的操作和数据集的可视化让学习和调参过程变得非常愉快。
![](/images/2016/weka_knowledgeflow.jpg)

### 名称->算法对应
functions ----  MultilayerPerceptron -> BP也叫多层前馈网络，而BP在weka中就是由算法实现的。
trees     ----  J48 -> 策略树
package timeseriesForecasting       -> 支持实现序列的处理

### 数据集可挖掘的意义验证
经过试验，使用策略树、神经网络等不同的模型对预测结果的影响并不是很大，仅相差几个点。对预测结果起决定性的因素，是自变量和因变量之间的相关性。假设预测的操作过程没有问题，测试的准确率高于随机结果，说明自变量和因变量之间存在关联。


