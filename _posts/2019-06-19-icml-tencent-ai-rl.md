---
layout: post
title: ICML2019 | 腾讯AI Lab强化学习论文
tags: [ICML, reinforcement learning, AI Lab, Tencent]
---

**Grid-Wise Control for Multi-Agent Reinforcement Learning in Video Game AI**

- Lei Han · Peng Sun · Yali Du · Jiechao Xiong · Qing Wang · Xinghai Sun · Han Liu · Tong Zhang
- [[Paper]](http://proceedings.mlr.press/v97/han19a/han19a.pdf) [[Slide]](https://icml.cc/media/Slides/icml/2019/201(11-11-00)-11-11-30-4821-grid-wise_contr.pdf)

本文由腾讯AI Lab主导，与悉尼科技大学合作完成，研究了游戏AI中的多智能体强化学习问题，其中智能体分布在网格世界环境中，并且智能体的数量可以在游戏中任意变化。`上述问题的难点在于灵活地处理变化数量的智能体，并且同时实现智能体之间的高质量合作。`目前已有的强化学习方法通常需要在这两个关注点之间做取舍。

本文提出了一种新的网络结构，可以学习`任意数量的智能体在空间上的一种综合的表达`，然后输出一个网格地图，对其中每一个网格都预测一个动作。每个智能体采纳它自己所占网格对应的动作，并且被独立的控制。通过将状态也表示成一种网格结构，然后采用了一种基于卷积操作的编码-解码结构，并使用这种结构作为策略网络。上面提出的结构可以通过卷积操作的感受野非常自然地处理多智能体合作的问题。

<p style="text-align:center">
	<img src="/topics/img/icml19/tencent-multi-rl.jpeg" width="650" />
	<br /> 网格粒度控制架构示意图。虚线矩形框中即为策略网络，右侧则是策略函数与价值函数。
</p>

此外，由于卷积核在空间上是被共享的，所以这种操作可以实现快速的并行探索，即当某一个智能体探索到了一个好的状态动作转移，那么这个信息会立刻共享给其他智能体。上述网络结构可以很便捷地与多种常用的强化学习算法结合，比如PPO和Q学习算法。

研究者在《星际争霸II》的战斗场景中做了大量的实验并进行了详尽的分析，结果表明该方法十分有效。下面是一段演示视频：

<iframe width="560" height="315" src="https://www.youtube.com/embed/LTcr01iTgZA" frameborder="0" allowfullscreen></iframe>

`应用价值：`本文对基于网格世界的多智能体强化学习问题提出了一种新的学习架构，可以灵活处理数量变化的智能体个数，可以有效的应用在视频游戏AI和真实世界多种场景中。

### 参考资料

- [ICML 2018: 腾讯AI Lab详解16篇入选论文](https://mp.weixin.qq.com/s?__biz=MzIzOTg4MjEwNw==&mid=2247483807&idx=1&sn=d90e8996f7533dcc9e83f9f171bb4525&scene=21#wechat_redirect)
- [ICML 2019: 腾讯AI Lab入选论文详解：从协同通道剪枝到多智能体强化学习](https://mp.weixin.qq.com/s?__biz=MzIzOTg4MjEwNw==&mid=2247484146&idx=1&sn=7b5d38201a597d76ea22fba87083249e&chksm=e92218e6de5591f0082436635bde71450f998bfec3878722b5d67e3932dce3120d7aa7ef7778&mpshare=1&scene=1&srcid=#rd)