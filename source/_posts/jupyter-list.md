---
title: Jupyter 数组基本操作
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210145263.png
tags:
    - Jupyter
    - 教程
---
# 1 生成数组的方法

## 1.1 生成0和1的数组

* np.ones(shape,dtype)

* np.ones_like(a,dtype)

* np.zeros(shape,dtype)

* np.zerso_like(a,dtype)


```python
import numpy as np
ones=np.ones([4,8])
ones
```




    array([[1., 1., 1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1., 1., 1.],
           [1., 1., 1., 1., 1., 1., 1., 1.]])




```python
np.zeros_like(ones)
```




    array([[0., 0., 0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0., 0., 0.],
           [0., 0., 0., 0., 0., 0., 0., 0.]])



## 1.2 从现有数组生成

### 1.2.1 生成方式

* np.array(object,dtype)

* np.asarry(a,dtype)


```python
a=np.array([[1,2,3],[4,5,6]])
a
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
a1=np.array(a) #深拷贝
a1
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
a2=np.asarray(a) #浅拷贝
a
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
a[0,0]
```




    1




```python
a[0,0]=1000
a
```




    array([[1000,    2,    3],
           [   4,    5,    6]])




```python
a1
```




    array([[1, 2, 3],
           [4, 5, 6]])




```python
a2
```




    array([[1000,    2,    3],
           [   4,    5,    6]])



## 1.3 生成固定范围的数组

### 1.3.1 np.linspace(start,stop,num,endpoint)

* 创建等差数组

* 参数
    * start 序列的起始值
    * stop 序列的终止值
    * num 要生成的间隔，默认为50
    * end point 序列中是否含有stop值，默认是有的


```python
# 生成等间隔的值
np.linspace(0,100,11)
```




    array([  0.,  10.,  20.,  30.,  40.,  50.,  60.,  70.,  80.,  90., 100.])



### 1.3.2 np.arange(start,stop,step,dtype)

* 创建等差数组，指定步长

* 参数
    * step 步长，默认为1


```python
np.arange(10,100,2)
```




    array([10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42,
           44, 46, 48, 50, 52, 54, 56, 58, 60, 62, 64, 66, 68, 70, 72, 74, 76,
           78, 80, 82, 84, 86, 88, 90, 92, 94, 96, 98])



### 1.3.2 np.logspace(start,stop,num)

* 创建等比数列

* 参数
    * num 要生成的等比数列数列，默认为50


```python
np.logspace(0,2,3) # 从10的0次到10的2次
```




    array([  1.,  10., 100.])



## 1.4 生成随机数组

### 1.4.1正态分布

* np.random.randn(d0,d1,....,dn) 功能是从标准正态分布中返回一个或多个样本值

* np.random.normal(loc=0.0,scale=1.0,size=None)
    * loc 平均值
    * scale 标准差
    * size 输出的shape，默认为None,只输出一个值


```python
x1=np.random.normal(1,2,100000)
x1
```




    array([ 0.34231076,  3.42480601, -0.94534042, ...,  3.64688988,
            0.35779773, -1.39490297])




```python
import matplotlib.pyplot as plt
```


```python
# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制图像
plt.hist(x1,1000)

# 3.显示图像
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202211649884.png)
​    



```python
stock_change=np.random.normal(0,1,[4,5])
stock_change
```




    array([[-0.15014493,  0.86883563,  1.43288001,  1.52881944, -0.15804121],
           [ 0.42120462, -0.37731794,  0.82449673,  0.82571125,  1.14846491],
           [-0.09014833,  0.47862224,  0.11942677,  0.65562547, -0.12761904],
           [-0.55336936,  0.4304151 , -0.97839863, -0.97315654, -0.11102239]])



### 1.4.2 均匀分布


```python
x2=np.random.uniform(-1,1,100000)
x2
```




    array([ 0.28107774,  0.3010664 , -0.10655626, ..., -0.4355808 ,
           -0.61298497, -0.32354305])




```python
# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制图像
plt.hist(x2,1000)

# 3.显示图像
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202211649886.png)
​    


# 2 数组的索引和切片


```python
stock_change
```




    array([[-0.15014493,  0.86883563,  1.43288001,  1.52881944, -0.15804121],
           [ 0.42120462, -0.37731794,  0.82449673,  0.82571125,  1.14846491],
           [-0.09014833,  0.47862224,  0.11942677,  0.65562547, -0.12761904],
           [-0.55336936,  0.4304151 , -0.97839863, -0.97315654, -0.11102239]])




```python
stock_change[0,0:3] #获取第 1 支股票的 前 3 个交易日的数据
```




    array([-0.15014493,  0.86883563,  1.43288001])




```python
a1=np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]])
```


```python
a1
```




    array([[[ 1,  2,  3],
            [ 4,  5,  6]],
    
           [[ 7,  8,  9],
            [10, 11, 12]]])




```python
a1[1,0,0]
```




    7



![ ](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202211541047.png)

# 3 形状修改

## 3.1 ndarray.reshape(shape,order)

* 返回一个具有相同数据域，但shape不一样的试图，不改变原来的数组本身

* 行列，不进行互换


```python
stock_change.shape
```




    (4, 5)




```python
stock_change
```




    array([[-0.15014493,  0.86883563,  1.43288001,  1.52881944, -0.15804121],
           [ 0.42120462, -0.37731794,  0.82449673,  0.82571125,  1.14846491],
           [-0.09014833,  0.47862224,  0.11942677,  0.65562547, -0.12761904],
           [-0.55336936,  0.4304151 , -0.97839863, -0.97315654, -0.11102239]])




```python
stock_change.reshape([5,4]) # 把原来的4行5列，改成了5行4列
```




    array([[-0.15014493,  0.86883563,  1.43288001,  1.52881944],
           [-0.15804121,  0.42120462, -0.37731794,  0.82449673],
           [ 0.82571125,  1.14846491, -0.09014833,  0.47862224],
           [ 0.11942677,  0.65562547, -0.12761904, -0.55336936],
           [ 0.4304151 , -0.97839863, -0.97315654, -0.11102239]])




```python
stock_change.reshape([-1,2])#不知道变成多行行，就写-1
```




    array([[-0.15014493,  0.86883563],
           [ 1.43288001,  1.52881944],
           [-0.15804121,  0.42120462],
           [-0.37731794,  0.82449673],
           [ 0.82571125,  1.14846491],
           [-0.09014833,  0.47862224],
           [ 0.11942677,  0.65562547],
           [-0.12761904, -0.55336936],
           [ 0.4304151 , -0.97839863],
           [-0.97315654, -0.11102239]])




```python
stock_change.reshape([3,-1]) # 报错，因为行不能被3整除
```


    ---------------------------------------------------------------------------
    
    ValueError                                Traceback (most recent call last)
    
    Input In [55], in <module>
    ----> 1 stock_change.reshape([3,-1])


    ValueError: cannot reshape array of size 20 into shape (3,newaxis)


## 3.2 ndarray.resize(new_shape)

* 这个要**修改数组本身**

* 行列不呼唤


```python
stock_change.resize([2,10])
```


```python
stock_change.shape 
```




    (2, 10)



可以看到原来是4行5列的，现在变成了2行10列，**改变了原来数组**

## 3.2 ndarray.T 

这是对数组做个转置


```python
stock_change.T
```




    array([[-0.15014493, -0.09014833],
           [ 0.86883563,  0.47862224],
           [ 1.43288001,  0.11942677],
           [ 1.52881944,  0.65562547],
           [-0.15804121, -0.12761904],
           [ 0.42120462, -0.55336936],
           [-0.37731794,  0.4304151 ],
           [ 0.82449673, -0.97839863],
           [ 0.82571125, -0.97315654],
           [ 1.14846491, -0.11102239]])



# 4 类型修改

## 4.1 ndarray.astype(type)

* 返回修改类型之后的数组


```python
stock_change.astype(np.int32)
```




    array([[0, 0, 1, 1, 0, 0, 0, 0, 0, 1],
           [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]])




```python
ar=np.array([[[1,2,3],[4,5,6]],[[7,8,9],[10,11,12]]])
ar
```




    array([[[ 1,  2,  3],
            [ 4,  5,  6]],
    
           [[ 7,  8,  9],
            [10, 11, 12]]])




```python
ar.tostring()
```

    C:\Users\Administrator\AppData\Local\Temp\2\ipykernel_4848\812263864.py:1: DeprecationWarning: tostring() is deprecated. Use tobytes() instead.
      ar.tostring()





    b'\x01\x00\x00\x00\x02\x00\x00\x00\x03\x00\x00\x00\x04\x00\x00\x00\x05\x00\x00\x00\x06\x00\x00\x00\x07\x00\x00\x00\x08\x00\x00\x00\t\x00\x00\x00\n\x00\x00\x00\x0b\x00\x00\x00\x0c\x00\x00\x00'



# 5 数组的去重

np.unique


```python
temp=np.array([[1,3,3],[3,4,9]])
temp
```




    array([[1, 3, 3],
           [3, 4, 9]])




```python
np.unique(temp)
```




    array([1, 3, 4, 9])

