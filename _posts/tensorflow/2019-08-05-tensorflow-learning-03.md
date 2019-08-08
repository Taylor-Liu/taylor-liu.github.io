---
layout: post
title: Tensorflow学习笔记03 - 基本概念
tags: [tensorflow, deep learning]
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

训练神经网络来解决二分类问题的例子：

```python
import tensorflow as tf
from numpy.random import RandomState

# 1. 定义神经网络的参数，输入和输出节点
batch_size = 8
w1 = tf.Variable(tf.random_normal([2,3], stddev=1, seed=1))
w2 = tf.Variable(tf.random_normal([3,1], stddev=1, seed=1))
x = tf.placeholder(tf.float32, shape=(None, 2), name='x-input')
y_ = tf.placeholder(tf.float32, shape=(None, 1), name='y-input')

# 2. 定义前向传播过程，损失函数及反向传播算法
a = tf.matmul(x, w1)
y = tf.matmul(a, w2)
y = tf.sigmoid(y)

cross_entropy = -tf.reduce_mean(y_ * tf.log(tf.clip_by_value(y, 1e-10, 1.0))
                               + (1 - y_) * tf.log(tf.clip_by_value(1 - y, 1e-10, 1.0)))
train_step = tf.train.AdamOptimizer(0.001).minimize(cross_entropy)

# 3. 生成模拟数据集
rdm = RandomState(1)
X = rdm.rand(128, 2)
Y = [[int(x1 + x2 < 1)] for (x1, x2) in X]

# 4. 创建一个会话来运行Tensorflow程序
with tf.Session() as sess:
    
    init_op = tf.global_variables_initializer()
    sess.run(init_op)
    
    # 输出目前（未经训练）的参数取值
    print(sess.run(w1))
    print(sess.run(w1))
    print('\n')
    
    # 训练模型
    STEPS = 5000
    for i in range(STEPS):
        start = (i * batch_size) % 128
        end = (i * batch_size) % 128 + batch_size
        sess.run([train_step, y, y_], feed_dict={x: X[start:end], y_: Y[start:end]})
        
        if i % 1000 == 0:
            total_cross_entropy = sess.run(cross_entropy, feed_dict={x: X, y_: Y})
            print('After %d trainining step(s), cross entropy on all data is %g' % (i, total_cross_entropy))
            
    # 输出训练后的参数取值
    print('\n')
    print(sess.run(w1))
    print(sess.run(w2))

"""
Output:
    [[-0.8113182   1.4845988   0.06532937]
     [-2.4427042   0.0992484   0.5912243 ]]
    [[-0.8113182   1.4845988   0.06532937]
     [-2.4427042   0.0992484   0.5912243 ]]


    After 0 trainining step(s), cross entropy on all data is 1.89805
    After 1000 trainining step(s), cross entropy on all data is 0.655075
    After 2000 trainining step(s), cross entropy on all data is 0.626172
    After 3000 trainining step(s), cross entropy on all data is 0.615096
    After 4000 trainining step(s), cross entropy on all data is 0.610309


    [[ 0.02476983  0.56948674  1.6921941 ]
     [-2.1977348  -0.23668921  1.1143895 ]]
    [[-0.45544702]
     [ 0.49110925]
     [-0.98110336]]
"""
```


## 8. Training epoch/batch












