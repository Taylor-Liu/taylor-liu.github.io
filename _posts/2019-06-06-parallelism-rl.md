---
layout: post
title: Parallelism in RL
---

Questions

- When to use CPU?
- When to use GPU?
- What can we parallelize in RL?

---

Share some great slides.

### 1. Parallelism in RL 

- From: 2017 - UC Berkeley - CS294_112 - Lecture_16
- Sergey Levine
- [[Slide]]()

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
- [[Slide]]()

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

### 3. Multi-GPU Accelerated Methods for Deep Reinforcement Learning

- From: GTC2018 - UC Berkeley
- Adam Stooke, Pieter Abbeel
- [[Slide]]()

Outline
- Background
	- Reinforcement Learning (RL)
	- Deep RL Algorithms
- Neural Network (NN) Inference Engine
	- CPU: Simulators, GPU: NN
- Multi-GPU Framework for RL
	- Synchronous & Asynchronous Optimization
	- Example Results
- Scaling Effects on Learning
	- Batch Size
	- Update Rule

### 4. Doing More with More: Recent Achievements in Large-Scale Deep Reinforcement Learning

- From: GTC2019 - UC Berkeley
- Adam Stooke, Pieter Abbeel
- [[Slide]]()

Outline
- Algorithms & Frameworks (Atari Legacy)
	- A3C / DQN (DeepMind)
	- IMPALA / Ape-X (DeepMind)
	- Accel RL (Berkeley)
- Large-Scale Projects (Beyond Atari)
	- AlpaGo Zero (DeepMind)
	- Capture the Flag (DeepMind)
		- Population Based Training
	- Dota2 (OpenAI)
	- Summary of Techniques

---

Papers:


















