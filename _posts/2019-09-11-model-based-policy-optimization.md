---
layout: post
title: Model Based Policy Optimization
subtitle: Reviewing recent advances in model-based reinforcement learning
tags: [reinforcement learning]
---

Author: [Or Rivlin](https://towardsdatascience.com/@or.rivlin.mail)  
Date: Aug. 1, 2019  
From: [https://towardsdatascience.com/model-based-policy-optimization-d7e099c73d8](https://towardsdatascience.com/model-based-policy-optimization-d7e099c73d8)

---
**Table of Contents**
* TOC
{:toc}
---

**Introduction**

Deep reinforcement learning has gained much fame in recent years due to some amazing successes in videos games such as Atari, simulated robotic control environments such as Mujoco and in games such as Chess, Go and Poker. A distinct feature of most RL success stories is the use of simulated environments that enable highly efficient data generation through trial and error. This is very important because most state of the art RL algorithms require huge quantities of data to achieve their great performance — often on the order of hundreds of millions of interactions with the environment, sometimes even billions.

A key reason to this sample inefficiency is the fact that most state of the art RL algorithms belong to the **Model-Free** family, which means that they are very general learning algorithms which assume no knowledge of the environment or the reward function, making them completely reliant on direct interactions. This is obviously very different from the way we humans learn to perform tasks, as we can use our experience to imagine the outcomes of our actions and plan before attempting to perform the task. For example, when a person tries to walk over a wet floor, he might slip on his first steps, but rapidly adjust his internal model of how foot placement and moving direction affects stability, and most likely perform much better on his next steps. Unlike Model-free algorithms, we don’t just try different walking styles and use feedback (did we fall or not) to eventually figure out the right way.

But if those general Model-free algorithms work so well on these difficult tasks, why bother with anything else? This is because not everything can be easily simulated reliably, and in many real-world use-cases our simulations are not nearly accurate enough that we could deploy a model trained using them in our target environment. An obvious example of such a case is that of robotic control and planning, as even simple robotic systems cannot be accurately simulated, not to mention complex robotic systems. But even if we could create accurate simulations, it would likely be a major undertaking, and would only apply to that specific robot model. Bridging the gap between simulation and real robots is an area of active research and I have previously [written about some of the interesting ideas out there](/reinforcement-learning-for-real-world-robotics-148c81dbdcff).

In these setting were we don’t have a reliable simulation or that running a simulation is very time consuming or expensive, we cannot hope to use a learning algorithm that requires a billion interactions with the environment as it will take a prohibitive amount of time or be unacceptably costly. It seems that we could benefit from a different paradigm.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/01.png" />
</p>

**Model Based Planning**

What if we were solving a problem for which we actually knew the model or had a good enough approximation? Could we use that knowledge to make better decisions or to learn a better policy? This is actually a very common case in areas such as automated planning, combinatorial optimization and control. In many control applications we might have an approximate analytic model of the dynamics due to domain knowledge of the specific problem (often in the form of a linear model) which allows us to plan ahead using techniques such as Model Predictive Control (MPC).

In MPC we plan ahead for a fixed time horizon using our approximate model to “simulate” the states our system transitions to due to the actions we take. Say we wish an airplane to follow a target trajectory, we can use the sum of distances between the states we rolled out using our model (with some initial actions that can be chosen randomly) and the states in the target trajectory, and take the derivative of the cost function with respect to the actions (since both cost function and approximate model are differentiable) and minimize the cost function using gradient descent. In this case we are not learning a policy (although we could try to fit a model to predict the optimized actions if we wanted) but using our model to plan.

Another approach could be to use our known model to learn a policy, and a very famous example of such a case is that of AlphaGo Zero (AGZ). In AlphaGo Zero we have a perfect model of the game; we know how the state of the game board changes given an action perfectly well, and can use that knowledge within tree search algorithms such as Monte-Carlo Tree Search (MCTS).

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/02.png" />
</p>

In AlphaGo Zero we try to learn a policy and a value function to be used inside an MCTS algorithm, and the MCTS search results are in turn used to improve the policy. This is possible since we can “look ahead” and reason about the likely consequences of actions our policy takes, before actually committing to a move. This procedure has proven to be very effective, resulting in a system that could achieve super-human performance against the world’s strongest players by learning from playing against itself.

**Model Based Reinforcement Learning**

What if we could achieve the aforementioned benefits even in problems for which we do not know the model? After all, a model of the environment is a function mapping from a state-action to a transition probability over the next states and the reward, and so perhaps we can learn that function from interactions with the environment and apply that learned model to either plan ahead or to generate large quantities of “simulated rollouts” with which we can improve our policy, thus requiring much less interactions with the real system (which is costly). Our agent could interact with the environment to gather real data, and use supervised learning methods to fit a model of the transition function and the reward. Once we have a good model, we can use it to perform MPC-like planning during deployment or generate vast amounts of fictitious training data to improve a learned policy that would be used in deployment (avoiding real-time planning can be desirable in hardware constrained or time critical applications).

While this idea appears intuitive and powerful, as is many times the case — things are not so simple. Several problems arise when trying to learn a model of the environment in the context of reinforcement learning, and these have given rise to a whole research field called Model Based Reinforcement Learning.

**Compounding errors**

Inevitably, a learned model will not be perfectly precise, and small errors are compounded and can grow rapidly as we propagate our learned model further in time. These compounding errors make any plans we produce through MPC-like planning and any fictitious data we generate unreliable, introducing bias to our plans and policies. This is one of the factors that contribute to the fact that model-based RL methods tend to achieve lower asymptotic performances than model-free methods.

A common workaround is to use a very biased model, which could possibly generalize better if chosen intelligently. For example, if our environment dynamics can be reasonably approximated with a linear model, we could possibly achieve good generalization and excellent sample complexity due to the severe restriction on the model class, but this is obviously unrealistic for all but the simplest problems. A common model class used in more practical situations with good results is Gaussian Processes, which can learn effectively from very few examples and also give a measure of uncertainty in its predictions. However, Gaussian Processes do net scale well to large data regimes and can be expensive to query during prediction. Another way to introduce bias is to use domain knowledge, and [I have previously written about this in another post](/robotic-control-with-graph-networks-f1b8d22b8c86)**.**

This highlights an interesting trade-off in model class selection; if we choose a low capacity model we might get good performance in the small data regime that occurs at the beginning of training, but fail to take advantage of the larger data regimes that are typical of later stages, when we have gathered enough data. On the other, if we use a high capacity model such as a deep neural network, we might easily overfit at the low data regime, but could take advantage of larger data quantities to get a more accurate model.

**Model exploitation**

Another outcome of an imperfect model arises when we try to optimize trajectories or policies using our learned model. A common occurrence is that in some poorly approximated areas of the state space, our model might predict falsely high rewards, prompting our policy or search algorithm to “actively” search out these areas, even if our model is mostly accurate. Since these errors are random artifacts of our specific model parameters, they are very hard to avoid, especially in high capacity model classes such as deep neural networks. This problem could possibly be handled if we could have some sense of model uncertainty, in which we can measure how “familiar” states are, and thus approach unfamiliar states with caution when optimizing instead of greedily seeking out false high rewards.

There is a large volume of research papers regarding model-based reinforcement learning with techniques to mitigate the problems I mentioned above, I will now look at two recent papers that I liked and examine how they dealt with these issues.

**PETS — Probabilistic Ensembles with Trajectory Sampling**

This 2018 paper takes the route of learning a model to be used for planning, instead of learning a policy. The authors recognize two kinds of uncertainty that must be dealt with: aleatoric uncertainty which is the inherent stochasticity in the environment, and epistemic uncertainty which reflects the model’s confidence regarding different input state-actions.

Typically, neural networks are used as deterministic models, as in the case of regression problems. In these cases, the neural network outputs numbers and they are treated as the prediction, without giving any information on confidence. While the output can be viewed as the mean of a distribution such as a gaussian, this is not helpful since we do not know anything about the variance of the output distribution. In the PETS paper, the authors instead use a probabilistic neural network who’s output parametrizes gaussian distributions over the next state and reward. When training such a model on environment transitions data, instead of using mean squared error as the loss, we use the negative log likelihood of the true next state under the distribution predicted by our model. This allows us to model the inherent stochasticity in the environment, as we would like to distinguish between this type and the other one, and avoid trying to “explore” transitions with high variance, unlike states of who’s transitions we are not certain about due to insufficient data.

To tackle the second type of uncertainty, the authors replaced the single learned model with an ensembles of learned models, each trained on an separate sampling of the dataset of true environment interactions. When aggregating the predictions of multiple different models we can smooth out their individual quirks and errors, somewhat akin to how Random forest improves over the performance of decision trees by aggregating different models. Using an ensemble of models, the optimization algorithm has a much harder time exploiting insufficiently explored states since the predictions given by each model will tend to have high variance and smaller bias, and the ensemble technique will lower the variance.

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/03.png" />
</p>

In the above illustration from the paper, we can see that the aggregate of two different models helps reduce error in unexplored states, and helps get a sense of the uncertainty present by measuring the variance in the ensemble.

In the PETS algorithm, the learned model ensemble is used to plan ahead by using a rather complicated sampling scheme in transitions are predicted using alternating models from the ensemble, and an optimization algorithm named Cross Entropy Method (not the cross entropy loss function…) is used to refine the actions in the plan. Using this algorithm, the authors could gain performances comparable to state-of-the-art model-free RL algorithms such as Proximal Policy Optimization and Soft Actor Critic, in just a handful of trials (around 100K timesteps).

**MBPO — Model Based Policy Optimization**

A more recent paper, called “When to trust your model: model-based policy optimization” takes a different route and instead of using a learned model of the environment to plan, uses it to gather fictitious data to train a policy. The paper details a very interesting theoretical investigation of model usage in RL, and uses an empirical evaluation of the generalization capabilities of neural networks to justify using learned model predictions.

In MBPO, the authors adopt the ensemble of probabilistic neural networks from the PETS paper, but introduce a nice and simple way to use that ensemble to generate training data. As we discussed before, compounding model errors make learning tasks with long horizons very difficult, since in order to generate data we sample from the distribution of initial states and propagate forward using our learned model, increasing errors along the way. In MBPO however, the authors suggest a method of disentangling the task horizon and the model propagation horizon by starting from random states seen previously during interaction with the environment and propagating short trajectories forward. This way we trade few long trajectories with large errors with many short trajectories with smaller errors.

The MBPO algorithm can briefly summarized as follows:

<p style="text-align:center">
	<img src="/posts-data/2019-09-11/04.png" />
</p>

To sample trajectories using the ensembles, the authors suggest to simply choose a model uniformly at each time step, and for the policy optimization step they chose Soft Actor Critic, which is a state-of-the-art off policy RL algorithm. Using all these techniques, the authors achieve results that are on par with the best model-free algorithms, and surpass other model-based methods such as PETS.

This seems to be a promising direction for the adoption of RL to physical systems, at least from the perspective of sample complexity. There are other difficult challenges such as reward specification and detection on a physical system, and safety issues, but reducing sample complexity to a reasonable level is an important step.

Disclaimer: the views expressed in this article are those of the author and do not reflect those of IBM.