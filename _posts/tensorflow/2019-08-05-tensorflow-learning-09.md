---
layout: post
title: Tensorflow学习笔记09 - GPU使用
tags: [tensorflow, deep learning]
---

### 1. 限制GPU资源使用

- 动态申请显存

```python
config = tf.ConfigProto()  
config.gpu_options.allow_growth = True  
session = tf.Session(config=config)
```

- 限制GPU使用率

```python
config = tf.ConfigProto()  
config.gpu_options.per_process_gpu_memory_fraction = 0.4  #占用40%显存  
session = tf.Session(config=config)
```

或者

```python
gpu_options=tf.GPUOptions(per_process_gpu_memory_fraction=0.4) 
config=tf.ConfigProto(gpu_options=gpu_options) 
session = tf.Session(config=config)
```

### 2. 设置使用哪块GPU

- 在Python程序中设置

```python
#在程序开头
os.environ['CUDA_VISIBLE_DEVICES'] = '0' #使用 GPU 0
os.environ['CUDA_VISIBLE_DEVICES'] = '0,1' # 使用 GPU 0，1
```

- 在执行程序时设置

```shell
CUDA_VISIBLE_DEVICE=0,1 python yourcode.py
```

