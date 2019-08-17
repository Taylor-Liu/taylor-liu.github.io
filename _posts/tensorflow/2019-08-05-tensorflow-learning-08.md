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

If you want to write a custom optimizer you may want to work with gradients directly. You can do this using `tf.gradients`.

### 1.1 使用TensorFlow内置的优化器对MNIST数据集进行softmax回归

在使用`tf.gradients`实现梯度下降之前，我们先尝试使用 TensorFlow 的内置优化器（比如 GradientDescentOptimizer）来解决MNIST数据集分类问题。

```python
import tensorflow as tf

# Import MNIST data
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets("/tmp/data/", one_hot=True)

# Parameters
learning_rate = 0.01
training_epochs = 10
batch_size = 100
display_step = 1


# tf Graph Input
x = tf.placeholder(tf.float32, [None, 784]) # mnist data image of shape 28*28=784
y = tf.placeholder(tf.float32, [None, 10]) # 0-9 digits recognition => 10 classes

# Set model weights
W = tf.Variable(tf.zeros([784, 10]))
b = tf.Variable(tf.zeros([10]))

# Construct model
pred = tf.nn.softmax(tf.matmul(x, W) + b) # Softmax

# Minimize error using cross entropy
cost = tf.reduce_mean(-tf.reduce_sum(y*tf.log(pred), reduction_indices=1))

optimizer = tf.train.GradientDescentOptimizer(learning_rate).minimize(cost)

# Start training
with tf.Session() as sess:
    sess.run(tf.global_variables_initializer())

    # Training cycle
    for epoch in range(training_epochs):
        avg_cost = 0.
        total_batch = int(mnist.train.num_examples/batch_size)
        # Loop over all batches
        for i in range(total_batch):
            batch_xs, batch_ys = mnist.train.next_batch(batch_size)
            # Fit training using batch data
            _, c = sess.run([optimizer, cost], feed_dict={x: batch_xs,
                                                       y: batch_ys})
            
#             print(__w)
            
            # Compute average loss
            avg_cost += c / total_batch
        # Display logs per epoch step
        if (epoch+1) % display_step == 0:
#             print(sess.run(W))
            print ("Epoch:", '%04d' % (epoch+1), "cost=", "{:.9f}".format(avg_cost))

    print ("Optimization Finished!")

    # Test model
    correct_prediction = tf.equal(tf.argmax(pred, 1), tf.argmax(y, 1))
    # Calculate accuracy for 3000 examples
    accuracy = tf.reduce_mean(tf.cast(correct_prediction, tf.float32))
    print ("Accuracy:", accuracy.eval({x: mnist.test.images[:3000], y: mnist.test.labels[:3000]}))
    
    
#### Output
    
# Extracting /tmp/data/train-images-idx3-ubyte.gz
# Extracting /tmp/data/train-labels-idx1-ubyte.gz
# Extracting /tmp/data/t10k-images-idx3-ubyte.gz
# Extracting /tmp/data/t10k-labels-idx1-ubyte.gz
# Epoch: 0001 cost= 1.184285608
# Epoch: 0002 cost= 0.665428013
# Epoch: 0003 cost= 0.552858426
# Epoch: 0004 cost= 0.498728328
# Epoch: 0005 cost= 0.465593693
# Epoch: 0006 cost= 0.442609185
# Epoch: 0007 cost= 0.425552949
# Epoch: 0008 cost= 0.412188290
# Epoch: 0009 cost= 0.401390140
# Epoch: 0010 cost= 0.392354651
# Optimization Finished!
# Accuracy: 0.873333
```

> 注：上面代码利用了tensorflow内置的优化器来计算损失值，如果想自己计算梯度和更新权重，可以利用tf.gradients

### 1.2 使用tf.gradients对MNIST数据集进行softmax回归

通过梯度下降公式，权重的更新方式如下：

$$
\begin{array}{l}{\text { Repeat until convergence }\{ } \\ {\qquad \theta_{j} \leftarrow \theta_{j}-\alpha \frac{\partial}{\partial \theta_{j}} J(\theta)}\end{array}
$$

为了实现梯度下降，这里将不使用优化器的代码，而是采用自己写的权重更新。

因为这里有权重矩阵`w`和偏差项矩阵`b`，所以我们需要去计算这些矩阵的梯度。所以实现的代码如下：

```python
# Computing the gradient of cost with respect to W and b
grad_W, grad_b = tf.gradients(xs=[W, b], ys=cost)

# Gradient Step
new_W = W.assign(W - learning_rate * grad_W)
new_b = b.assign(b - learning_rate * grad_b)
```

上面代码相当于tensorflow内置的优化器所完成的事情：

```python
train_op = tf.train.GradientDescentOptimizer(learning_rate).minimize(cost)
```

在调用minimize方法的时候，底层实际做了两件事

- 计算所有`trainable variables`的`gradients`
- Apply them to `variables`

随后, 在我们`sess.run(train_op)`的时候, 会对`variables`进行更新

之后，只需要在会话中运行这个计算图即可。代码如下：

```python
# Fit training using batch data
            _, _,  c = sess.run([new_W, new_b ,cost], feed_dict={x: batch_xs, y: batch_ys})
```

> 注：这里不需要new_W和new_b的输出，用“_”来忽略这些变量

完整代码如下：

```python
import tensorflow as tf

# Import MNIST data
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets("/tmp/data/", one_hot=True)

# Parameters
learning_rate = 0.01
training_epochs = 10
batch_size = 100
display_step = 1

# Parameters
learning_rate = 0.01
training_epochs = 10
batch_size = 100
display_step = 1

# tf Graph Input
x = tf.placeholder(tf.float32, [None, 784]) # mnist data image of shape 28*28=784
y = tf.placeholder(tf.float32, [None, 10]) # 0-9 digits recognition => 10 classes

# Set model weights
W = tf.Variable(tf.zeros([784, 10]))
b = tf.Variable(tf.zeros([10]))

# Construct model
pred = tf.nn.softmax(tf.matmul(x, W) + b) # Softmax

# Minimize error using cross entropy
cost = tf.reduce_mean(-tf.reduce_sum(y*tf.log(pred), reduction_indices=1))

grad_W, grad_b = tf.gradients(xs=[W, b], ys=cost)


new_W = W.assign(W - learning_rate * grad_W)
new_b = b.assign(b - learning_rate * grad_b)

# Initialize the variables (i.e. assign their default value)
init = tf.global_variables_initializer()

# Start training
with tf.Session() as sess:
    sess.run(init)

    # Training cycle
    for epoch in range(training_epochs):
        avg_cost = 0.
        total_batch = int(mnist.train.num_examples/batch_size)
        # Loop over all batches
        for i in range(total_batch):
            batch_xs, batch_ys = mnist.train.next_batch(batch_size)
            # Fit training using batch data
            _, _,  c = sess.run([new_W, new_b ,cost], feed_dict={x: batch_xs,
                                                       y: batch_ys})
            
            # Compute average loss
            avg_cost += c / total_batch
        # Display logs per epoch step
        if (epoch+1) % display_step == 0:
#             print(sess.run(W))
            print ("Epoch:", '%04d' % (epoch+1), "cost=", "{:.9f}".format(avg_cost))

    print ("Optimization Finished!")

    # Test model
    correct_prediction = tf.equal(tf.argmax(pred, 1), tf.argmax(y, 1))
    # Calculate accuracy for 3000 examples
    accuracy = tf.reduce_mean(tf.cast(correct_prediction, tf.float32))
    print ("Accuracy:", accuracy.eval({x: mnist.test.images[:3000], y: mnist.test.labels[:3000]}))
    
    
# Output
# Epoch: 0001 cost= 1.183741399
# Epoch: 0002 cost= 0.665312284
# Epoch: 0003 cost= 0.552796521
# Epoch: 0004 cost= 0.498697014
# Epoch: 0005 cost= 0.465521633
# Epoch: 0006 cost= 0.442611256
# Epoch: 0007 cost= 0.425528946
# Epoch: 0008 cost= 0.412203073
# Epoch: 0009 cost= 0.401364554
# Epoch: 0010 cost= 0.392398663
# Optimization Finished!
# Accuracy: 0.874
```

### 1.3 tensorflow中操作gradient-clip

在训练深度神经网络的时候,我们经常会碰到`梯度消失`和`梯度爆炸`问题,scientists提出了很多方法来解决这些问题,本篇就介绍一下如何在tensorflow中使用clip来address这些问题

```python
train_op = tf.train.GradientDescentOptimizer(learning_rate).minimize(cost)
```

在调用minimize方法的时候，底层实际做了两件事

- 计算所有`trainable variables`的梯度(gradients)
- Apply them to `variables`

随后, 在我们`sess.run(train_op)`的时候, 会对`variables`进行更新

那我们如果想处理一下计算完的`gradients`,那该怎么办呢? 官方给出了以下步骤：

1. Compute the gradients with `compute_gradients()`. 计算梯度
2. Process the gradients as you wish. 处理梯度
3. Apply the processed gradients with `apply_gradients()`. apply处理后的梯度给`variables`

这样,我们以后在`train`的时候就会使用`processed gradient`去更新`variable`

框架如下：

```python
# Create an optimizer.optimizer必须和variable在一个设备上声明
opt = GradientDescentOptimizer(learning_rate=0.1)

# Compute the gradients for a list of variables.
grads_and_vars = opt.compute_gradients(loss, <list of variables>)

# grads_and_vars is a list of tuples (gradient, variable).  Do whatever you
# need to the 'gradient' part, for example cap them, etc.
capped_grads_and_vars = [(MyCapper(gv[0]), gv[1]) for gv in grads_and_vars]

# Ask the optimizer to apply the capped gradients.
opt.apply_gradients(capped_grads_and_vars)
```

例子：

```python
#return a list of trainable variable in you model
params = tf.trainable_variables()

#create an optimizer
opt = tf.train.GradientDescentOptimizer(self.learning_rate)

#compute gradients for params
gradients = tf.gradients(loss, params)

#process gradients
clipped_gradients, norm = tf.clip_by_global_norm(gradients,max_gradient_norm)

train_op = opt.apply_gradients(zip(clipped_gradients, params))
```

之后，就可以利用`sess.run(train_op)`进行训练了

### 参考资料

- [利用 tf.gradients 在 TensorFlow 中实现梯度下降](https://segmentfault.com/a/1190000012531967)
- [tf.gradients API](https://www.tensorflow.org/api_docs/python/tf/gradients)

## 2. tf.stop_gradient

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

### 参考资料

- [关于tf.stop_gradient的使用及理解](https://blog.csdn.net/u013745804/article/details/79589514)
- [OpenAI Spinningup - Tensorflow Tutorial (Slide)](https://github.com/openai/spinningup-workshop/blob/master/tensorflow_review/tf_review_session.pdf)
- [tf.stop_gradient API](https://www.tensorflow.org/api_docs/python/tf/stop_gradient)

## 3. manual gradient 和 gradient descent magic

## 4. compute_gradient 和 apply_gradient



























