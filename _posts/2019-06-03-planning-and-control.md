---
layout: post
title: Planning and Control in Self-Driving Cars
---

Illustration of the hierarchy of decision-making processes. A destination is passed to a **route planner** that generates a route through the road network. A **behavioral layer** reasons about the environment and generates a motion specification to progress along the selected route. A **motion planner** then solves for a feasible motion accomplishing the specification. A **feedback control** adjusts actuation variables to correct errors in executing the reference path.

<p style="text-align:center">
	<img src="/topics/img/decision-making.png" width="400" />
</p>

Questions:

- 根据什么来决定此时的行为？（超车？跟车？变道？）
	- cost function?
- 决定超车后，如何规划一条可行的轨迹？
- 不同框架PNC模块的输入是什么？
	- Apollo ？
	- Waymo ?
- 什么时候会有行为层(behavioral layer)? 
- Apollo中是否有行为层？
- 哪些模块可以用学习的方法（如：RL, DL）得到？
- PNC目前存在的难点是什么？


### 参考资料

- 2016 - MIT - A Survey of Motion Planning and ControlTechniques for Self-Driving Urban Vehicles
- 《Creating Autonomous Vehicle Systems》Chapter 07: Decision,Planning and Control [[English]](/topics/data/decision-planning-control.pdf) [[Chinese]](/topics/data/无人驾驶的规划与控制.pdf) [[Mindnote]](/topics/data/pnc-mindnote.pdf)
- [刘少山：深度 | 无人驾驶的决策规划控制技术（雷锋网）](https://www.leiphone.com/news/201705/ShKxa21KiSdwmu7n.html)

<p style="text-align:center">
	<img src="/topics/img/pnc.png" />
</p>