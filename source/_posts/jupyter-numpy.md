---
title: Jupyter的numpy介绍
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210145263.png
tags:
    - Jupyter
    - 教程
---

numpy介绍

```python
import numpy as np
```

# 1 hello numpy
## 1.1初始numpy


```python
score=np.array([[1,3],[1,4],[2,3]])
```


```python
score
```




    array([[1, 3],
           [1, 4],
           [2, 3]])



## 1.2 原生ndarray和Python效率对比


```python
import random
import time
import numpy as np
a = []
for i in range(100000000):
    a.append(random.random())
    
# 通过 %time 魔法方法，对比运行时间
%time sum1=sum(a)

b=np.array(a)
%time sum2=np.sum(b)
```

    CPU times: total: 3.69 s
    Wall time: 42.9 s


​    
    KeyboardInterrupt


​    ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210241022.png)



ndarray和Python List的对比

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210241457.png)

# 2 N维数组-ndarray 
## 2.1 数组的属性

|属性名字|属性解释|
|--- | --- |
|ndarray.shape|数组维度的元组|
|ndarray.ndim|数组维数|
|ndarray.size|数组中元素数量|
|ndarray.itemsize|一个数组元素的长度|
|ndarray.dtype|数组元素的类型|



```python
score
```




    array([[1, 3],
           [1, 4],
           [2, 3]])




```python
score.shape
```




    (3, 2)




```python
score.ndim
```




    2




```python
score.size
```




    6




```python
score.itemsize
```




    4




```python
score.dtype
```




    dtype('int32')



## 2.2 数组的形状


```python
a = np.array([1,2,3])
```


```python
a
```




    array([1, 2, 3])




```python
a.shape
```




    (3,)




```python
b=np.array([[1,3,3],[4,3,6]])
```


```python
b.shape
```




    (2, 3)




```python
c=np.array([[[1,3,3],[2,3,3]],[[1,1,3],[3,1,3]]])
```


```python
c
```




    array([[[1, 3, 3],
            [2, 3, 3]],
    
           [[1, 1, 3],
            [3, 1, 3]]])




```python
c.shape
```




    (2, 2, 3)



这里的223代表最外面是**两个**二维数组，二维数组里面由**两个**一维数组构成，每个一维数组有**三个**维度

## 2.3 ndarray的类型


```python
b=np.array([[1,3,3],[4,3,6]],dtype=np.float32)
```


```python
b
```




    array([[1., 3., 3.],
           [4., 3., 6.]], dtype=float32)




```python
arr = np.array ([ "pythonI", "hello", "I"], dtype=np.string_)
```


```python
arr
```




    array([b'pythonI', b'hello', b'I'], dtype='|S7')



这里的7代表最大的一个长度，上面的“pythonI”长度就是7

