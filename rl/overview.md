---
layout: page
title: Reinforcement Learning
subtitle: Sim-to-Real, RL in Real World, Distributed RL, Meta-RL, Model-based RL, Hierarchical RL
---

<p style="text-align:center">
<img src="/topics/img/rl_framework.jpg" width="500" />
</p>

### 专栏

- [知乎专栏：强化学习知识大讲堂](https://zhuanlan.zhihu.com/sharerl)

### Model-based RL

- Blog
	- Jonathan Hui
		- [RL — LQR & iLQR Linear Quadratic Regulator](https://medium.com/@jonathan_hui/rl-lqr-ilqr-linear-quadratic-regulator-a5de5104c750)
		- [RL — Model-based Reinforcement Learning](https://medium.com/@jonathan_hui/rl-model-based-reinforcement-learning-3c2b6f0aa323)
	- [Week 6 - Model-based RL](https://hollygrimm.com/rl_modelbased)

- Related Works
	- 2019 - Dynamics-Aware Unsupervised Discovery of Skills
		- Archit Sharma, Shixiang Gu, Sergey Levine, Vikash Kumar, Karol Hausman
		- Google Brain
		- [[Project Home]](https://sites.google.com/view/dads-skill)
	- 2019 - Benchmarking Model-Based Reinforcement Learning
		- [Tingwu Wang](https://t.co/ja6y9tA496), Xuchan Bao, Ignasi Clavera, Jerrick Hoang, Yeming Wen, Eric Langlois, Shunshi Zhang, Guodong Zhang, Pieter Abbeel, Jimmy Ba
		- University of Toronto & UC Berkeley & Vector Institute
		- [[Project Home]](http://www.cs.toronto.edu/~tingwuwang/mbrl.html) [[Github]](https://github.com/WilsonWangTHU/mbbl) [[Paper]](https://arxiv.org/abs/1907.02057.pdf)
	- 2019 - Exploring Model-based Planning with Policy Networks
		- [Tingwu Wang](https://t.co/ja6y9tA496), Jimmy Ba
		- University of Toronto
		- [[Github]](https://github.com/WilsonWangTHU/POPLIN) [[Paper]](https://arxiv.org/pdf/1906.08649.pdf)
	- 2019 - Baconian: A Unified Opensource Framework for Model-Based Reinforcement Learning
	 	- [Linsen Dong](https://sites.google.com/view/linsendong/), Guanyu Gao, Yuanlong Li, Yonggang Wen
		- Nanyang Technological University
		- [[Github]](https://github.com/Lukeeeeee/baconian-project) [[Paper]](https://arxiv.org/pdf/1904.10762.pdf)
	- ICML'19 Workshop - When to Trust Your Model: Model-Based Policy Optimization
		- [[Project Home]](https://people.eecs.berkeley.edu/~janner/mbpo/) [[Paper]](https://arxiv.org/abs/1906.08253) [[Slide]](topics/data/rl/trust_mbpo.pdf)
	- ICLR'19 - ProMP: Proximal Meta-Policy Search
		- Jonas Rothfuss, Dennis Lee, Ignasi Clavera, Tamim Asfour, Pieter Abbeel
		- UC Berkeley
		- [[Project Home]](https://sites.google.com/view/pro-mp) [[Github]](https://github.com/jonasrothfuss/ProMP) [[Poster]](https://s3.amazonaws.com/postersession.ai/7822e5a9-cb97-40ba-8f8e-8395fa4cf03e.pdf) 

- [Meta-Policy Search’s documentation](https://promp.readthedocs.io/en/latest/index.html), including
	- ProMP: Proximal Meta-Policy Search (Rothfuss et al., 2018)
	- MAML: Model Agnostic Meta-Learning (Finn et al., 2017)
	- E-MAML: Exploration MAML (Al-Shedivat et al., 2018, Stadie et al., 2018)



### RL in Real World

- Challenges of Real-World Reinforcement Learning [[Paper]](https://arxiv.org/pdf/1904.12901.pdf)
	- Gabriel Dulac-Arnold, Daniel Mankowitz, Todd Hester
	- Google Brain, DeepMind
	- 2019

### Sim-to-Real

- Blog
	- [Domain Randomization for Sim2Real Transfer (May, 2019)](https://lilianweng.github.io/lil-log/2019/05/05/domain-randomization.html)
	- [Reliability in Reinforcement Learning (June 6, 2019; Microsoft Research Blog)](https://www.microsoft.com/en-us/research/blog/reliability-in-reinforcement-learning/)
	- [Abstraction and RL: Literature Overview (Mar. 9, 2019)](https://david-abel.github.io/blog/posts/rl_abstr.html)
	- [Meta Reinforcement Learning (June 23, 2019)](https://lilianweng.github.io/lil-log/2019/06/23/meta-reinforcement-learning.html)
	- [Policy Gradient Algorithms](https://lilianweng.github.io/lil-log/2018/04/08/policy-gradient-algorithms.html#d4pg)

### RL Paper Slide and Code

- **(SAC) Soft actor-critic: Off-policy maximum entropy deep reinforcement learning with a stochastic actor**
	- [Tuomas Haarnoja](https://people.eecs.berkeley.edu/~haarnoja/), Aurick Zhou, Pieter Abbeel, Sergey Levine
	- UC Berkeley
	- ICML'18
	- [[Slide]](https://drive.google.com/file/d/1rm49ouRtEH4Usjiem3VGDXKrLScSlSBH/view)[[Github]](https://github.com/haarnoja/sac)[[Blog]](https://bair.berkeley.edu/blog/2018/12/14/sac/)
	- Previous Post: [Learning Diverse Skills via Maximum Entropy Deep Reinforcement Learning (Oct 6, 2017)](https://bair.berkeley.edu/blog/2017/10/06/soft-q-learning/) 
	- Other Paper
		- ICML'18: Latent Space Policies for Hierarchical Reinforcement Learning
			- [[Website]](https://sites.google.com/view/latent-space-deep-rl) [[Paper]](https://arxiv.org/abs/1804.02808) [[Github]](https://github.com/haarnoja/sac/) [[Talk]](https://vimeo.com/312265271)

<p style="text-align:center">
<img src="/topics/img/rl/sac-01.jpg" width="650" />
</p>

<p style="text-align:center">
<img src="/topics/img/rl/sac-02.jpg" width="650" />
</p>

- **(TD3) Addressing Function Approximation Error in Actor-Critic Methods**
	- Scott Fujimoto, Herke van Hoof, David Meger
	- McGill University, University of Amsterdam (阿姆斯特丹大学)
	- ICML'18
	- [[Paper]](http://proceedings.mlr.press/v80/fujimoto18a/fujimoto18a.pdf) [[Github-Pytorch]](https://github.com/sfujim/TD3) [[Talk]](https://vimeo.com/312360735)
	- Other Paper
		- ICML'19: Off-Policy Deep Reinforcement Learning without Exploration
			- Scott Fujimoto · David Meger · Doina Precup
			- [[Slide]](https://icml.cc/media/Slides/icml/2019/hallb(11-11-00)-11-12-05-4583-off-policy_deep.pdf) [[Github]](https://github.com/sfujim/BCQ)


### DRL Workshop

- [NIPS2017: Deep Reinforcement Learning Symposium](https://sites.google.com/view/deeprl-symposium-nips2017)
	- with slides

- [NIPS2018: Deep Reinforcement Learning Workshop](https://sites.google.com/view/deep-rl-workshop-nips-2018/home)
	- with slides

- [NIPS2018: Infer2Control](https://sites.google.com/view/infer2control-nips2018/home)
	- with videos

- [NIPS2018: Workshop on Meta-Learning](http://metalearning.ml/2018/)
	- with slides

- [ICML2018: Exploration in RL](https://sites.google.com/view/erl-2018/)
	- with slides and videos

- [ICML2019: Exploration in RL](https://sites.google.com/view/erl-2019/)
	- with slides and videos

### Exploration

Ian Osband (DeepMind)
- [Homepage](https://iosband.github.io/)
- Phd Thesis (2016): Deep Exploration via Randomized Value Functions
	- [[Thesis]](https://searchworks.stanford.edu/view/11891201)[[Video]](https://www.youtube.com/watch?v=ck4GixLs4ZQ)[[Slide]](https://docs.google.com/presentation/d/1lis0yBGT-uIXnAsi0vlP3SuWD2svMErJWy_LYtfzMOA/edit#slide=id.p)
	- Statistically efficient RL requires "deep exploration". Previous approaches to deep exploration have not been computationally tractable beyond small scale problems. This dissertation presents an alternative approach through the use of randomized value functions. 
- ICML2016: Generalization and Exploration via Randomized Value Functions
	- [[Paper]](https://arxiv.org/abs/1402.0635)[[Talk]](http://techtalks.tv/talks/generalization-and-exploration-via-randomized-value-functions/62467/)[[Poster]](https://iosband.github.io/docs/ICML2016_RLSVI_Poster.pdf)[[Slide]](https://docs.google.com/presentation/d/1OkJjM1EGEHbcJM--98hWTc9fZdlMnegY8NFUToYcrLQ/edit?usp=sharing)

### 深度文章

- [深度强化学习的 18 个关键问题](https://zhuanlan.zhihu.com/p/32153603)
- [知乎专栏：强化学习路在何方？](https://zhuanlan.zhihu.com/p/39999667)
- [The Promise of Hierarchical Reinforcement Learning (Mar. 2019, by Yannis Flet-Berliac)](https://thegradient.pub/the-promise-of-hierarchical-reinforcement-learning/)
- [Reinforcement learning’s foundational flaw (Jul. 2018, by Andrey Kurenkov)](https://thegradient.pub/why-rl-is-flawed/)
	- [AI科技评论译文 - 论强化学习的根本缺陷](https://mp.weixin.qq.com/s?__biz=MzI5NTIxNTg0OA==&mid=2247491939&idx=1&sn=4f67123ee48635672185e6a17c3a2104&chksm=ec5456e4db23dff28ac55411e9012ceee118bee98fb9f9a908a94887fc3f0ecbe9ef9f26074b&mpshare=1&scene=1&srcid=0726AM1AhQc0b552WGcrzCxF#rd)
- [How to fix reinforcement learning (Jul. 2018, by Andrey Kurenkov)](https://thegradient.pub/how-to-fix-rl/)
- [Lessons Learned Reproducing a Deep Reinforcement Learning Paper (Apr. 2018, by Amid Fish)](http://amid.fish/reproducing-deep-rl)
- [Deep Reinforcement Learning Doesn't Work Yet (Feb. 2018, by Alexirpan)](https://www.alexirpan.com/2018/02/14/rl-hard.html)
	- [机器之心译文 - 变革尚未成功：深度强化学习研究的短期悲观与长期乐观](https://mp.weixin.qq.com/s?__biz=MzA3MzI4MjgzMw==&mid=2650739470&idx=1&sn=8556f0261844848c62cae514cfa89103&chksm=871ad770b06d5e66d2b52cf985e70ad4995a1cec5fea7390335356eaa20cd94accad5cab8c4c&mpshare=1&scene=1&srcid=0419H6yX1ITVgMi11tHte6Ll#rd)









