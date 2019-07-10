---
layout: page
title: Robotics
---

## ROS

- [开源机器人基金会（中国）](http://www.roseducation.org/)

- ROSCon [[2019]](https://roscon.ros.org/2019/) [[2018]](https://roscon.ros.org/2018/) [[2017]](https://roscon.ros.org/2017/) [[2016]](https://roscon.ros.org/2016/) [[2015]](https://roscon.ros.org/2015/) [[2014]](https://roscon.ros.org/2014/) [[2013]](https://roscon.ros.org/2013/) [[2012]](https://roscon.ros.org/2012/)

- Determinism in Robotics Software: when things break sometimes and how to fix it (ROSCon2017) [[Slide]](https://roscon.ros.org/2017/presentations/ROSCon%202017%20Determinism%20in%20ROS.pdf) [[Video]](https://vimeo.com/236186712)
	- ROS’s foundational style, the asynchronous, loosely coupled compute graph, is great for re-use and distribution, but there’s a catch: Nothing guarantees execution ordering. This means, the order in which callbacks and timers are executed can change even when inputs are the same. In many important cases, this leads to different results, and – subtly or not so subtly – changes the robot’s behavior. As an example, in the common move_base node, we found reaction times changing between 50 and 200ms, while pure computation time was only 20ms. I will show why this happens, and how to address it, both in the move_base and in general.

`ROS2`

- [Awesome Robot Operating System 2 (ROS 2) ](https://fkromer.github.io/awesome-ros2/)
- In ROSCon2018
	- Hands-on ROS 2: A Walkthrough [[Video]](https://vimeo.com/292693129)[[Slide]](https://roscon.ros.org/2018/presentations/ROSCon2018_ROS2HandsOn.pdf)
		- In this talk we show the current state of ROS 2 features through hands-on demonstrations. We guide the developer through a set of features and functionalities of ROS 2 beginning with creating a simple “hello world” package and consecutively increasing functionality. We show how to launch multiple nodes, how lifecycle nodes can be used to bootstrap a complete system, through to how the ROS 2 security features can be utilized to secure applications. This talk is meant to highlight the newly available features and tools of ROS 2 and aims to incline developers to start working with it.
	- ROS 2 on Autonomous Driving Vehicles [[Video]](https://vimeo.com/292695688)[[Slide]](https://roscon.ros.org/2018/presentations/ROSCon2018_ROS2onAutonomousDrivingVehicles.pdf)
		- Over the past 10 years, ROS 1 has proven itself to be the framework of choice for prototyping and developing large robotic applications. Many limitations preventing ROS 1 from being used in production applications have been discovered over the years, and after significant prototyping, ROS 2 makes great headway in making ROS 2 suitable for production. Autonomous driving is the next great technology waiting to be realized and transform our society. A full autonomous driving stack is inarguably a large robotic system, and consequently ROS 2 is the right framework upon which to develop a full autonomous driving stack. To prove this, we have developed a part of the autonomous driving stack based on ROS 2.

## Conferences

- [ICRA2019 Paper List](https://github.com/Taylor-Liu/ICRA2019-paper-list)