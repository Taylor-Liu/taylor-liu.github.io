---
layout: post
title: Tensorflow学习笔记06 - 常用API
---

### 1. Assign a value to a TensorFlow variable

三种方法：

- op = x.assign(new_value)

```python
import tensorflow as tf

x = tf.Variable(12)
x_assign_op = x.assign(34)

with tf.Session() as sess:

	sess.run(tf.global_variables_initializer())

	print("Before assign: ", sess.run(x))
	sess.run(x_assign_op)
	print("After assign: ", sess.run(x))

"""
output:
	Before assign: 12
	After assign: 34
"""
```

- tf.assign(x, new_value)

```python
import tensorflow as tf

x = tf.Variable(12)
y = tf.assign(x, 34)

with tf.Session() as sess:

	sess.run(tf.global_variables_initializer())

	print("Before assign: ", sess.run(x))
	sess.run(y)
	print("y: ", sess.run(y))
	print("After assign: ", sess.run(x))

"""
output:
	Before assign: 12
	y: 34
	After assign: 34
"""
```

- 直接操作

$$
\nabla_{\theta} J\left(\pi_{\theta}\right)=\underset{\tau \sim \pi_{\theta}}{\mathrm{E}}\left[\sum_{t=0}^{T} \nabla_{\theta} \log \pi_{\theta}\left(a_{t} | s_{t}\right) R(\tau)\right]
$$


### 2. tf.cast


### 3. argmax


### 4. tf.one_hot and reshape


### 5. tf.distributions.Normal


### 6. Others

