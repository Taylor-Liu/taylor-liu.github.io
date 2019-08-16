---
layout: post
title: Tensorflow学习笔记06 - 常用API
tags: [tensorflow, deep learning]
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


### 2. tf.cast


### 3. argmax


### 4. tf.one_hot and reshape


### 5. tf.distributions.Normal


### 6. Others

`tf.squeeze()`

```python
squeeze(
    input,
    axis=None,
    name=None,
    squeeze_dims=None
)
```

该函数返回一个张量，这个张量是将原始input中所有维度为1的那些维都删掉的结果。`axis`可以用来指定要删掉的为1的维度，**此处要注意指定的维度必须确保其是1，否则会报错**

```python
>>> y = tf.squeeze(inputs, [0, 1], name='squeeze')
>>> ValueError: Can not squeeze dim[0], expected a dimension of 1, got 32 for 'squeeze' (op: 'Squeeze') with input shapes: [32,1,1,3].
```

例子：

```python
#  't' 是一个维度是[1, 2, 1, 3, 1, 1]的张量
tf.shape(tf.squeeze(t))   # [2, 3]， 默认删除所有为1的维度

# 't' 是一个维度[1, 2, 1, 3, 1, 1]的张量
tf.shape(tf.squeeze(t, [2, 4]))  # [1, 2, 3, 1]，标号从零开始，只删掉了2和4维的1
```




























