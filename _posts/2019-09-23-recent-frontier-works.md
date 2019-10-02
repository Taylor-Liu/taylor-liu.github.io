---
layout: post
title: Recent Frontier Works (2019.09.23 update)
tags: [reinforcement learning]
---

---
**Content**
* TOC
{:toc}
---

## 1. Model-based Learning

* Model Based Policy Optimization: Reviewing recent advances in model-based reinforcement learning [[Blog]](http://taylorliu.com/2019-09-11-model-based-policy-optimization/)

* Model-based Lookahead Reinforcement Learning [[Paper]](https://arxiv.org/abs/1908.06012v1)

    * Zhang-Wei Hong, Joni Pajarinen, Jan Peters

    * TU Darmstadt

* Hierarchical Foresight: Self-Supervised Learning of Long-Horizon Tasks via Visual Subgoal Generation [[Paper]](https://arxiv.org/abs/1909.05829) [[Github]](https://github.com/google-research/google-research/tree/master/hierarchical_foresight)

    * Suraj Nair, Chelsea Finn

![](/posts-data/media/15687335003539.jpg)

* Dynamics-Aware Unsupervised Discovery of Skills [[Homepage]](https://sites.google.com/view/dads-skill)

    * Archit Sharma, Shixiang Gu, Sergey Levine, Vikash Kumar, Karol Hausman
    
    * Google Brain
    
## 2. Hierarchical Learning

* Multi-Agent Manipulation via Locomotion using Hierarchical Sim2Real [[Homepage]](https://sites.google.com/view/manipulation-via-locomotion/home) [[Paper]](https://arxiv.org/abs/1908.05224)

    *  Ofir Nachum, Michael Ahn, Hugo Ponte, Shixiang Gu, Vikash Kumar

![](/posts-data/media/15687345050670.jpg)

![](/posts-data/media/15687345129596.jpg)

![](/posts-data/media/15687345206880.jpg)


## 3. Meta Learning

* Meta-World: A Benchmark and Evaluation for Multi-Task and Meta Reinforcement Learning [[Homepage]](https://meta-world.github.io) [[Github]](https://github.com/rlworkgroup/metaworld)
    
    * Stanford, UC Berkeley
    
    * Tianhe Yu (Stanford), Deirdre Quillen (UC Berkeley), Zhanpeng He (Columbia University), Ryan Julian (USC), Karol Hausman (Robotics at Google), Sergey Levine (UC Berkeley), Chelsea Finn (Stanford University)


![](/posts-data/media/15687323670854.jpg)

![](/posts-data/media/15687329679172.jpg)

* Meta-Learning with Implicit Gradients [[Paper]](https://arxiv.org/abs/1909.04630)
    
    * Aravind Rajeswaran, Chelsea Finn, Sham Kakade, Sergey Levine

    * NIPS'19

    * 摘要：智能系统的一个核心能力是能够通过借鉴以往的经验快速学习新任务。基于梯度(或优化)的元学习是近年来出现的一种有效的学习方法。在这个范式中，元参数在外部循环中学习，而特定于任务的模型在内部循环中只使用当前任务的少量数据学习。扩展这些方法的一个关键挑战是需要通过内部循环学习过程进行区分，这可能带来相当大的计算和内存负担。利用隐式微分法，提出了隐式MAML算法，该算法只依赖于内部层次优化的解，而不依赖于内部循环优化器所采用的路径。这有效地将元梯度计算与内部循环优化器的选择解耦。因此，我们的方法对内部循环优化器的选择是不可知的，并且可以优雅地处理许多梯度步骤，而不会消失梯度或内存约束。从理论上，我们证明了隐式MAML可以计算精确的元梯度，其内存占用不超过计算单个内循环梯度所需的内存占用，且不增加总计算成本。实验表明，隐式MAML的这些优点可以转化为基于少量样本图像识别基准的经验增益。
    
![](/posts-data/media/15687332543722.jpg)

* PyTorch Meta-learning Framework for Researchers [[Homepage]](http://learn2learn.net/) [[Github]](https://github.com/learnables/learn2learn)

    * learn2learn provides high- and low-level utilities for meta-learning. The high-level utilities allow arbitrary users to take advantage of exisiting meta-learning algorithms. The low-level utilities enable researchers to develop new and better meta-learning algorithms.

    * Some features of learn2learn include:

        * Modular API: implement your own training loops with our low-level utilities.
        
        * Provides various meta-learning algorithms (e.g. MAML, FOMAML, MetaSGD, ProtoNets, DiCE)
        
        * Task generator with unified API, compatible with torchvision, torchtext, torchaudio, and cherry.
        
        * Provides standardized meta-learning tasks for vision (Omniglot, mini-ImageNet), reinforcement learning (Particles, Mujoco), and even text (news classification).
        
        * 100% compatible with PyTorch -- use your own modules, datasets, or libraries!

## 4. RL Library

* rlpyt: A Research Code Base for Deep ReinforcementLearning in PyTorch [[Paper]](https://arxiv.org/abs/1909.01500) [[Github]](https://github.com/astooke/rlpyt)

    * Adam Stooke, Pieter Abbeel

    * Implemented Algorithms

        * **Policy Gradient** A2C, PPO.
        
        * **Replay Buffers** (supporting both DQN + QPG) non-sequence and sequence (for recurrent) replay, n-step returns, uniform or prioritized replay, full-observation or frame-based buffer (e.g. for Atari, stores only unique frames to save memory, reconstructs multi-frame observations).
        
        * **Deep Q-Learning** DQN + variants: Double, Dueling, Categorical (up to Rainbow minus Noisy Nets), Recurrent (R2D2-style). _Coming soon_: Implicit Quantile Networks?
        
        * **Q-Function Policy Gradient** DDPG, TD3, SAC.

* [p-christ/Deep-Reinforcement-Learning-Algorithms-with-PyTorch](https://github.com/p-christ/Deep-Reinforcement-Learning-Algorithms-with-PyTorch)
	
	* PyTorch implementations of deep reinforcement learning algorithms and environments, including DQN, DQN-HER, Double DQN, REINFORCE, DDPG, DDPG-HER, PPO, SAC, SAC Discrete, A3C, A2C etc..

