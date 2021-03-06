title: TeamManager
date: 2016/01/07 06:04:38
categories:
 - tryghost

tags:
 - manage 



---

## 管理方面书籍

* [技术管理之巅——如何从零打造高质效互联网技术团队？]
* [一网打尽]
* [互联网时代的软件革命-SaaS架构设计]
* [30天软件开发：告别瀑布拥抱敏捷]


## 管理方法

 * 狼群管理/末位淘汰制/KPI绩效制度
<br/>基本上都是说的同一个东西, 讲白了就是wow里面下副本的时候用的那种... 大部分对团队激励还是蛮大的, 但是也会有创伤,不够人性.

 * 看板管理
<br/>日本人发明的..尊重守时的完成可持续交付

 * 敏捷开发

![](http://img.sandseasoft.com/image/e/72/5e1bb2f1b6062695527fa0c38029f.jpg)
idea

 1. 人的自律 scrum
 2. 团队透明化
 3. 每天站立会议， sprint启动会议，结束会议，下个sprint的预估，上个sprint的总结
 3. 3-9人的小组
 4. 最少14天最多30天为一个增量周期的sprint
 5. 一功能为单位的，迭代增量开发，降低模块开发之间的关联性，每次发布都有可用功能演示
 6. 不要技术债务
 7. 周报日报,个人计划透明,团队正向
 8. 学会分享,团队分享氛围越好,成长越快,抱团越紧

看到别的评论摘抄
以下是书中一些观点信息的摘抄：

1：Nokia总结出的迭代开发的基本要求：
1.1：迭代要有固定时长，不能超过六个星期；
1.2：在每一次迭代的结尾，代码都必须经过QA的测试，能够正常工作；

2：Nokia的Scurm标准：
2.1：Scurm团队必须要有产品负责人，而且团队都清楚这个人是谁；
2.2：产品负责人必须要有产品backlog，其中包括团队对它进行的估算；
2.3：团队必须要有燃尽图，而且要了解他们自己的生产率；
2.4：在一个sprint中，外人不能干涉团队的工作；

3：产品负责人之外的人也可以向产品backlog中添加故事，但是他们不能说这个故事有多重要，这是产品负责人独有的权利。他们也不能添加时间估算，这是开发团队独有的权利；

4：我尽力把内部质量和外部质量分开。
4.1：外部质量是系统用户可以感知的。运行缓慢、让人迷糊的用户界面就属于外部质量低劣；
4.2：内部质量一般指用户看不到的要素，它们对系统的可维护性有深远影响。可维护性包括系统设计的一致性、测试覆盖率、代码可读性和重构等等；

5：经验告诉我，牺牲内部质量是一个糟糕透顶的想法。现在节省下来一点时间，接下来的日子里你就要一直为它付出代价。一旦我们放松要求，允许代码库中暗藏问题，后面就很难恢复质量了；

6：为了调整不同的人对故事的工作量的估算的差异，我们采用了计划扑克方法：每个人独立估算工作量，然后公开，差异比较大的成员互相沟通直至时间估算趋于一致；

7：故事是可以交付的东西，是产品负责人所关心的。任务是不可交付的东西，产品负责人对它也不关心；

8：产品负责人往往不能对技术故事的优先级作出正确的权衡；

9：只要让团队坐到一起，就会有立竿见影的成效。过上一个sprint，团队就会认为挪到一起是绝妙的主意。“一起”具有以下含义：互相听到，互相看到，相对独立（团队突然开始激烈讨论，不会影响团队外的任何人）；

10：我们的目标是在每个sprint之间安排一个实验日（这一天员工可以干任何想干的事情），目前实际执行的是每个月有一个实验日，放在每个月的第一个星期五；

11：TDD（测试驱动开发）很难，但是在一开始没有用TDD进行构建的代码库上实施TDD……则是难上加难！

12：如果你深陷手工回归测试的泥潭，打算让它自动化执行，最好还是放弃吧。首先还是应该想办法简化手工回归测试，然后再考虑将真正的测试变成自动化执行；

13：我的经验是：宁可团队数量少，人数多，也比弄上一大堆总在互相干扰的小团队强。要想拆分小团队，必须确保他们彼此之间不会产生互相干扰；

14：我们在实施Scrum的时候，所做的第一件事情就是打乱基于组件的团队，创建跨组件的团队。它减少了诸如“我们没法完成这个任务，因为我们在等服务器那帮家伙完成他们的工作”之类的情况发生；

15：“团队凝聚力”是Scrum的核心要素之一，如果一个团队合作工作达多个sprint之久，他们就会变得非常紧密。他们会学会如何达成团队涌流（group flow），生产力会提升至难以置信的地步。


## 马斯洛需求层次理论

![](http://img.sandseasoft.com/image/0/01/778897be182ea714c2d0cb2d748cb.jpg)



## 视频
  哈佛大学公开课：领袖心理学
  http://open.163.com/special/opencourse/psychologyofleadership.html

## 技术等级
### 中级
* 了解maven/git/基础算法
* 对 SOA服务有了解（如 dubbo）
* 对 linux 基础操作有了解
* 对 java 并发编程相关上层 api 了解
* 工作2-5年，本科生
* 假想目标薪资8k-14k

### 高级
* 了解阿里云各种组件
* 了解云架构运维安全
* 了解分布式日志运维框架
* 了解分布式服务框架
* 熟悉 nginx 
* 假想目标薪资13k+


## 面试问题
### 构建工具
1. Git 使用
2. IDEA 使用
3. MAVEN 使用

### Spring/Mybatis/Druid 使用
1. ApplicationContext
2. Mybatis、Hibernate 区别
3. Druid 和 C3P0 区别

### Java current包
1. 队列工具有哪些？具体场景？
2. Threadlocal使用场景

### 数据库 
1. slowsql 怎么出现的，如何调试修复
2. 为什么要使用PreparedStatement接口，SQl 注入如何产生的
3. 事务、ACID、DML、DDL、索引优化

### 算法  
1. 冒泡排序、斐波拉契数列

### 中间件
1. 了解 dubbo
2. 听说过哪些 队列中间件
3. 听说过哪些 NoSQl
4. 听说过哪些 搜索引擎






