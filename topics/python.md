---
layout: page
title:  Python
---

---
**Table of Contents**
* TOC
{:toc}

---

## Python学习

- Stanford - CS224n - Python review [[Slide]](http://web.stanford.edu/class/cs224n/readings/python-review.pdf)
- Stanford - CS231n - Python Numpy Tutorial [[Website]](http://cs231n.github.io/python-numpy-tutorial/) [[ipython]](https://github.com/kuleshov/cs228-material/blob/master/tutorials/python/cs228-python-tutorial.ipynb)

## jupyter插件

- [A Jupyter notebook viewer for macOS](https://github.com/tuxu/nbviewer-app)
- [A JupyterLab extension for displaying dashboards of GPU usage](https://github.com/jacobtomlinson/jupyterlab-nvdashboard)

## 工具

- [Python Handout](https://github.com/danijar/handout)
    - Turn Python scripts into handouts with Markdown and figures

## jupyter notebook 增加kernel

假设python环境名为python35，执行下面命令添加该环境下的kernel

> pip install ipykernel
> python -m ipykernel install --name python35

## Python在Terminal中的自动补全

为了在 Terminal 中使用 Python 更加方便，在 home 目录下添加脚本 `.pythonstartup`，内容如下，

然后在 `.bashrc` 中添加 `export PYTHONSTARTUP=~/.pythonstartup`，

这样就能在 Terminal 中使用 Tab 实现 Python 的自动补全了。

```python
#!/usr/bin/python
#
#-----------------------------------------------------------------------------
#
# Usage: 
#   - rename this file to ".pythonstartup"
#   - put it under your home directory, e.g. "~"
#   - modify .bashrc, add following line,
#       export PYTHONSTARTUP=~/.pythonstartup
#
#-----------------------------------------------------------------------------

import readline
import rlcompleter
import atexit
import os

# tab completion
readline.parse_and_bind('tab: complete')
# history file
histfile = os.path.join(os.environ['HOME'], '.pythonhistory')
try:
    readline.read_history_file(histfile)
except IOError:
    pass

atexit.register(readline.write_history_file, histfile)
del os, histfile, readline, rlcompleter
```

## Python语法

### Python中append和extend的区别

- list.append(object) 向列表中添加一个对象object
- list.extend(sequence) 把一个序列seq的内容添加到列表中

### python函数: 形参中的 *args 和 **kwargs

*args：（表示的就是将实参中按照位置传值，多出来的值都给args，且以元祖的方式呈现）

示例：

```python
def foo(x, *args):
    print(x)
    print(args)

foo(1, 2, 3, 4, 5) # 其中的2,3,4,5都给了args

"""
output:
    1
    (2, 3, 4, 5)
"""
```

**kwargs：（表示的就是形参中按照关键字传值把多余的传值以字典的方式呈现）

示例：

```python
def foo(x, **kwargs):
    print(x)
    print(kwargs)

foo(1, y=1, a=2, b=3, c=4) # 将y=1, a=2, b=3, c=4以字典的方式给了kwargs

"""
output:
    1
    {'y': 1, 'a': 2, 'b': 3, 'c': 4}
"""
```

### Python 直接赋值、浅拷贝和深度拷贝解析

- 直接赋值: 其实就是对象的引用（别名）
- 浅拷贝(copy): 拷贝父对象，不会拷贝对象的内部的子对象
- 深拷贝(deepcopy): copy 模块的 deepcopy 方法，完全拷贝了父对象及其子对象

字典浅拷贝实例

```python
>>> a = {1: [1,2,3]}
>>> b = a.copy()
>>> a, b
({1: [1, 2, 3]}, {1: [1, 2, 3]})
>>> a[1].append(4)
>>> a, b
({1: [1, 2, 3, 4]}, {1: [1, 2, 3, 4]})
```

深度拷贝需要引入`copy`模块

```python
>>> import copy
>>> c = copy.deepcopy(a)
>>> a, c
({1: [1, 2, 3, 4]}, {1: [1, 2, 3, 4]})
>>> a[1].append(5)
>>> a, c
({1: [1, 2, 3, 4, 5]}, {1: [1, 2, 3, 4]})
```

### python的方法和属性私有化:单下划线，双下划线

* xx: 公有变量
* _x: 单前置下划线,私有化属性或方法，禁止通过from modules import *导入,但是类对象和子类可以访问
* __xx：双前置下划线,避免与子类中的属性命名冲突，无法在外部直接访问(名字重整所以访问不到)，类对象和子类不能访问
* __xx__:双前后下划线,用户名字空间的魔法对象或属性。例如:__init__ , __ 尽量不要自定义这种形式的。
* xx_:单后置下划线,用于避免与Python关键词的冲突

### axis = 0/1/-1


* axis=0：在第一维操作
* axis=1：在第二维操作
* axis=-1：在最后一维操作

以`np.argmax()`函数为例：

```python
>>> a = np.arange(24).reshape(2,3,4)
>>> a
array([[[ 0,  1,  2,  3],
        [ 4,  5,  6,  7],
        [ 8,  9, 10, 11]],

       [[12, 13, 14, 15],
        [16, 17, 18, 19],
        [20, 21, 22, 23]]])
>>> np.argmax(a,axis = 0)  #返回尺寸(3,4)
array([[1, 1, 1, 1],
       [1, 1, 1, 1],
       [1, 1, 1, 1]])
>>> np.argmax(a,axis = 1) #返回尺寸(2,4)
array([[2, 2, 2, 2],
       [2, 2, 2, 2]])
>>> np.argmax(a,axis = -1) #返回尺寸(2,3) 
array([[3, 3, 3],
       [3, 3, 3]])
```











