---
layout: post
title: Framework of Pick and Place for Mobile Manipulation
---

The overall approach to the pick and place task is shown schematically in Figure 1. A representation of the environment is built and maintained using a combination of 2D and 3D visual sensors. This model includes a lower resolution representation of the environment using an octree-based approach, and higher resolution representations of objects of interest using mesh primitives. Object detection and segmentation routines are used to segment the raw point cloud representation and to recognize objects of interest, including planar surface models from which objects can be placed or picked up. The environment model serves as input to both the grasp planning and motion planning components. The grasp planning framework determines grasps for objects of interest and is capable of dealing with either detailed mesh representations or a coarser model obtained from segmentation. The motion planning and execution framework plans and executes trajectories to the desired end-effector positions for grasping, pickup, and placement of objects. A grasp execution component takes over control of the arm during the actual grasping action, using reactive controllers to correct for any error in the perceived placement of the objects. These components will now be described in greater detail.

<p style="text-align:center">
	<img src="/topics/img/manipulation/pick_and_place_framework.png" width="600" />
	<br /> Figure 1: High-level system architecture for our approach to 
	<br /> executing pick and place tasks.
</p>


### References

- Chitta, Sachin, et al. "Perception, planning, and execution for mobile manipulation in unstructured environments." IEEE Robotics and Automation Magazine, Special Issue on Mobile Manipulation 19.2 (2012): 58-71. [[Paper]](https://www.willowgarage.com/sites/default/files/chitta_ram_2011.pdf)
- Researcher: Sachin Chitta [[Mobile Manipulation]](https://www.sachinchitta.org/mobile-manipulation.html)