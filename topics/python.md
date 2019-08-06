---
layout: page
title:  Python
---

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

直接赋值: 其实就是对象的引用（别名）
浅拷贝(copy): 拷贝父对象，不会拷贝对象的内部的子对象
深拷贝(deepcopy): copy 模块的 deepcopy 方法，完全拷贝了父对象及其子对象

字典浅拷贝实例

```python
>>>a = {1: [1,2,3]}
>>> b = a.copy()
>>> a, b
({1: [1, 2, 3]}, {1: [1, 2, 3]})
>>> a[1].append(4)
>>> a, b
({1: [1, 2, 3, 4]}, {1: [1, 2, 3, 4]})
```












