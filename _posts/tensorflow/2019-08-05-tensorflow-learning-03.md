---
layout: post
title: Tensorflow学习笔记03 - 基本概念
---

## 0. Hello World

```python
import tensorflow as tf

# Create a constant op
# This op is added as a node to the default graph
hello = tf.constant("Hello, Tensorflow!")constant

# start a TF session
sess = tf.Session()

# run the op and get result
print(sess.run(hello))
```

## 1. 计算模型：计算图 (tf.Graph)

Tensorflow 中的所有计算都会被转化为计算图上的节点

Tensorflow中的每一个计算都是计算图上的一个节点，而节点之间的边描述了计算之间的依赖关系

Tensorflow 程序一般可以分为两个阶段
* 阶段一：定义计算图中所有的计算
* 阶段二：执行计算


## 2. 数据模型：张量 (tf.Tensor)

从功能的角度，张量可以被简单理解为多维数组
* 零阶张量：表示标量 (scalar)，也就是一个数
* 一阶张量：表示向量 (vector)，也就是一个一维数组，例：shape(2, )
*  n阶张量：可以理解为一个n维数组

张量的三个属性：
* 名字 (name)
* 维度 (shape)
* 类型 (type)

张量的类型
* 实数：tf.float32，tf.float64
* 整数：tf.int8，tf.int16，tf.int32，tf.int64，tf.uint8
* 布尔型：tf.bool
* 复数型：tf.complex64，tf.complex128

！！！！张量是Tensorflow的数据类型，Tensorflow中所有运算的输入、输出都是张量。
！！！！张量本身并不存储任何数据，它只是对运算结果的引用。


## 3. 运行模型：会话 (tf.Session)


## 4. 基本单位


## 5. 集合（collection）


## 6. 常用的优化算法


## 7. 训练神经网络的过程（从不同角度去看）


## 8. Training epoch/batch
