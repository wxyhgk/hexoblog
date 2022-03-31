---
title: 第五讲-相关系数(3)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250041414.png
tags:
    - 教程
    - 数学建模
    - 笔记
math: true
---
# 斯皮尔曼相关系数

## 1 定义斯皮尔曼相关系数

### 1.1 定义一

定义：X，Y为两组数据，其 斯皮尔曼（等级）相关系数为
$$
r_{s}=1-\frac{6 \sum_{i=1}^{n} d_{i}^{2}}{n\left(n^{2}-1\right)}
$$
其中 $d_i$ 为 $X_i,Y_i$  之间的等级差

我们可以证明斯皮尔曼相关系数 $  -1 \leqslant r_s \leqslant 1$



什么是等级呢？

一个数的等级就是，将它所在的列按照从小到大排列后，这个数所在的位置，如果有相同的数，那么我们就取他们位置的平均值

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271555371.png" style="zoom: 33%;" />



带入到公式中去，可以计算得到：
$$
r_{s}=1-\frac{6 \times(1+0.25+0.25+1)}{5 \times 24}=0.875
$$

### 2.1 定义二

另外一种 斯皮尔曼相关系数被定义成 **等级之间的皮尔逊相关系数**

这个计算公式比较复杂，这里不说，可以看 [这篇文章](https://www.codetd.com/article/13247102) 

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271555372.png" style="zoom:33%;" />

Matlab 代码

Matlab 采用的是第二种定义方法，第一种需要自己手动计算

两种命令用法：

`corr(X,Y,'type','Spearman')` 这个要求 X，Y 都是列向量

`corr(M,'type','Spearman')`  这个是计算M矩阵各列之间的皮尔逊相关系数

```matlab
%% 斯皮尔曼相关系数
X = [3 8 4 7 2]'  % 一定要是列向量哦，一撇'表示求转置
Y = [5 10 9 10 6]'
% 第一种计算方法
1-6*(1+0.25+0.25+1)/5/24

% 第二种计算方法
coeff = corr(X , Y , 'type' , 'Spearman')
% 等价于：
RX = [2 5 3 4 1]
RY = [1 4.5 3 4.5 2]
R = corrcoef(RX,RY)
%这里的等价就是斯皮尔曼相关系数被定义成等级变量之间的皮尔逊相关系数。

% 计算矩阵各列的斯皮尔曼相关系数
R = corr(Test, 'type' , 'Spearman')
```

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271555373.png)

## 2 假设检验

分成两种情况，小样本 和 大样本

### 2.1 小样本

小样本就是 $n \le 30$,可以查表，这里就不做讨论了

### 2.2 大样本

在大样本情况下，统计量服从
$$
r_{s} \sqrt{n-1} \sim N(0,1)
$$
我们要计算 $r_{s} \sqrt{n-1}$ ，然后求出对应的 p 值，然后 p 和 0.05 比较

使用 `[R,P]=corr(Test, 'type' , 'Spearman')` 给出接给出 相关系数R 和 p值



## 3 两种系数的比较

* **连续数据，正态分布，线性关系**，用pearson相关系数是最恰当，
  当然用 spearman相关系数也可以， 就是效率没有pearson相关系数高。

* 上述任一条件不满足，就用spearman相关系数，不能用pearson相关系数

* **两个定序数据**之间也用spearman相关系数，不能用pearson相关系数

  **定序数据**是指仅仅反映观测对象等级、顺序关系的数据，是由定序尺度计量 形成的，表现为类别，可以进行排序，属于品质数据。

  例如:优、良、差; 我们可以用1表示差、2表示良、3表示优，但请注意，用2除以1得出的2并不 代表任何含义。定序数据最重要的意义代表了一组数据中的某种逻辑顺序。

