---
layout: page
title: Autonomous Driving
---

<p style="text-align:center">
	<img src="/topics/img/waymo.png" />
</p>


[Apollo自动驾驶工程师技能图谱V2.0](/topics/data/apollo-v2.pdf)

### 0. Basics

- [无人驾驶技术入门（十二）- 无人驾驶中的坐标转换](https://zhuanlan.zhihu.com/p/41263701)
- [无人驾驶技术入门（十三）- 手把手教你写卡尔曼滤波器](https://zhuanlan.zhihu.com/p/45238681)
- [无人驾驶技术入门（十八）- 手把手教你写扩展卡尔曼滤波器](https://zhuanlan.zhihu.com/p/63641680)


### 1. Overview

- Creating Autonomous Vechicle Systems (刘少山) [[Slide]](/topics/data/CreatingAutonomousVechicleSystems.pdf)
- DiDi: AI in Transportation (KDD2018 Tutorial) [[Slide]](/topics/data/DiDi_KDD2018_Tutorial.pdf)
- JD X-Lab: Artificial Intelligence in Autonomous Vehicle Systems [[Slide]](/topics/data/JD_AI_in_autonomous_vehicle_systems.pdf)

### 2. Prediction

- [自动驾驶公开课 - Apollo 2.5预测系统介绍](https://mp.weixin.qq.com/s/48DcWP1kAoze0Lv8jHY3Ow)
- Apollo3.5预测模块官方介绍[[中文]](https://github.com/ApolloAuto/apollo/blob/master/modules/prediction/README_cn.md)[[英文]](https://github.com/ApolloAuto/apollo/blob/master/modules/prediction/README.md)
- [【美团技术解析】自动驾驶中的障碍物行为预测](https://www.jiqizhixin.com/articles/2019-05-14-4?from=synced&keyword=%E8%87%AA%E5%8A%A8%E9%A9%BE%E9%A9%B6)


### 3. Planning and Control (PNC)

- [解析百度Apollo之决策规划模块](https://paul.pub/apollo-planning/#id-publicroadplanner)
- [直播回顾 - Apollo决策技术分享](https://mp.weixin.qq.com/s/KFjfhs5zdHdrukRnm52rsg)
	- [Slide](/topics/data/20190326-Apollo决策技术分享.pdf)
- [Apollo问答 - 如何拿下无人驾驶决策技术②](https://mp.weixin.qq.com/s/GvbOUg2LOnFTWZrXL7aQ2A)
- Apollo3.5规划模块官方介绍[[中文]](https://github.com/ApolloAuto/apollo/blob/master/modules/planning/README_cn.md)[[英文]](https://github.com/ApolloAuto/apollo/blob/master/modules/planning/README.md)
- [自动驾驶中有哪些路径规划框架?](https://zhuanlan.zhihu.com/p/43405664)
- [PythonRobotics: Python sample codes for robotics algorithms](https://atsushisakai.github.io/PythonRobotics/)

`相关分享`

- 自动驾驶大脑设计思路探析（智行者）[[Slide]](/topics/data/自动驾驶大脑设计思路探析.pdf)
- 智能车控制决策系统开发（智行者）[[Slide]](/topics/data/智能车控制决策系统开发.pdf)
- 同济大学：无人驾驶车辆行为决策系统研究（2018）[[Website]](https://mp.weixin.qq.com/s/PKez00qYG84I_61_74YUfQ) [[Paper]](/topics/data/2018-无人驾驶车辆行为决策系统研究.pdf)

`路径规划`

- [路径搜索可视化](http://qiao.github.io/PathFinding.js/visual/)
- [路径规划之 A* 算法](https://paul.pub/a-star-algorithm/#id-%E7%AE%97%E6%B3%95%E5%8F%98%E7%A7%8D)
- [Introduction to the A* Algorithm](https://www.redblobgames.com/pathfinding/a-star/introduction.html)
- Baidu Apollo EM Motion Planner[[Paper-18年发表]](https://arxiv.org/pdf/1807.08048.pdf)

`企业招聘要求`

- [Waymo: Software / Research Engineer, Planning and Motion Control](https://waymo.com/joinus/1305655/)
- [Waymo: Software Engineer, Planner & Controls](https://waymo.com/joinus/928478/)
- [文远知行：决策规划工程师 - ML/DL方向](https://app.mokahr.com/apply/jingchi/2138#/job/d2455c6c-8f2a-4c39-b2ff-e20fdd552836?_k=qxytrx)

### 4. 运行时的计算框架

要解决的问题：不同模块之间如何进行通信？

在自动驾驶领域，ROS存在的挑战：

- 第一，在ROS中，计算任务都会执行在一个一个线程中，当系统中存在大量计算任务的时候，会衍生出大量的线程，对调度系统而言是一个非常大的负担，会引入很多的线程切换，导致系统的实时性难以保障。
- 第二，分布式系统的通信性能瓶颈很大。分布式架构通信性能、中心化的Master、消息格式不够灵活等问题导致调度难以满足实际需求。

Apollo3.5之前的版本（1.0-3.0）采用ROS系统，并针对无人车的要求对ROS系统进行了改进，主要包括下面三个方面：

- 通信性能优化
	- 通过共享内存来减少数据拷贝，以提升通信性能
- 去中心化网络拓扑
	- 主要解决ROS中只包含单主节点的问题（单主节点发生故障后容易导致系统崩溃）
	- 使用RTPS（Real-Time Publish-Subscribe）服务发现协议实现完全的P2P网络拓扑
- 数据兼容性扩展
	- 不使用ROS用来描述文件定义模块间的消息接口msg
	- 改用Google的Protocol Buffers格式数据

ROS在自动驾驶的探索和实践 [[Blog]](https://mp.weixin.qq.com/s?__biz=MzI5MjcyNTc1Mw==&mid=2247483975&idx=1&sn=7d946e3322710d7b7b1e6688c37f8f43&chksm=ec7db4d1db0a3dc7eda3e26ea35945da9aebaee32cbe28f91c5b8b9fc589fbec284887e1bc18&scene=21#wechat_redirect) [[Slide]](/topics/data/ROS在自动驾驶的探索和实践.pdf)

Apollo3.5之后采用百度自家设计的Apollo Cyber RT系统

- [百度Apollo 3.5是如何设计Cyber RT计算框架的？(2019.02.02)](https://mp.weixin.qq.com/s/YKmn_oJFheq17hs8M2zkMw)
- [让Cyber RT触手可及 专场问答第二弹！(2019.03.08)](https://mp.weixin.qq.com/s/g6Zc7szKfWn9wdZIPJpkSA)
- [技术文档 - Cyber RT 协程技术解读 (2019.04.08)](https://mp.weixin.qq.com/s/6LdFTZrTiRZfF_gv1NJhzg)
- [技术文档 - Apollo Cyber调度器 (2019.04.16)](https://mp.weixin.qq.com/s/uRmNDmpUiPC7pRykR3zBeg)
- [技术文档 - Cyber RT 进程间通信 (2019.04.22)](https://mp.weixin.qq.com/s/aL5T1HIlr2rNBrNOX4Xbjw)
- [沙龙回顾 - Apollo Cyber RT计算框架详解 (2019.05.16)](https://mp.weixin.qq.com/s/d4sLuJFiyFyL6NRhyx-i8A)

### 5. 端到端方法（从感知到控制）

`相关博文`

- [【美团技术解析】无人车端到端驾驶模型概述](https://mp.weixin.qq.com/s/5yH8aXDrPYjGJdv0npHkig)

`相关论文`

* 2015 - Princeton - ICCV - DeepDriving：Learning Affordance for Direct Perception in Autonomous Driving
* 2017 - Berkeley - CVPR - End-to-end Learning of Driving Models from Large-scale Video Datasets
* 2018 - Intel - ICRA - End-to-end  Driving  via  Conditional  Imitation  Learning
* 2015 - NYU - DAVE_Off-Road Obstacle Avoidance through End-to-End Learning
* 2016 - Comma.ai - Learning a Driving Simulator
* 2016 - Nvidia - End to End Learning for Self-Driving Cars
* 2018 - Intel - Learning End-to-end Autonomous Driving using Guided Auxiliary Supervision 

### 6. 基于学习的方法（PNC方面）

### 7. Apollo项目

`Apollo3.5整体架构：`

<p style="text-align:center">
	<img src="/topics/img/apollo/apollo_3_5_Architecture.png" />
</p>

`硬件架构：`

<p style="text-align:center">
	<img src="/topics/img/apollo/apollo_ardware_overview_3_5.png" />
</p>

`硬件之间的数据流：`

<p style="text-align:center">
	<img src="/topics/img/apollo/apollo_hardware_connection_3_5_1.png" />
</p>

`软件架构（导航模式）：`

<p style="text-align:center">
	<img src="/topics/img/apollo/apollo_3_5_software_architecture.png" />
</p>

`模块的官方说明：`

- [Perception（感知）](https://github.com/ApolloAuto/apollo/tree/master/modules/perception)
- [Prediction（预测）](hhttps://github.com/ApolloAuto/apollo/tree/master/modules/prediction)
- [Routing（路由）](https://github.com/ApolloAuto/apollo/tree/master/modules/routing)
- [Planing（计划）](https://github.com/ApolloAuto/apollo/tree/master/modules/planning)
- [Control（控制）](https://github.com/ApolloAuto/apollo/tree/master/modules/control)

`相关博文：`

- [解析百度Apollo自动驾驶平台](https://paul.pub/baidu-apollo/#id-prediction%E9%A2%84%E6%B5%8B)
- [技术文档 - Apollo 3.5学习指南高能上线，先睹为快！](https://mp.weixin.qq.com/s/0VHpdAi1PiHsj6DbdvcwvQ)
- [技术文档 - Apollo3.5 软件架构](https://mp.weixin.qq.com/s/k5GNHhxEE6mIOnxXlCpKXg)
- [沙龙回顾 - Apollo 3.5 技术架构详解](https://mp.weixin.qq.com/s/svcCQHIcQFIx-AifvbrP9Q)
- [沙龙回顾 - Apollo障碍物感知5大板块，一文揭秘](https://mp.weixin.qq.com/s/NlTw6TEQ9oMyxRDohlKSQw)
- [开发者说 - Apollo代码学习—模型预测控制（MPC)](https://mp.weixin.qq.com/s/UAPbNq_KNWCFd7p8U8HnYQ)
- [开发者说 - Apollo代码学习—MPC与LQR比较](https://mp.weixin.qq.com/s/BFNaEBa8KwvRBK_mSunXjw)
- [开发者说 - Apollo控制算法之LQR](https://mp.weixin.qq.com/s/WbTtBjeUmBeS3OQgaFG4eA)
- [技术文档 - 二次规划（QP）样条路径](https://mp.weixin.qq.com/s/Ofn-p8NnnO4kLYqTlL0bJg)


### 8. 相关课程

`Apollo自动驾驶入门课程`

* [重磅 - Udacity X Apollo自动驾驶免费入门课程正式上线！](https://mp.weixin.qq.com/s/h_4EACy8rxW4yR1dkGvDRw)
* [Apollo自动驾驶入门课程第①讲—无人驾驶概览](https://mp.weixin.qq.com/s/yO_Lc5Fo-8fBC9PwVCQBqA)
* [Apollo自动驾驶入门课程第②讲 — 高精地图](https://mp.weixin.qq.com/s/IVD0aq8V-qZoB0tcLMigYw)
* [Apollo自动驾驶入门课程第③讲 — 定位](https://mp.weixin.qq.com/s/KJbm4wfsTLxT5LGR7GV_SA)
* [Apollo自动驾驶入门课程第④讲 — 感知（上）](https://mp.weixin.qq.com/s?__biz=MzI1NjkxOTMyNQ==&mid=2247485321&idx=1&sn=6644ab23e2a733d3ea25f6c4e6052478&chksm=ea1e15fbdd699ced66598e976910f9e870ac8209cb6c14ba8d184939529be046c4ee65534589&mpshare=1&scene=1&srcid=0903hY3xRJhpDGQhIuduVdmf#rd)
* [Apollo自动驾驶入门课程第⑤讲 — 感知（下）](https://mp.weixin.qq.com/s/FqW2X9LJZvNe9efllAYhTQ)
* [Apollo自动驾驶入门课程第⑥讲 — 预测](https://mp.weixin.qq.com/s/6ro9y69h-6yHZ7MfodxUHQ)
* [Apollo自动驾驶入门课程第⑦讲 — 规划（上）](https://mp.weixin.qq.com/s/ZBHKDtnaEI9sVCfEfeeUlQ)
* [Apollo自动驾驶入门课程第⑧讲 — 规划（下）](https://mp.weixin.qq.com/s/1yA-kgS_rL4o9I4OWeI4-A)
* [Apollo自动驾驶入门课程第⑨讲 — 控制（上）](https://mp.weixin.qq.com/s/8hLVHuv635fyHRNftXJQ4w)
* [Apollo自动驾驶入门课程第⑩讲 — 控制（下）](https://mp.weixin.qq.com/s/AnWWnD3ScSW6GhrwRGpRDw)

`Apollo自动驾驶进阶课程`

`MIT 6.S094: Deep Learning for Self-Driving Car`

- [HomePage](https://selfdrivingcars.mit.edu/)








