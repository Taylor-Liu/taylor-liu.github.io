---
layout: post
title: Reinforcement Learning for Real-World Robotics
subtitle: Ideas from the literature on RL for real-world robot control
tags: [reinforcement learning, robotics]
---

Author: [Or Rivlin](https://towardsdatascience.com/@or.rivlin.mail)  
Date: Aug. 1, 2019  
From: [https://towardsdatascience.com/reinforcement-learning-for-real-world-robotics-148c81dbdcff](https://towardsdatascience.com/reinforcement-learning-for-real-world-robotics-148c81dbdcff)

---
**Table of Contents**
* TOC
{:toc}
---

## Robots — The Promise

Robots are pervasive throughout modern industry. Unlike most science-fiction works of the previous century, humanoid robots are still not doing our dirty dishes and taking out the trash, nor are Schwarzenegger-looking terminators fighting on the battlefields (at least for now…). But, in almost every manufacturing facility robots are doing the kind of tedious and demanding work that human workers used to do just several decades ago. Anything that requires repetitive and precise work in an environment that can be carefully controlled and monitored is a good candidate for a robot to replace a human, and today cutting edge research is fast-approaching the possibility of automating tasks that are very hard even though we might consider them tedious (such as driving).

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/05.png" />
</p>

The motivation behind our fascination with robots can be easily seen; a future where humans are free from hard and boring manual work seems very desirable to many. In addition, the precision and consistency that are typical of machines could reduce disasters that occur due to human error, such as car crashes and medical accidents during surgery. We are starting to see the first harbingers of that revolution outside of manufacturing lines; in large warehouses such as those of amazon, robots are being used to transport crates instead of human workers.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/06.png" />
</p>

While we still don’t have killer humanoid robots on the battlefield, we do have semi-autonomous drones operating all over the world, both in reconnaissance and combat missions. Large efforts in military advanced research organizations are on the way to move soldiers further from harm’s way and let machines do the actual fighting, and I expect that we will indeed see such developments in future decades.

## Reinforcement Learning for Robotics

Why is it that science-fiction from several decades ago nearly always saw our near future as including intelligent humanoid robots doing everything, and we seem so far away from it? How comes our manufacturing facilities are full of robots but our streets and homes have none? For a robot to successfully operate in a given environment it must make sense of it somehow, plan its actions and execute those plans using some means of actuation, while using feedback to make sure everything proceeds according to plan.

It turns out that each of those components is a very hard problem, and things that we humans do easily (like recognizing objects in a visual scene and predicting to some degree people’s intents) are often incredibly challenging for a computer. Recent years have seen the rise of deep learning to prominence in various tasks of computer vision, but the broad spectrum of skills required to make sense of a typical pedestrian street scene is still not within the grasp of current technology.

It turns out that there is a vast difference between operating in an assembly line and operating in the street. In the assembly line, everything in the environment can usually be precisely controlled, and the tasks needed to be performed by the robot are often very specific and narrow. Despite these advantages, designing the motion planning and control algorithms for manufacturing robots is a long and tedious process, requiring the combined efforts of many domain experts. This makes the process very costly and lengthy, which highlights the vast gap between our current capabilities and those required for robots that need to operate in much more general environments and perform an array of tasks. If we are having difficulty designing algorithms for those narrow tasks, how can we scale to robots for our homes? Those robots will have to navigate the often-complex landscape of urban spaces, handle the messy real-world (compare washing dishes haphazardly left in the sink and painting a car exterior, precisely placed and timed in an assembly line) and interact with human beings while ensuring their safety.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/07.png" />
</p>

The successes of deep learning and reinforcement learning in recent years have led many researchers to develop methods to control robots using RL. The motivation is obvious, can we automate the process of designing sensing, planning and control algorithms by letting the robot learn them autonomously? If we could, we would solve two of our problems at once; save the time and energy we spend on designing algorithms for the problems that we know how to solve today (industrial robots) and gain solutions to those harder problems that we have no current solution for.

Deep reinforcement learning came to the public attention after amazing successes in various video games and board games, or relatively simple simulated control problems. In these tasks, the environment on which the agent learns is the same on which it must operate, and we can efficiently use the simulation to allow the agent many trials before it learns to solve the task. <mark class="ro rp fr">Deep reinforcement learning algorithms are notoriously data inefficient, and often require millions of attempts before learning to solve a task such as playing an Atari game.</mark> If we tried to apply the same methods to train our robot in the real world, it would take an unrealistic amount of time, and likely destroy the robot in the process. Alternatively, we might naively attempt to use a simulation to train our agent and then deploy the trained policy on the real robot. But simulating the intricacies of the real world is very difficult and such policies often perform poorly on the physical robot.

There are many challenges in applying RL to robotics, and in my opinion, many of them can be crudely divided to these four categories:

**Sample efficiency**: If we wish to train our policies using physical robots, we must develop algorithms that require few enough trials to learn, so that training will be feasible, unlike many of the algorithms we have today.

**Sim2Real**: If we wish to train our policies in a simulated environment and then deploy them

**Reward specification**: When playing chess or StarCraft2 the goal is very clear and easily quantified; win or lose. However, how do you quantify the level of success in something like washing dishes? Or folding laundry?

**Safety**: Our robot policies must be safe (during both training on a robot and deployment to the real world), in order to ensure the integrity of the robot itself and the safety of people and property in the environment.

I will mostly address the first two categories, briefly touch on the third one and avoid the last.

## Sample Efficiency

Traditionally, the go-to approach when desiring extremely low sample complexity in RL is model-based RL. In model-based RL, instead of learning a policy only based on rewards obtained by interaction with the environment, the agent tries to learn a model of the environment and use it to plan and improve its policy, thus dramatically reducing the number of interactions it needs with the environment. However, this approach often results in lower asymptotic performance compared to model-free algorithms, and sometimes suffers from catastrophic failures due to errors in the learned model.

Model-based RL showed great success in problems where the dynamics can be sufficiently represented by a simple model, such as a linear one, but have not had great successes in more complex environments where non-linear models (such as deep neural networks) are required. In 2018 researchers from Berkeley published a [paper](https://arxiv.org/pdf/1802.10592.pdf) on the subject, in which they identified a suspected cause to the instability issues and suggested a solution.

In their paper, they claim that during learning and planning, the policy tends to exploit those regions of the state-space on which the learned model performs poorly, which veers the agent “off-course” from areas in which it can reliably plan ahead using the learned model to those in which it is completely blind, rendering it ineffective. Their solution is relatively simple; learn several different models of the environment, and during planning uniformly sample from these different models, effectively regularizing the learning process. This enabled applying model-based RL to more complex tasks than previously possible, achieving asymptotic performance comparable to model-free algorithms in orders of magnitude less attempts.

Interestingly, a recent model-free algorithm has demonstrated excellent sample complexity, so much so that it was possible to train a policy on a real robot in a relatively short amount of time. In 2019 researchers from Berkeley and Google Brain published a [paper](https://arxiv.org/pdf/1812.05905.pdf) in which they describe an off-policy actor-critic algorithm called Soft Actor Critic (SAC). They demonstrated that this algorithm performs very well with low sample complexity on several traditional RL control benchmarks, and then proceeded to train a robot to walk in only 4 hours of environment interaction.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/08.png" />
</p>

The robot was trained to walk on a flat surface, and then successfully tested on surfaces with different obstacles, showing the robustness of the learned policy.

Another nice [paper](https://arxiv.org/pdf/1812.03201.pdf) took a different path to sample efficiency; by doing away with the notion that the policy must be learned from scratch, and should utilize existing imperfect control algorithms to provide a “skeleton” on which to grow the policy. By exploiting the fact that existing control algorithms are reasonably well-behaved for the problem, the policy can learn to fine-tune the control system and not start from random behavior as in most RL algorithms. They use this approach to train a robot for a real block assembly task involving complex dynamics.

## Sim2Real

In the past few years, many research papers have demonstrated the capabilities of their learned RL policies to operate in a physical robot platform, but these are often limited to narrow tasks and usually require extensive manual adjustments to work properly. Especially for robots that use visual sensing, it is extremely difficult to realistically simulate the images a robot is likely to encounter, and this creates the famous Sim2Real gap.

In problems where the dynamics can be sufficiently captured by a simulation, RL can actually work pretty well, as can be seen in this [paper](https://arxiv.org/pdf/1901.07517.pdf?fbclid=IwAR21IneQ5Lusw62bCyh0oDzRJYh2nKercXP53vp35dIGtT-edIcITZBeetc), in which a policy was trained to learn recovery maneuvers for a quadrupedal robot using a simulation, and it transferred to the real robot very well, with an impressive 97% success rate. However, in this problem the state was relatively low dimensional, unlike visual representations.

To tackle the problem of coping with visual inputs, a nice [paper](https://arxiv.org/pdf/1703.06907.pdf) from 2017 by OpenAI and Berkeley offers a very neat solution; randomize the visual inputs provided by the environment, and train the policy to be very robust to these changes, in the hopes that the real world would like just another variation of the simulation.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/09.png" />
</p>

This worked very well, and they were able to use an object detector trained solely in simulation, in a real robot grasping system.

A very cool continuation of that work was published in a 2019 [paper](https://arxiv.org/pdf/1812.07252.pdf). In this paper the researchers used a similar randomized simulation to help train the policy to be robust, but simultaneously trained a conditional GAN (cGAN) to transform the randomized images back to a canonical form of the original simulation. During test time, the cGAN transformed the real images to the canonical image form that the policy was familiar with, thus helping to reduce the Sim2Real gap. Using this method, they trained an agent in simulation and used it on a robot with 70% success rate. Using some finetuning on the real robot, they were able to achieve 91% and even 99% success rates.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/10.png" />
</p>

## Reward Specification

Say you want your robot to learn to place books in a bookshelf, and that you have an algorithm with very low sample complexity. How does one go about designing a reward function for this? In a very cool 2019 [paper](https://arxiv.org/pdf/1904.07854.pdf), researchers from Berkeley did just that. Instead of specifying a reward function, they provide the algorithm with several images of a goal state (arranged bookshelves), and allow it to query the user (very few times) if the current state is a goal state. Using the r=previously mentioned Soft Actor Critic algorithm together with several other algorithms, they trained their policy on a real robot in a few hours. They trained different policies for different tasks, such as putting books in the shelf and draping a cloth over a box.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/11.png" />
</p>

## Conclusion

The challenge of applying RL to real-world robotics problems is still far from being declared solved, but much progress is being made and hopefully we will continue to see further breakthroughs in this exciting field.

Disclaimer: the views expressed in this article are those of the author and do not reflect those of IBM.













