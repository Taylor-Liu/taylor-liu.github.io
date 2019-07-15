---
layout: page
title: Model-based RL
---

### Researchers

| People | Department |
| :------ |:--- |
| [Timothy Lillicrap](http://contrastiveconvergence.net/~timothylillicrap/index.php) | DeepMind |
| [Oriol Vinyals](https://ai.google/research/people/OriolVinyals) | DeepMind |
| [Jessica Hamrick](http://www.jesshamrick.com/) | DeepMind |
| [Shixiang Gu](https://sites.google.com/view/gugurus/home) | Google Brain |
| [Danijar Hafner](https://danijar.com/) | Google Brain |
| [Vitchyr H. Pong](http://people.eecs.berkeley.edu/~vitchyr/) | UC Berkeley |
| [Anusha Nagabandi](https://people.eecs.berkeley.edu/~nagaban2/index.html) | UC Berkeley |
| [Ignasi Clavera](https://iclavera.github.io/) | UC Berkeley |
| [Tingwu Wang](https://t.co/ja6y9tA496) | University of Toronto |

### Blog

UC Berkeley
- [Model-based Reinforcement Learning with Neural Network Dynamics (Nov 30, 2017)](https://bair.berkeley.edu/blog/2017/11/30/model-based-rl/)
- [TDM: From Model-Free to Model-Based Deep Reinforcement Learning (Apr 26, 2018)](https://bair.berkeley.edu/blog/2018/04/26/tdm/)

Jonathan Hui
- [RL — LQR & iLQR Linear Quadratic Regulator](https://medium.com/@jonathan_hui/rl-lqr-ilqr-linear-quadratic-regulator-a5de5104c750)
- [RL — Model-based Reinforcement Learning](https://medium.com/@jonathan_hui/rl-model-based-reinforcement-learning-3c2b6f0aa323)

天津包子馅儿
- [高级强化学习系列 第一讲 联合模型的强化学习算法（一）](https://zhuanlan.zhihu.com/p/31045635)
- [高级强化学习系列 第一讲 联合模型的强化学习算法（二）](https://zhuanlan.zhihu.com/p/31084371)
- [高级强化学习系列 第一讲 联合模型的强化学习算法（三）](https://zhuanlan.zhihu.com/p/31344949)

Others
- [Week 6 - Model-based RL](https://hollygrimm.com/rl_modelbased)

### Library

[Meta-Policy Search’s documentation](https://promp.readthedocs.io/en/latest/index.html), including
- ProMP: Proximal Meta-Policy Search (Rothfuss et al., 2018)
- MAML: Model Agnostic Meta-Learning (Finn et al., 2017)
- E-MAML: Exploration MAML (Al-Shedivat et al., 2018, Stadie et al., 2018)

### Papers

**2019 - Dynamics-Aware Unsupervised Discovery of Skills**

- Archit Sharma, Shixiang Gu, Sergey Levine, Vikash Kumar, Karol Hausman
- Google Brain
- [[Project Home]](https://sites.google.com/view/dads-skill)

**2019 - Benchmarking Model-Based Reinforcement Learning**

- [Tingwu Wang](https://t.co/ja6y9tA496), Xuchan Bao, Ignasi Clavera, Jerrick Hoang, Yeming Wen, Eric Langlois, Shunshi Zhang, Guodong Zhang, Pieter Abbeel, Jimmy Ba
- University of Toronto & UC Berkeley & Vector Institute
- [[Project Home]](http://www.cs.toronto.edu/~tingwuwang/mbrl.html) [[Github]](https://github.com/WilsonWangTHU/mbbl) [[Paper]](https://arxiv.org/abs/1907.02057.pdf)

**2019 - Baconian: A Unified Opensource Framework for Model-Based Reinforcement Learning**

- [Linsen Dong](https://sites.google.com/view/linsendong/), Guanyu Gao, Yuanlong Li, Yonggang Wen
- Nanyang Technological University
- [[Github]](https://github.com/Lukeeeeee/baconian-project) [[Paper]](https://arxiv.org/pdf/1904.10762.pdf)

**ICML'19 Workshop - When to Trust Your Model: Model-Based Policy Optimization**

- [[Project Home]](https://people.eecs.berkeley.edu/~janner/mbpo/) [[Paper]](https://arxiv.org/abs/1906.08253) [[Slide]](/topics/data/rl/trust_mbpo.pdf)

**2019 - Exploring Model-based Planning with Policy Networks**

- [Tingwu Wang](https://t.co/ja6y9tA496), Jimmy Ba
- University of Toronto
- [[Github]](https://github.com/WilsonWangTHU/POPLIN) [[Paper]](https://arxiv.org/pdf/1906.08649) 

**ICLR'19 - (SLBO) Algorithmic Framework for Model-based Deep Reinforcement Learning with Theoretical Guarantees**

- Yuping Luo, Huazhe Xu, Yuanzhi Li, Yuandong Tian, Trevor Darrell, Tengyu Ma
- Princeton, UC Berkeley, Facebook, Stanford
- [[Github]](https://github.com/facebookresearch/slbo) [[Poster]](https://s3.amazonaws.com/postersession.ai/ba9846bc-713d-41d7-9683-0fbefe4e7005.pdf) [[Paper]](https://openreview.net/pdf?id=BJe1E2R5KX)

**ICLR'19 - Learning to Adapt in Dynamic, Real-World Environment through Meta-Reinforcement Learning**

- Anusha Nagabandi, Ignasi Clavera, Simin Liu, Ronald S. Fearing, Pieter Abbeel, Sergey Levine, Chelsea Finn
- UC Berkeley
- [[Project Home]](https://sites.google.com/berkeley.edu/metaadaptivecontrol) [[Github]](https://github.com/iclavera/learning_to_adapt) [[Poster]](https://s3.amazonaws.com/postersession.ai/6953f332-e782-4315-b657-10fd02fb10fa.pdf) [[Blog]](https://bair.berkeley.edu/blog/2019/05/06/robot-adapt/)

**ICLR'19 - Deep Online Learning via Meta-Learning: Continual Adaptation for Model-Based RL**

- Anusha Nagabandi, Chelsea Finn, Sergey Levine
- UC Berkeley
- [[Project Home]](https://sites.google.com/berkeley.edu/onlineviameta) [[Paper]](https://openreview.net/pdf?id=HyxAfnA5tm) [[Poster]](https://s3.amazonaws.com/postersession.ai/9ab74406-2565-4a43-a863-e8e4a50e727c.pdf)

**ICLR'19 - ProMP: Proximal Meta-Policy Search**

- Jonas Rothfuss, Dennis Lee, Ignasi Clavera, Tamim Asfour, Pieter Abbeel
- UC Berkeley
- [[Project Home]](https://sites.google.com/view/pro-mp) [[Github]](https://github.com/jonasrothfuss/ProMP) [[Poster]](https://s3.amazonaws.com/postersession.ai/7822e5a9-cb97-40ba-8f8e-8395fa4cf03e.pdf)

**NIPS'18 - (STEVE) Sample-Efficient Reinforcement Learning with Stochastic Ensemble Value Expansion**

- Jacob Buckman, Danijar Hafner, George Tucker, Eugene Brevdo, Honglak Lee
- Google Brain
- [[Project Home]](https://danijar.com/project/steve/) [[Github]](https://github.com/tensorflow/models/tree/master/research/steve) [[Poster]](https://danijar.com/asset/steve/poster.pdf) [[Paper]](https://arxiv.org/pdf/1807.01675.pdf) 

**ICLR'18 - (ME-TRPO) Model-Ensemble Trust-Region Policy Optimization**

- Thanard Kurutach, Ignasi Clavera, Yan Duan, Aviv Tamar, and Pieter Abbeel
- UC Berkeley
- [[Project Home]](https://sites.google.com/view/me-trpo) [[Github]](https://github.com/thanard/me-trpo) [[Paper]](https://openreview.net/pdf?id=SJJinbWRZ) [[Poster]](http://people.eecs.berkeley.edu/~thanard.kurutach/me-trpo-poster.pdf)

**CORL'18 - (MB-MPO) Model-Based Reinforcement Learning via Meta-Policy Optimization**

- Ignasi Clavera, Jonas Rothfuss, John Schulman, Yasuhiro Fujita, Tamim Asfour, Pieter Abbeel
- UC Berkeley
- [[Project Home]](https://sites.google.com/view/mb-mpo/home) [[Github]](https://github.com/jonasrothfuss/model_ensemble_meta_learning)