---
layout: page
title: Robotics
---

## ROS

- ROSCon [[2019]](https://roscon.ros.org/2019/) [[2018]](https://roscon.ros.org/2018/) [[2017]](https://roscon.ros.org/2017/) [[2016]](https://roscon.ros.org/2016/) [[2015]](https://roscon.ros.org/2015/) [[2014]](https://roscon.ros.org/2014/) [[2013]](https://roscon.ros.org/2013/) [[2012]](https://roscon.ros.org/2012/)

- Determinism in Robotics Software: when things break sometimes and how to fix it (ROSCon2017) [[Slide]](https://roscon.ros.org/2017/presentations/ROSCon%202017%20Determinism%20in%20ROS.pdf) [[Video]](https://vimeo.com/236186712)
	- ROS’s foundational style, the asynchronous, loosely coupled compute graph, is great for re-use and distribution, but there’s a catch: Nothing guarantees execution ordering. This means, the order in which callbacks and timers are executed can change even when inputs are the same. In many important cases, this leads to different results, and – subtly or not so subtly – changes the robot’s behavior. As an example, in the common move_base node, we found reaction times changing between 50 and 200ms, while pure computation time was only 20ms. I will show why this happens, and how to address it, both in the move_base and in general.

## Conferences

- [ICRA2019 Paper List](https://github.com/Taylor-Liu/ICRA2019-paper-list)