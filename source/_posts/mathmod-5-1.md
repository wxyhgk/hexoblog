---
title: 第五讲-相关系数(1)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250041414.png
tags:
    - 教程
    - 数学建模
    - 笔记
math: true
---

基础概念

|总体|考察对象的全体|
|---|---|
|样本|总体中抽取的一部分|



## 总体皮尔逊相关系数

两组数据：

$X:\{X_1,X_2,....,X_n\}$ 和 $Y:\{Y_1,Y_2,....Y_n\}$ 是 **总体数据**

(1)总体均值：

$$
\begin{aligned}
E(X) &=\frac{\sum_{i=1}^{N} X_{i}}{n} \\
E(Y) &=\frac{\sum_{i=1}^{N} Y_{i}}{n}
\end{aligned}
$$

(2)总体协方差

$$
\mathrm{Cov(X, Y)}=\frac{\sum_{i=1}^{n}\left(X_{i}-E(X)\right)\left(Y_{i}-E(Y)\right)}{n}
$$


(3)**总体皮尔逊相关系数**

$$
\rho_{X Y}=\frac{\mathrm{Cov}(X, Y)}{\sigma_{X} \sigma_{Y}}=\frac{\sum_{i=1}^{n} \frac{\left(X_{i}-E(X)\right)}{\sigma_{X}} \frac{\left(Y_{i}-E(Y)\right)}{\sigma_{Y}}}{n}
$$

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036327.png" style="zoom: 50%;" />

**也就是说 皮尔逊相关系数 消除了量纲的影响**



可以证明$|\rho_{X Y}| \leq 1$,且当 $Y=aX+b$ 时

$$
\rho_{X Y}=\left\{\begin{aligned}
1, & a>0 \\
-1, & a<0
\end{aligned}\right.
$$


## 样本皮尔逊相关系数

两组数据：

$X:\{X_1,X_2,....,X_n\}$ 和 $Y:\{Y_1,Y_2,....Y_n\}$ 是 **样本数据**

(1)样本均值：

$$
\begin{equation}
\bar{X}=\frac{\sum_{i=1}^{n} X_{i}}{n}, \bar{Y}=\frac{\sum_{i=1}^{n} Y_{i}}{n}
\end{equation}
$$



(2)样本协方差：

$$
\mathrm{Cov}(X, Y)=\frac{\sum_{i=1}^{n}(X_{i}-\bar{X})(Y_{i}-\bar{Y})}{n-1}
$$


注意这里是 $n-1$

(3) 样本皮尔逊相关系数

$$
r_{X Y}=\frac{\mathrm{Cov}(X, Y)}{S_{X} S_{Y}}
$$


$$
S_{X}=\sqrt{\frac{\sum_{i=1}^{n}\left(X_{i}-\bar{X}\right)^{2}}{n-1}},  S_{Y}=\sqrt{\frac{\sum_{i=1}^{n}\left(Y_{i}-\bar{Y}\right)^{2}}{n-1}}
$$


## 皮尔逊相关系数的一些误解

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036329.png" style="zoom:50%;" />

上面几个图的皮尔逊相关系数都是0.816，**皮尔逊相关系数容易受到异常值的影响**



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036331.png" style="zoom:50%;" />

这个图的横坐标和纵坐标很明显是类似于二次函数关系，但是皮尔逊相关系数为0



相关系数只是用来衡量两个变量**线性相关程度的指标**；

也就是说，**你必须先确认这两个变量是线性相关的**，然后这个相关系数才能告诉你他俩相关程度如何。



## 数据分析

### 用Excel做分析

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036332.png "")

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036333.png "")

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036334.png "")

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036335.png "")

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036336.png "")

### 用spss做分析

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036337.png "")

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036338.png "")

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036339.png "")

搞好之后按 确定 就能得到下面的图

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250036340.png "")

