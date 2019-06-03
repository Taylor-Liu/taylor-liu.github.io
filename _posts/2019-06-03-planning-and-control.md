---
layout: post
title: Planning and Control in Self-Driving Cars
---

Illustration of the hierarchy of decision-making processes. A destination is passed to a **route planner** that generates a route through the road network. A **behavioral layer** reasons about the environment and generates a motion specification to progress along the selected route. A **motion planner** then solves for a feasible motion accomplishing the specification. A **feedback control** adjusts actuation variables to correct errors in executing the reference path.

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