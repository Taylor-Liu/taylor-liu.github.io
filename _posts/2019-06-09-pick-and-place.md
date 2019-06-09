---
layout: post
title: Framework of Pick and Place for Mobile Manipulation
---

The overall approach to the pick and place task is shown schematically in Figure 1. A representation of the environment is built and maintained using a combination of 2D and 3D visual sensors. This model includes a lower resolution representation of the environment using an octree-based approach, and higher resolution representations of objects of interest using mesh primitives. Object detection and segmentation routines are used to segment the raw point cloud representation and to recognize objects of interest, including planar surface models from which objects can be placed or picked up. The environment model serves as input to both the grasp planning and motion planning components. The grasp planning framework determines grasps for objects of interest and is capable of dealing with either detailed mesh representations or a coarser model obtained from segmentation. The motion planning and execution framework plans and executes trajectories to the desired end-effector positions for grasping, pickup, and placement of objects. A grasp execution component takes over control of the arm during the actual grasping action, using reactive controllers to correct for any error in the perceived placement of the objects.

<p style="text-align:center">
	<img src="/topics/img/manipulation/pick_and_place_framework.png" width="600" />
	<br /> Figure 1. High-level system architecture for our approach to 
	<br /> executing pick and place tasks.
</p>

### Motion Planning and Execution

An overall schematic representation of our motion planning and execution framework used for the robot’s arms is shown in Figure 2. The particular implementation we describe here is intended for use with robotic arms. Motion planning and execution for the base is decoupled from that for the arms, and is described in Section IV-B3. Future work will involve the development of components for whole-body planning and control. Our approach to motion planning and execution follows a traditional sense-plan-act paradigm but also incorporates an online monitoring component, allowing our system to abort execution and replan quickly if necessary when new obstacles move into the planned path of the robot.  

<p style="text-align:center">
	<img src="/topics/img/manipulation/motion_planning_and_execution.jpg" width="600" />
	<br /> Figure 2. System architecture for motion planning and execution. 
	<br /> *Move Arm* is the software component that serves as the interface 
	<br /> to motion planning and execution. 
</p>

The Motion Planner component in Figure 2 is carried out using randomized motion planners integrated from the OMPL Library. These motion planners can operate on both joint space or end-effector pose goals (Figure 2). Inverse kinematics (IK component in Figure 2) is used in the latter case to sample joint-space goals that the planner can then plan to. The output of the motion planner is a path that can often be jagged and long. The path is refined and parametrized in time using shortcutting techniques designed for smoothing and shortening the path (the smoother component in Figure 2). Our particular implementation of shortcutting uses cubic splines and can account for bounds on joint velocities and accelerations. A custom analytical solution for inverse kinematics was used for the 7-DOF PR2 robot, parameterized by one of the joint angles. For robots other than the PR2, we use the KDL toolchain to provide a numerical inverse kinematics solver.  

Execution of trajectories is handled using a state machine approach that incorporates active monitoring of the trajectories executed on the arm. A controller designed to accurately track the desired trajectory is used to execute the planned trajectory on the robot. Active monitoring involves moving the head of the robot (on which the sensors are mounted) to maintain visibility of the arm as it is executing the trajectory. If a new obstacle is detected along the expected execution path, the arm is brought to a stop along the path. If the obstacle clears out of the path of the robot within a specified timeout, the trajectory continues to be executed. If the timeout is exceeded, a new path is planned and executed, taking into account the presence of the new obstacle. Figure 3 shows two snapshots from a scenario where the robot stops when it sees a new obstacle, waits for the obstacle to clear, and then re-executes its planned path.

### References

- Chitta, Sachin, et al. "Perception, planning, and execution for mobile manipulation in unstructured environments." IEEE Robotics and Automation Magazine, Special Issue on Mobile Manipulation 19.2 (2012): 58-71. [[Paper]](https://www.willowgarage.com/sites/default/files/chitta_ram_2011.pdf)
- Researcher: Sachin Chitta [[Mobile Manipulation]](https://www.sachinchitta.org/mobile-manipulation.html)