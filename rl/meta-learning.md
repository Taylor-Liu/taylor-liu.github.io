---
layout: page
title: Meta Learning
---

## Conference & Workshop

- [Workshop on Meta-Learning (MetaLearn 2018) @ NeurIPS 2018](http://metalearning.ml/2018/)
- [Workshop on Meta-Learning (MetaLearn 2017) @ NeurIPS 2017](http://metalearning.ml/2017/)

## papers

- 2019 - UC Berkeley - NIPS - Meta-Learning with Implicit Gradients（隐式梯度元学习）
	- Aravind Rajeswaran, Chelsea Finn, Sham Kakade, Sergey Levine
	- Abstract: 智能系统的一个核心能力是能够通过借鉴以往的经验快速学习新任务。基于梯度(或优化)的元学习是近年来出现的一种有效的学习方法。在这个范式中，元参数在外部循环中学习，而特定于任务的模型在内部循环中只使用当前任务的少量数据学习。扩展这些方法的一个关键挑战是需要通过内部循环学习过程进行区分，这可能带来相当大的计算和内存负担。利用隐式微分法，提出了隐式MAML算法，该算法只依赖于内部层次优化的解，而不依赖于内部循环优化器所采用的路径。这有效地将元梯度计算与内部循环优化器的选择解耦。因此，我们的方法对内部循环优化器的选择是不可知的，并且可以优雅地处理许多梯度步骤，而不会消失梯度或内存约束。从理论上，我们证明了隐式MAML可以计算精确的元梯度，其内存占用不超过计算单个内循环梯度所需的内存占用，且不增加总计算成本。实验表明，隐式MAML的这些优点可以转化为基于少量样本图像识别基准的经验增益。
	- [[Home]](https://sites.google.com/view/imaml) [[Paper]](http://arxiv.org/abs/1909.04630)

<p style="text-align:center">
	<img src="/rl/data/maml-2.jpeg" />
</p>