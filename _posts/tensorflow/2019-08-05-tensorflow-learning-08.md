---
layout: post
title: Tensorflow学习笔记08 - Gradient
tags: [tensorflow, deep learning]
---

---
**Table of Contents**
* TOC
{:toc}
---

## 1. tf.gradient

## 2. tf.stop_gradient

参考：
- [关于tf.stop_gradient的使用及理解](https://blog.csdn.net/u013745804/article/details/79589514)
- [OpenAI Spinningup - Tensorflow Tutorial (Slide)](https://github.com/openai/spinningup-workshop/blob/master/tensorflow_review/tf_review_session.pdf)
- [tf.stop_gradient API](https://www.tensorflow.org/api_docs/python/tf/stop_gradient)

You may want to prevent backpropagation through a particular tensor: can do this with tf.stop_gradient

- Example: in DQN, where we want to minimize a mean-square Bellman error with respect to params of current network but not target network

```python
o = tf.placeholder(shape=(None,dim_o),dtype=tf.float32)
a = tf.placeholder(shape=(None,),dtype=tf.int32)
o2 = tf.placeholder(shape=(None,dim_o),dtype=tf.float32)
r = tf.placeholder(shape=(None,),dtype=tf.float32)
with tf.variable_scope(’main’):
q = build_network(o) # b x a
with tf.variable_scope(’target’):
q_targ = build_network(o2) # b x a
q_a = tf.reduce_sum(q * tf.one_hot(a, num_actions),1) # b
q_targ_a = tf.reduce_max(q_targ,1) # b
target = r + gamma * q_targ_a
target = tf.stop_gradient(target)
loss = tf.reduce_mean(tf.square(q_a - target))
# later on, make assign statement so q_targ lags q
```

---

DQN中为什么要对q_target进行stop_gradient? 

`无stop_gradient的情况`

这个版本就是人们写得相对较多的版本了，代码如下：

```python
self.q_target = tf.placeholder(tf.float32, [None, self.n_actions], name='Q_target')  # for calculating loss

with tf.variable_scope('loss'):
    self.loss = tf.reduce_mean(tf.squared_difference(self.q_target, self.q_eval))

with tf.variable_scope('train'):
    self._train_op = tf.train.RMSPropOptimizer(self.lr).minimize(self.loss)
```

上面这一小段代码就是DQN的常规写法了。我们知道，在DQN中会维持两个网络，一个eval net，一个target net。我们对eval net的参数更新是通过MSE + GD来更新的，而MSE的计算将用到target net对下一状态的估值，通常的做法是对eval net设置一个placeholder，也即引入一个输入，用这个placeholder计算loss。

`有stop_gradient的情况`

如果我们使用stop_gradient的话，又是如何解决的呢？

 ```python
with tf.variable_scope('q_target'):
    q_target = self.r + self.gamma * tf.reduce_max(self.q_next, axis=1, name='Qmax_s_')    # shape=(None, )
    self.q_target = tf.stop_gradient(q_target)

with tf.variable_scope('loss'):
    self.loss = tf.reduce_mean(tf.squared_difference(self.q_target, self.q_eval_wrt_a, name='TD_error'))
 ```

这段代码中，我们使用tf.stop_gradient对q_target的反传进行截断，得到self.q_target这个op（运行时就是Tensor了），然后利用通过截断反传得到的self.q_target来计算loss，并没有使用feed_dict。

`不同之处`

这两者究竟有什么内在区别？我们知道，在TensorFlow中，维持着一些op，op在被执行之后将变为常量Tensor（指的不是Variable意义的Tensor），这些计算（eval/run）得到的常量Tensor可以看作是我们自己给出的输入数据。 

第一种方法中placeholder输入的本身就是计算好了的q_target，也就是说我们通过feed_dict，将对target net进行计算得到的一个q_target Tensor传入placeholder中，当做常量来对待，我们可以把一次计算（eval/run）看作是一次截图，得到当时各个op的值。这样的话，我们对于eval net中loss的反传就不会影响到target net了。 

第二种方法中直接拿target net中的q_target这个op来计算eval net中的loss显然是不妥的，因为我们对loss进行反传时将会影响到target net，这不是我们想看到的结果。所以，这里引入stop_gradient来对从loss到target net的反传进行截断，换句话说，通过self.q_target = tf.stop_gradient(q_target)，将原本为TensorFlow计算图中的一个op（节点）转为一个常量self.q_target，这时候对于loss的求导反传就不会传到target net去了。

## 3. manual gradient 和 gradient descent magic

## 4. compute_gradient 和 apply_gradient



























