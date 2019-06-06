---
layout: post
title: Parallelism in RL
---

Questions

- When to use CPU?
- When to use GPU?
- What can we parallelize in rl?

---

Share some great slides.

### 1. Parallelism in RL [[Slide]]()

- From: 2017 - UC Berkeley - CS294_112 - Lecture_16
- Speaker: Sergey Levine

Outline
- What can we parallelize?
- Case studies: specific parallel RL methods
- Tradeoffs & considerations
- Goals
	- Understand the high-level anatomy of reinforcement learning algorithms
	- Understand standard strategies for parallelization
	- Tradeoffs of different parallel methods

### 2. Distributed RL

- From: 2018 - UC Berkeley - CS294_112 - lecture_21
- Richard Liaw, Eric Liang

Outline
- Common Computational Patterns for RL
- History of large scale distributed RL
	- 2013/2015: DQN
	- 2015: General Reinforcement Learning Architecture (GORILA)
	- 2016: Asynchronous Advantage Actor Critic (A3C)
	- 2018: Distributed Prioritized Experience Replay (Ape-X)
	- 2018: Importance Weighted Actor-Learner Architectures (IMPALA)
- Other interesting distributed architectures
	- AlphaZero
	- Evolution Strategies
- RLlib: Abstractions for Distributed Reinforcement Learning (ICML'18)

---
