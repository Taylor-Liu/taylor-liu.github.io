---
layout: page
title: Autonomous Driving
---

<p style="text-align:center">
	<img src="/topics/img/waymo.png" />
</p>


[Apollo自动驾驶工程师技能图谱V2.0](https://taylor-liu.github.io/topics/data/apollo-v2.pdf)


### 1. 基础知识

- [无人驾驶技术入门（十二）- 无人驾驶中的坐标转换](https://zhuanlan.zhihu.com/p/41263701)
- [无人驾驶技术入门（十三）- 手把手教你写卡尔曼滤波器](https://zhuanlan.zhihu.com/p/45238681)
- [无人驾驶技术入门（十八）- 手把手教你写扩展卡尔曼滤波器](https://zhuanlan.zhihu.com/p/63641680)

- [解析百度Apollo自动驾驶平台](https://paul.pub/baidu-apollo/#id-prediction%E9%A2%84%E6%B5%8B)

### 2. Prediction

- [自动驾驶公开课 - Apollo 2.5预测系统介绍](https://mp.weixin.qq.com/s/48DcWP1kAoze0Lv8jHY3Ow)
- Apollo3.5预测模块官方介绍[[中文]](https://github.com/ApolloAuto/apollo/blob/master/modules/prediction/README_cn.md)[[英文]](https://github.com/ApolloAuto/apollo/blob/master/modules/prediction/README.md)
- [自动驾驶中的障碍物行为预测](https://www.jiqizhixin.com/articles/2019-05-14-4?from=synced&keyword=%E8%87%AA%E5%8A%A8%E9%A9%BE%E9%A9%B6)


### 3. Planning and Control (PNC)

- [解析百度Apollo之决策规划模块](https://paul.pub/apollo-planning/#id-publicroadplanner)
- [直播回顾 - Apollo决策技术分享](https://mp.weixin.qq.com/s/KFjfhs5zdHdrukRnm52rsg)
- [Apollo问答 - 如何拿下无人驾驶决策技术②](https://mp.weixin.qq.com/s/GvbOUg2LOnFTWZrXL7aQ2A)
- Apollo3.5规划模块官方介绍[[中文]](https://github.com/ApolloAuto/apollo/blob/master/modules/planning/README_cn.md)[[英文]](https://github.com/ApolloAuto/apollo/blob/master/modules/planning/README.md)
- [自动驾驶中有哪些路径规划框架?](https://zhuanlan.zhihu.com/p/43405664)
- [PythonRobotics: Python sample codes for robotics algorithms](https://atsushisakai.github.io/PythonRobotics/)

`路径规划`

- [路径搜索可视化](http://qiao.github.io/PathFinding.js/visual/)
- [路径规划之 A* 算法](https://paul.pub/a-star-algorithm/#id-%E7%AE%97%E6%B3%95%E5%8F%98%E7%A7%8D)
- [Introduction to the A* Algorithm](https://www.redblobgames.com/pathfinding/a-star/introduction.html)
- Baidu Apollo EM Motion Planner[[Paper-18年发表]](https://arxiv.org/pdf/1807.08048.pdf)

`企业招聘要求`

- [Waymo: Software / Research Engineer, Planning and Motion Control](https://waymo.com/joinus/1305655/)
- [Waymo: Software Engineer, Planner & Controls](https://waymo.com/joinus/928478/)
- [文远知行：决策规划工程师 - ML/DL方向](https://app.mokahr.com/apply/jingchi/2138#/job/d2455c6c-8f2a-4c39-b2ff-e20fdd552836?_k=qxytrx)

### 4. 操作系统

- ROS在自动驾驶的探索和实践 [[Blog]](https://mp.weixin.qq.com/s?__biz=MzI5MjcyNTc1Mw==&mid=2247483975&idx=1&sn=7d946e3322710d7b7b1e6688c37f8f43&chksm=ec7db4d1db0a3dc7eda3e26ea35945da9aebaee32cbe28f91c5b8b9fc589fbec284887e1bc18&scene=21#wechat_redirect) [[Slide]](https://taylor-liu.github.io/topics/data/ROS在自动驾驶的探索和实践.pdf)

### 5. Apollo项目

`硬件架构：`

<p style="text-align:center">
	<img src="https://taylor-liu.github.io/topics/img/apollo/apollo_ardware_overview_3_5.png" />
</p>

`硬件之间的数据流：`

<p style="text-align:center">
	<img src="https://taylor-liu.github.io/topics/img/apollo/apollo_hardware_connection_3_5_1.png" />
</p>

`软件架构（导航模式）：`

<p style="text-align:center">
	<img src="https://taylor-liu.github.io/topics/img/apollo/apollo_3_5_software_architecture.png" />
</p>

`模块的官方说明：`

- [Perception（感知）](https://github.com/ApolloAuto/apollo/tree/master/modules/perception)
- [Prediction（预测）](hhttps://github.com/ApolloAuto/apollo/tree/master/modules/prediction)
- [Routing（路由）](https://github.com/ApolloAuto/apollo/tree/master/modules/routing)
- [Planing（计划）](https://github.com/ApolloAuto/apollo/tree/master/modules/planning)
- [Control（控制）](https://github.com/ApolloAuto/apollo/tree/master/modules/control)

### 6. 相关课程

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








