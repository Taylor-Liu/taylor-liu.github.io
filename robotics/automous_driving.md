---
layout: page
title: Autonomous Driving
---

<p style="text-align:center">
	<img src="/topics/img/waymo.jpg" />
</p>

### Content
	
1. Basics
2. Overview
3. Prediction
4. Planning and Control (PNC)
5. 运行时的计算框架
6. 端到端方法（从感知到控制）
7. 基于强化学习的方法（在PNC方面）
8. Apollo项目
9. 相关课程
10. 个人成长经验分享
11. 硬件
12. 仿真
13. 商业落地
14. 观点
15. 相关实验室
16. 期刊/会议（智能车领域）
17. 数据集
18. Pony.ai技术分享
19. 安全报告
20. 其它

### 前沿进展

- Waymo
	- CVPR2019发布大型自动驾驶数据库 [[机器之心报道]](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650764187&idx=4&sn=14995d261c92df057db1b2ce3ce6aa9f&chksm=871ab7e5b06d3ef360b3f148b216c36972c890fe2260417be8a3f8896c8ddfafe529d9714cf0&mpshare=1&scene=1&srcid=#rd)


[Apollo自动驾驶工程师技能图谱V2.0](/topics/data/apollo-v2.pdf)

### 1. Basics

- [无人驾驶技术入门（十二）- 无人驾驶中的坐标转换](https://zhuanlan.zhihu.com/p/41263701)
- [无人驾驶技术入门（十三）- 手把手教你写卡尔曼滤波器](https://zhuanlan.zhihu.com/p/45238681)
- [无人驾驶技术入门（十八）- 手把手教你写扩展卡尔曼滤波器](https://zhuanlan.zhihu.com/p/63641680)

### 2. Overview

- Creating Autonomous Vechicle Systems (刘少山) [[Slide]](/topics/data/CreatingAutonomousVechicleSystems.pdf) [[雷锋网报道]](https://www.leiphone.com/news/201707/Os8tY7kc6SOfnBmC.html)
- DiDi: AI in Transportation (KDD2018 Tutorial) [[Slide]](/topics/data/DiDi_KDD2018_Tutorial.pdf)
- JD X-Lab: Artificial Intelligence in Autonomous Vehicle Systems [[Slide]](/topics/data/JD_AI_in_autonomous_vehicle_systems.pdf)

`相关博文`

- [自动驾驶之路已走了多远？一文读懂研究现状](https://mp.weixin.qq.com/s/1Lj6DaY5m-sWb-Y7lnLeEw)
	- 编译自2019年论文 Self-Driving Cars: A Survey [[Paper]](https://arxiv.org/abs/1901.04407)
- [一个自动驾驶工程师眼中的自动驾驶](https://mp.weixin.qq.com/s/cgWJvhn6mclsKOv0gvaUcg)
- [自动驾驶传感器，感知，地图定位和规划控制发展现状及热点研究](https://mp.weixin.qq.com/s/qyZS6ufN6f4dQRdG9diP0A)
- [史上最全的自动驾驶研究报告（上）](https://mp.weixin.qq.com/s/fG_Oee0biudXyX-B-93THw)
- [史上最全的自动驾驶研究报告（下）](https://mp.weixin.qq.com/s/Qe6ex06SFbI1ggq9ONZYFA)

### 3. Prediction

- [自动驾驶公开课 - Apollo 2.5预测系统介绍](https://mp.weixin.qq.com/s/48DcWP1kAoze0Lv8jHY3Ow)
- Apollo3.5预测模块官方介绍[[中文]](https://github.com/ApolloAuto/apollo/blob/master/modules/prediction/README_cn.md)[[英文]](https://github.com/ApolloAuto/apollo/blob/master/modules/prediction/README.md)
- [【美团技术解析】自动驾驶中的障碍物行为预测](https://www.jiqizhixin.com/articles/2019-05-14-4?from=synced&keyword=%E8%87%AA%E5%8A%A8%E9%A9%BE%E9%A9%B6)
- [自动驾驶中行为预测的一些根本问题和最新方法](https://mp.weixin.qq.com/s/NH09Pvh8vKtOGrS6Lwq3Tw)
	- 作者简介：战威，UC Berkeley博士在读，主要研究方向为自动驾驶中的预测、决策与规划
- [自动驾驶中的驾驶行为建模和预测方法](https://mp.weixin.qq.com/s/FmqMg-j-Mf2nguHbuCyXAA)


### 4. Planning and Control (PNC)

- [Apollo 轨迹规划技术分享](https://mp.weixin.qq.com/s/ao5hC_3A7fn8_L_PFw399A)
	- [轨迹规划中的关键问题汇总1](https://mp.weixin.qq.com/s/C189dqfNOwuDW1MoHepmBQ)
	- [轨迹规划中的关键问题汇总2](https://mp.weixin.qq.com/s/alszWkfOChC1CydTDgWg5g)
- [解析百度Apollo之决策规划模块](https://paul.pub/apollo-planning/#id-publicroadplanner)
- [直播回顾 - Apollo决策技术分享](https://mp.weixin.qq.com/s/KFjfhs5zdHdrukRnm52rsg)
	- [Slide](/topics/data/20190326-Apollo决策技术分享.pdf)
- [Apollo问答 - 如何拿下无人驾驶决策技术②](https://mp.weixin.qq.com/s/GvbOUg2LOnFTWZrXL7aQ2A)
- Apollo3.5规划模块官方介绍[[中文]](https://github.com/ApolloAuto/apollo/blob/master/modules/planning/README_cn.md)[[英文]](https://github.com/ApolloAuto/apollo/blob/master/modules/planning/README.md)
- [自动驾驶中有哪些路径规划框架?](https://zhuanlan.zhihu.com/p/43405664)
- [PythonRobotics: Python sample codes for robotics algorithms](https://atsushisakai.github.io/PythonRobotics/)

- [Antonin RAFFIN: Learning to Drive Smoothly in Minutes (June 27, 2019)](https://towardsdatascience.com/learning-to-drive-smoothly-in-minutes-450a7cdb35f4)

`相关分享`

- 自动驾驶大脑设计思路探析（智行者）[[Slide]](/topics/data/自动驾驶大脑设计思路探析.pdf)
- 智能车控制决策系统开发（智行者）[[Slide]](/topics/data/智能车控制决策系统开发.pdf) [[雷锋网报道]](https://www.leiphone.com/news/201701/pCFzcs7O9UDn2ETl.html)
- 同济大学：无人驾驶车辆行为决策系统研究（2018）[[Website]](https://mp.weixin.qq.com/s/PKez00qYG84I_61_74YUfQ) [[Paper]](/topics/data/2018-无人驾驶车辆行为决策系统研究.pdf)
- 自动驾驶的“大脑”——决策规划篇 [[Website]](https://mp.weixin.qq.com/s/P-PR5CSDE0zKOUwXebN3xw)
	- 选自《中国人工智能系列白皮书-智能驾驶2017》[[PDF]](/topics/data/2017-中国人工智能系列白皮书-智能驾驶.pdf)
- 自动驾驶汽车的运动规划技术综述 [[Website]](https://mp.weixin.qq.com/s/BmpjnNMvpOywjPxt30p0bw)
	- 2016 - A Review of Motion Planning Techniques for Automated Vehicles
- 算法 - 一篇读懂自动驾驶汽车决策层算法的新思路 [[Website]](https://mp.weixin.qq.com/s/4chZ52I3Qy34GmEqtDpHfw)
- 自动驾驶中轨迹规划的探索和挑战 [[Website]](https://mp.weixin.qq.com/s/1QXdFuppw1I3PkD5LV9kcg)
	- 作者：Pony.ai Tech lead 梁亚雄
- 【美团无人配送】自动驾驶中的决策规划算法概述 [[Website]](https://mp.weixin.qq.com/s/oNHDzdxMy_ciAok79kLDYg)
- 『无人驾驶』运动规划与运动控制（知乎专栏）[[Website]](https://zhuanlan.zhihu.com/c_1090991479136346112)

`路径规划`

- [路径搜索可视化](http://qiao.github.io/PathFinding.js/visual/)
- [路径规划之 A* 算法](https://paul.pub/a-star-algorithm/#id-%E7%AE%97%E6%B3%95%E5%8F%98%E7%A7%8D)
- [Introduction to the A* Algorithm](https://www.redblobgames.com/pathfinding/a-star/introduction.html)
- Baidu Apollo EM Motion Planner[[Paper-18年发表]](https://arxiv.org/pdf/1807.08048.pdf)

`企业招聘要求`

- [Waymo: Software / Research Engineer, Planning and Motion Control](https://waymo.com/joinus/1305655/)
- [Waymo: Software Engineer, Planner & Controls](https://waymo.com/joinus/928478/)
- [文远知行：决策规划工程师 - ML/DL方向](https://app.mokahr.com/apply/jingchi/2138#/job/d2455c6c-8f2a-4c39-b2ff-e20fdd552836?_k=qxytrx)

### 5. 运行时的计算框架

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

Cruise Automation：基于ROS构建无人驾驶汽车的经验总结 (ROSCon2018 Talk) [[Blog]](https://mp.weixin.qq.com/s/zXTAQd5JUtLPUW0xYr0qgA) [[Slide]](https://roscon.ros.org/2018/presentations/ROSCon2018_LessonsLearnedSelfDriving.pdf) [[Video]](https://vimeo.com/292693011)

Apollo3.5之后采用百度自家设计的Apollo Cyber RT系统

- [百度Apollo 3.5是如何设计Cyber RT计算框架的？(2019.02.02)](https://mp.weixin.qq.com/s/YKmn_oJFheq17hs8M2zkMw)
- [让Cyber RT触手可及 专场问答第二弹！(2019.03.08)](https://mp.weixin.qq.com/s/g6Zc7szKfWn9wdZIPJpkSA)
- [技术文档 - Cyber RT 协程技术解读 (2019.04.08)](https://mp.weixin.qq.com/s/6LdFTZrTiRZfF_gv1NJhzg)
- [技术文档 - Apollo Cyber调度器 (2019.04.16)](https://mp.weixin.qq.com/s/uRmNDmpUiPC7pRykR3zBeg)
- [技术文档 - Cyber RT 进程间通信 (2019.04.22)](https://mp.weixin.qq.com/s/aL5T1HIlr2rNBrNOX4Xbjw)
- [沙龙回顾 - Apollo Cyber RT计算框架详解 (2019.05.16)](https://mp.weixin.qq.com/s/d4sLuJFiyFyL6NRhyx-i8A)

### 6. 端到端方法（从感知到控制）

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

2018 - Waymo - ChauffeurNet: Learning to Drive by Imitating the Best and Synthesizing the Worst
- 不是完全的端到端模型
- [Waymo找到了无人车运动规划的新方法！机器学习模型还有巨大潜力](https://mp.weixin.qq.com/s/6cx4SiwNkDTd12lPIBPUaw)
- [谷歌ChauffeurNet:训练能够鲁棒地驾驶实车的网络](https://mp.weixin.qq.com/s/enUyu6nJI5olRUQehmu6UA)

### 7. 基于强化学习的方法（在PNC方面）

- [对抗强化学习最新研究：可用于自动驾驶汽车「碰撞避免机制」检测](https://mp.weixin.qq.com/s/dx2zbPN4ZIUCUHbIXhjAKg)
- [IEEE IV 2018：基于深度增强学习的高层驾驶决策研究](https://mp.weixin.qq.com/s/ODFKIIS5Z-WA2gDXxO1z9A)
- [Wayve：强化学习教汽车学会自动驾驶](https://mp.weixin.qq.com/s/ky8qsOlO--DzMQKd9fX-5Q)
- [知乎：强化学习在自动驾驶上有哪些应用？](https://www.zhihu.com/question/299700072?utm_source=wechat_search&utm_medium=organic)
- [深度强化学习在自动驾驶技术中的应用](https://mp.weixin.qq.com/s/SVR_P8dj-G68Aq5PN-FkcA) 
	- [[Slide]](/topics/data/2018-深度强化学习在自动驾驶技术中的应用.pdf)
- [伯克利新研究：在人类司机中引入10%自动驾驶车，车流量提升超3成](https://mp.weixin.qq.com/s/4io4E4iobNtVWEO52e1Wng)
	- [[BAIR Blog]](https://bair.berkeley.edu/blog/2019/06/03/benchmarks/)

- Flow [HomePage](https://flow-project.github.io/usingFlow.html)
	- Flow is a deep reinforcement learning framework for mixed autonomy traffic. Flow is a traffic control benchmarking framework and it provides a suite of traffic control scenarios (benchmarks), tools for designing custom traffic scenarios, and integration with deep reinforcement learning and traffic microsimulation libraries.

- [面试题：如何设计一个端到端的自动驾驶模型？ & 如何设计一个基于增强学习的自动驾驶决策系统？](https://mp.weixin.qq.com/s/7mu-n13H2YxbCFrVJ0fD1A)

### 8. Apollo项目

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

- [终极解析：“唤醒万物”的Apollo5.0来了！](https://mp.weixin.qq.com/s/s7uf-99MX95fTXE1CC_X4Q)


### 9. 相关课程

`MIT 6.S094: Deep Learning for Self-Driving Car`

- [HomePage](https://selfdrivingcars.mit.edu/)

`DALI 2018 Workshop on Autonomous Driving`

- [Homepage](http://dalimeeting.org/dali2018/autonomous-driving.html)

`Apollo自动驾驶入门课程`

* [重磅 - Udacity X Apollo自动驾驶免费入门课程正式上线！](https://mp.weixin.qq.com/s/h_4EACy8rxW4yR1dkGvDRw)
* [Apollo自动驾驶入门课程第①讲 — 无人驾驶概览](https://mp.weixin.qq.com/s/yO_Lc5Fo-8fBC9PwVCQBqA)
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

- [Apollo首个自动驾驶进阶课程正式上线！](https://mp.weixin.qq.com/s/FgnBhOEPS9-_uY1dH4VddQ)

- [进阶课程① - 带你纵览无人车](https://mp.weixin.qq.com/s/VR8E_kggbh_GSN_QNOM8PQ)

- [进阶课程② - 开源模块讲解（上）](https://mp.weixin.qq.com/s/VFGZGn6GEk7mml6cG4rE4A)
- [进阶课程③ - 开源模块讲解（中）](https://mp.weixin.qq.com/s/hwOXegnHFfNPFT8iEj9DDw)
- [进阶课程④ - 开源模块讲解（下）](https://mp.weixin.qq.com/s/r1hVVdfXZISnbrV3zYruYQ)

- [进阶课程⑤ - Apollo硬件开发平台介绍](https://mp.weixin.qq.com/s/why3vtC8hseM7TEN92ALLw)

- [进阶课程⑥ - 高精地图与自动驾驶的关系](https://mp.weixin.qq.com/s/6aK-jZInb254D8o2_07a8Q)
- [进阶课程⑦ - 高精地图的采集与生产](https://mp.weixin.qq.com/s/8Gk5_OAVUT0vuPr4ZOgAJw)
- [进阶课程⑧ - 高精地图的格式规范](https://mp.weixin.qq.com/s/mlXyNHn0ts_tA8L-8rf1oQ)
- [进阶课程⑨ - 业界的高精地图产品](https://mp.weixin.qq.com/s/46D_H4rpisAg0y6VmZJ3gQ)
- [进阶课程⑩ - Apollo地图采集方案](https://mp.weixin.qq.com/s/vqkv5y6XdXlKR7jefJIcOA)
- [进阶课程⑪ - Apollo地图生产技术](https://mp.weixin.qq.com/s/OlqKMDHiXAmB_3A9BR5Jdw)
- [进阶课程⑫ - Apollo高精地图](https://mp.weixin.qq.com/s/X2PgTQIjvpgQQ1YOyXe7eQ)

- [进阶课程⑬ - Apollo无人车自定位技术入门](https://mp.weixin.qq.com/s/eOxle3q_QgejlX10kc30Rg)
- [进阶课程⑭ - Apollo自动定位技术——三维几何变换和坐标系介绍](https://mp.weixin.qq.com/s/8n_o83A-5AjG3YCPG4FOgA)
- [进阶课程⑮ - Apollo自动定位技术详解—百度无人车定位技术](https://mp.weixin.qq.com/s/UokP3urHU8c5Nn0BT-F_BQ)

- [进阶课程⑯ - Apollo感知之旅——感知概貌](https://mp.weixin.qq.com/s/PJKv_RieG2yXil0E1oefPA)
- [进阶课程⑰ - Apollo感知之旅——传感器选择和安装](https://mp.weixin.qq.com/s/NbloG2p98VTkytCqhIVJeQ)
- [进阶课程⑱ - Apollo感知之旅——传感器标定](https://mp.weixin.qq.com/s/lVtZ_tWaMghMvkpYvRAEmQ)
- [进阶课程⑲ - Apollo感知之旅——感知算法](https://mp.weixin.qq.com/s/g8Y83vhw-OORm0CJElwPEA)
- [进阶课程⑳ - Apollo感知之旅——机器学习与感知的未来](https://mp.weixin.qq.com/s/E7t0M9MSxNG8nMWpUIjsJA)

- [进阶课程㉑ - Apollo规划技术详解——Basic Motion Planning and Overview](https://mp.weixin.qq.com/s/_4P_eEZzxj87sv5MALDM-A)
- [进阶课程㉒ - Apollo规划技术详解——Motion Planning with Autonomous Driving](https://mp.weixin.qq.com/s/HyacYh2FcGPW4-8SOECCtA)
- [进阶课程㉓ - Apollo规划技术详解——Motion Planning with Environment](https://mp.weixin.qq.com/s/yOmLYRyUji-Hvk2hObpDvw)
- [进阶课程㉔ - Apollo规划技术详解——Motion Planning Environment](https://mp.weixin.qq.com/s/vSa5KSSj_B_2YFNvZuaygQ)
- [进阶课程㉕ - Apollo规划技术详解——Optimization Inside Motion Planning](https://mp.weixin.qq.com/s/3GFCpjakIvpLu8cse_euUg)

`知乎专栏：无人驾驶干货铺`

- [主页](https://zhuanlan.zhihu.com/c_147309339)
- [无人驾驶技术入门（一）- 百度无人驾驶的引路人](https://zhuanlan.zhihu.com/p/31853845)
- [自动驾驶行业观察 - 站在Level 2之巅，沃尔沃XC60主动安全系统剖析](https://zhuanlan.zhihu.com/p/32058304)
- [无人驾驶技术入门（二）- 不会写代码也能做无人驾驶工程师](https://zhuanlan.zhihu.com/p/32308457)
- [无人驾驶技术入门（三）- 百度无人车传感器 GPS 深入剖析](https://zhuanlan.zhihu.com/p/32638633)
- [无人驾驶技术入门（四）- 百度无人车传感器 IMU 深入剖析](https://zhuanlan.zhihu.com/p/32693377)
- [无人驾驶技术入门（五）- 没有视觉传感器，还谈什么无人驾驶？](https://zhuanlan.zhihu.com/p/33067923)
- [自动驾驶行业观察 - 进军Level 3，奥迪A8自动驾驶功能剖析](https://zhuanlan.zhihu.com/p/33260873)
- [无人驾驶技术入门（六）- 工程师又爱又恨的激光雷达](https://zhuanlan.zhihu.com/p/33792450)
- [无人驾驶技术入门（七）- 量产必备的毫米波雷达](https://zhuanlan.zhihu.com/p/34675392)
- [无人驾驶技术入门（八）- 被严重低估的传感器超声波雷达](https://zhuanlan.zhihu.com/p/35177313)
- [自动驾驶行业观察 - 移动的安全感，奥迪A8L主动安全技术剖析](https://zhuanlan.zhihu.com/p/35944238)
- [无人驾驶技术入门（九）- 与生俱来的VCU信号](https://zhuanlan.zhihu.com/p/36654874)
- [自动驾驶行业观察 - More Than Level 2，捷豹I-PACE主动安全技术剖析](https://zhuanlan.zhihu.com/p/37357110)
- [无人驾驶技术入门（十）- 看不见的“传感器”高精度地图](https://zhuanlan.zhihu.com/p/37885573)
- [自动驾驶行业观察 - Baidu Apollo 五大安全魔鬼挑战](https://zhuanlan.zhihu.com/p/38979991)
- [无人驾驶技术入门（十一）- 无人驾驶中的CAN消息解析](https://zhuanlan.zhihu.com/p/39624163)
- [无人驾驶技术入门（十二）- 无人驾驶中的坐标转换](https://zhuanlan.zhihu.com/p/41263701)
- [无人驾驶技术快问快答 - 第一期](https://zhuanlan.zhihu.com/p/41840988)
- [无人驾驶技术快问快答 - 第二期](https://zhuanlan.zhihu.com/p/43498615)
- [无人驾驶技术入门（十三）- 手把手教你写卡尔曼滤波器](https://zhuanlan.zhihu.com/p/45238681)
- [自动驾驶行业观察 - 汽车高级驾驶辅助系统ADAS盘点](https://zhuanlan.zhihu.com/p/49170116)
- [无人驾驶技术入门（十四）- 初识图像之初级车道线检测](https://zhuanlan.zhihu.com/p/52623916)
- [无人驾驶技术入门（十五）- 再识图像之高级车道线检测](https://zhuanlan.zhihu.com/p/54866418)
- [无人驾驶实训营100小时回忆录](https://zhuanlan.zhihu.com/p/55035198)
- [无人驾驶技术入门（十六）- 初识深度学习之交通标志分类](https://zhuanlan.zhihu.com/p/57160727)
- [无人驾驶技术入门（十七）- 深度学习进阶之无人车行为克隆](https://zhuanlan.zhihu.com/p/60625133)
- [无人驾驶技术入门（十八）- 手把手教你写扩展卡尔曼滤波器](https://zhuanlan.zhihu.com/p/63641680)
- [无人驾驶技术入门（十九）- 手把手教你实现多传感器融合技术](https://zhuanlan.zhihu.com/p/67139241)

### 10. 个人成长经验分享

- [陆奇演讲：如何成为一个优秀的自动驾驶工程师（2018年）](https://mp.weixin.qq.com/s/acsBTZfCDHx-EcTjaK31Dw)

### 11. 硬件

- [百度王石峰：自动驾驶汽车硬件系统概述](https://mp.weixin.qq.com/s/Q8_4G-rxNqQVynNoBdZQWA)
- [全面解读毫米波雷达](https://mp.weixin.qq.com/s/0CtchlQlSpeB5VQtwxYYAQ)
- [谷歌Waymo的整车传感器配置方案](https://mp.weixin.qq.com/s/V4ZxKVBUtmOqzxZlqrYQvg)
- [特斯拉的整车传感器配置方案](https://mp.weixin.qq.com/s/Gs6kERBHLul9Dc4llrXAyw)
- [沙龙回顾丨Apollo 开发套件加速自动驾驶研发](https://mp.weixin.qq.com/s/22fOZv0Vxd4phebxh0fAIA)

### 12. 仿真

- 2019中国自动驾驶仿真技术蓝皮书 [[PDF]](/topics/data/2019-中国自动驾驶仿真技术蓝皮书.pdf)

- [自动驾驶车辆仿真模拟软件盘点](https://mp.weixin.qq.com/s/Qhx7TTZEgpFFjyBWyUkOgA)
- [回顾：Drive.ai 、文远知行WeRide、51VR，三大视角解读自动驾驶仿真](https://www.leiphone.com/news/201812/LrT2QsJvYSAv7khF.html)
- [Live回顾：文远知行WeRide自动驾驶仿真论——真实、闭环、规模、整合](https://www.leiphone.com/news/201812/PqnyCW6ngG0ikJFJ.html)
- [社群分享 - Apollo仿真平台如何Hold住99.9999%的复杂场景？](https://mp.weixin.qq.com/s/j4faPastB3nFmgH_nhVW6g)
	- [Apollo直答号 - 真实场景数据是怎么应用到仿真环境中的？](https://mp.weixin.qq.com/s/Pn8Kp-6MlQkjwO35FNBrRg)
- Apollo高精地图服务介绍及云端仿真平台应用[[Slide]](/topics/data/2017-Apollo高精地图服务介绍及云端仿真平台应用.pdf)

`51VR`

- [快讯 - 51VR受邀出席中国汽车重庆论坛，五大案例详解仿真最新实践](https://mp.weixin.qq.com/s/G6pcpWHREntP5Lnvc07NeQ)
- [51VR鲍世强：自动驾驶仿真不但注重技术细节，更需培育生态工具链](https://mp.weixin.qq.com/s/HPSHHi9jI516NaONcKLMJw)
- [51Sim-One无人驾驶仿真测试平台的自主研发经验与工程实践](https://mp.weixin.qq.com/s?__biz=MzAwOTMxOTc2NQ==&mid=2650589631&idx=1&sn=dc206f89426ff7e091300fd73cda2a6d&chksm=83690d85b41e8493daa5b02b76e5c5616939d92a1bc6e2537fe2cc2b46229b703a2711048648&mpshare=1&scene=1&srcid=%23rd)

`场景构建`

- [自动驾驶测试中的场景构建](https://mp.weixin.qq.com/s/4vLIdxjcV5YZv03kP72h8Q)

### 13. 商业落地

- [盘点百度、阿里、腾讯、华为自动驾驶战略](https://mp.weixin.qq.com/s/3TLO4C2NgagS-ncl9kWQYA)
- [自动驾驶商业化应用研究](https://mp.weixin.qq.com/s/AMcjRrjMuil8_g-TetKS2Q)
- [福瑞泰克CTO沈骏强谈自动驾驶商业化：怎样解决安全、体验、成本和场景问题？](https://www.leiphone.com/news/201811/rsI08E8M2Z8kNN34.html)
- [文远知行钟华：L4级别无人驾驶在中国的落地之路 -- GTC 中国 2018](https://www.leiphone.com/news/201811/rjZSfPELbOeK89m4.html)

### 14. 观点

- [哥伦比亚大学AI实验室主任Hod Lipson：阻碍无人驾驶技术发展的7个误区](https://mp.weixin.qq.com/s/A0PPdK55WLTNU0rvDfIWng)
- [Waymo 首席科学家在MIT自动驾驶课上开讲：如何解决自动驾驶的长期挑战](https://mp.weixin.qq.com/s/EmOnA4K-LApsAihOtdqIMQ)

### 15. 相关实验室

- [【盘点】智能车实验室盘点-欧洲篇](https://mp.weixin.qq.com/s/l7y9d9puzdGW467q4DPfzw)

- UC Berkeley: Mechanical Systems Control Lab
	- [[Home]](https://msc.berkeley.edu/) [[Research Topic: Autonomous Driving]](https://msc.berkeley.edu/research/autonomous-vehicle.html)

### 16. 期刊/会议（智能车领域）

会议
- IEEE Intelligent Vehicles Symposium (IV)
- IEEE International Conference on Intelligent Transportation Systems (ITSC)

期刊
- IEEE Transactions on Intelligent Transportation Systems

相关博文
- [自动驾驶领域顶级会议有哪些？](http://m.elecfans.com/article/688175.html)


### 17. 数据集

- [无人驾驶数据集汇总](https://mp.weixin.qq.com/s/dY5rqVc2fQ0cbzyJIHtcqA)


### 18. Pony.ai技术分享

整体
- [Pony.ai 的基础架构挑战与实践](https://mp.weixin.qq.com/s/fBmYxP0ALyil7crSFKWWEg)
- [自动驾驶从0到1之路](https://mp.weixin.qq.com/s?__biz=MzU1NTMyOTI4Mw==&mid=2247491875&idx=1&sn=4308296b589e6aecb3597ad6e986182b&chksm=fbd7534fcca0da59112b136be0bbbbdab2d79db4020e350ac1db71ad4b5aadacbaecd90519f3&mpshare=1&scene=1&srcid=&sharer_sharetime=1563857235612&sharer_shareid=3230aa8d692bbd5745277f42012c9308%23rd)

定位
- [高精地图和定位在自动驾驶的应用](https://mp.weixin.qq.com/s/QZ5W4YDD4rX8zM6qajQDtg)
- [自动驾驶复杂环境下高精度定位技术](https://mp.weixin.qq.com/s?__biz=MzU1NTMyOTI4Mw==&mid=2247491711&idx=1&sn=2299f6045271c28bdbb8bb30ae9cd8d2&chksm=fbd75213cca0db05281bccf11f14ac0587e0bd022e3506e1c0bc3b7deae8447040aff1a26608&mpshare=1&scene=1&srcid=&sharer_sharetime=1563857253686&sharer_shareid=3230aa8d692bbd5745277f42012c9308%23rd)

感知
- [L4自动驾驶中感知系统遇到的挑战及解决方案](https://mp.weixin.qq.com/s/cqdi9V_BnY6pwRJl3dD0dA)
- [传统方法和深度学习结合的感知策略探索](https://mp.weixin.qq.com/s?__biz=MzU1NTMyOTI4Mw==&mid=2247491669&idx=1&sn=47f3e771448efc8e12ad562ed6b78148&chksm=fbd75239cca0db2ff604247f820744eb37397f346252c03eb464277ff46ad45b370b6885be6f&scene=21#wechat_redirect)

决策规划控制
- [自动驾驶中轨迹规划的探索和挑战](https://mp.weixin.qq.com/s/1QXdFuppw1I3PkD5LV9kcg)



### 19. 安全报告

国内
- Apollo(2018) [[PDF]](/topics/data/safety-report/2018-Apollo-safety-report.pdf)
- 自动驾驶安全白皮书(2019) [[PDF]](http://apollo.auto/docment/Safety_First_for_Automated_Driving_handover_to_PR.pdf)
- 高精地图安全白皮书(2019) [[PDF]](http://apollo.auto/docment/Reliable_and_Safe_maps_for_Automated_driving.pdf)

国外
- Waymo(2017) [[PDF]](/topics/data/safety-report/2017-Waymo-on_the_road_to_fully_self-driving.pdf)
- GM(2018) [[PDF]](/topics/data/safety-report/2018-GM-safety-report.pdf)[[Appendix]](/topics/data/safety-report/2018-GM-safety-report-appendix.pdf)
- Ford(2018) [[PDF]](/topics/data/safety-report/2018-Ford-safety-report.pdf)
- Nuro(2018) [[PDF]](/topics/data/safety-report/2018-Nuro-delivering_safety_nuros_approach.pdf)[[解读]](https://mp.weixin.qq.com/s/U0q1I32EU5PVLYe8ZgpqQQ)
- Nvidia(2018) [[PDF]](/topics/data/safety-report/2018-NVIDIA-Self-Driving-Safety-Report.pdf)
- Uber(2018) [[PDF]](/topics/data/safety-report/2018-Uber-ATGSafety-Report.pdf)
- Apple(2019) [[PDF]](/topics/data/safety-report/2019-Apple-ADS-Safety.pdf)

### 20. 其它

- [自动驾驶思考：硬件篇（王方浩）](https://mp.weixin.qq.com/s/IgwdJx6D3cmdxZ3suP86lQ)
- [自动驾驶思考：基础架构篇（王方浩）](https://mp.weixin.qq.com/s?__biz=MzU1NTMyOTI4Mw==&mid=2247492116&idx=1&sn=2b383a7303fb7becfa13cdd872c89b47&chksm=fbd75078cca0d96edd5146105a03065bbaf81fa23412c6c1cdcd0ce33ab20bcc3e1b119e1879&mpshare=1&scene=1&srcid=&sharer_sharetime=1563857187601&sharer_shareid=3230aa8d692bbd5745277f42012c9308%23rd)











