---
layout: post
title: Tensorflow学习笔记01
---

### 1. 基本概念

- 节点（constant、placeholder、Variable）

### 2. 细节问题

#### 2.1 tensorflow 张量的阶、形状、数据类型及None在tensor中表示的意思

[https://www.cnblogs.com/welhzh/p/6554872.html](https://www.cnblogs.com/welhzh/p/6554872.html)

```python
x = tf.placeholder(tf.float32, [None, 784])
```

x isn't a specific value. It's a placeholder, a value that we'll input when we ask TensorFlow to run a computation. We want to be able to input any number of MNIST images, each flattened into a 784-dimensional vector. We represent this as a 2-D tensor of floating-point numbers, with a shape [None, 784]. (`Here None means that a dimension can be of any length.`) 注：这里的“None”表示其可以是任意长度

#### 2.2 tensorflow函数解析：Session.run和Tensor.eval

[http://blog.csdn.net/zcf1784266476/article/details/70259676](http://blog.csdn.net/zcf1784266476/article/details/70259676)

这其中最重要的区别就在于你可以使用`sess.run()`在同一步获取多个tensor中的值，例如：

```python
t = tf.constant(42.0)
u = tf.constant(37.0)
tu = tf.mul(t, u)
ut = tf.mul(U, t)
with sess.as_default():
	tu.eval() # runs one step
	ut.eval() # runs one step
	sess.run([tu, ut]) # evaluates both tensors in a single step
```

### 3. Numpy学习

numpy.random.choice()随机选取内容, [https://docs.scipy.org/doc/numpy/reference/generated/numpy.random.choice.html](https://docs.scipy.org/doc/numpy/reference/generated/numpy.random.choice.html)

### 4. 博客学习

一文学会用 Tensorflow 搭建神经网络, [https://www.jianshu.com/p/e112012a4b2d](https://www.jianshu.com/p/e112012a4b2d)

### 5. 教程学习

- [Github (MorvanZhou/Tensorflow-Tutorial)](https://github.com/MorvanZhou/Tensorflow-Tutorial)
- [Google机器学习速成课程（使用 TensorFlow API）](https://developers.google.cn/machine-learning/crash-course/prereqs-and-prework)

### 6. 数据预处理

标准化（normalization）

- 数据的标准化（normalization）是将数据按比例缩放，使之落入一个小的特定区间。在一些数据比较和评价中常用到。典型的有归一化法，还有比如极值法、`标准差法`。

归一化

- 归一化方法的主要有两种形式：一种是把数变为（0，1）之间的小数，一种是把有量纲表达式变为无量纲表达式。在数字信号处理中是简化计算的有效方式。

标准差标准化 (z-score standardization)

$$
x^*=\frac{x-\mu}{\sigma}
$$

经过处理的数据符合标准正态分布，均值为$$0$$，标准差为$$1$$

```python
# 使用scikit-learn函数

```














