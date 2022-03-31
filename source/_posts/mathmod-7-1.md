---
title: 第七讲-多元线性回归分析(1)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250041414.png
tags:
    - 教程
    - 数学建模
    - 笔记
math: true
---
# 第七讲-多元线性回归分析(1)

原ppt：[点我下载](https://ougrk-my.sharepoint.com/:b:/g/personal/task_ougrk_onmicrosoft_com/Ec4w7Z2-xN5GiTVDGUmx6koBXdj49148yfYAUvaSNWwPGg?e=6bf51B)

这是理论篇

## 1 简介

回归分析：研究 X 和 Y 之间相关性的分析

### 1.1 三个关键词：

* 相关性

  两个数据是否有相关性，比如说：

  统计数据表明：游泳死亡人数越高，雪糕卖得越多
  （游泳死亡人数和雪糕售出量之间呈显著正相关）

  但是**相关性不等于因果性**

* Y

  Y是因变量，也即是我们要研究的核心变量，被解释变量

  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132410.png)

* X

  这个是因变量，或者叫做解释变量

回归分析的任务就是，通过研究X和Y的相关关系，尝试去解释Y的形成机制，进而达到通过X去预测Y的目的。



### 1.2 回归分析的使命：

* **识别重要变量**

* **判断相关性的方向**

* **要估计权重（回归系数）**

  也就是不同变量之间的重要性，哪个变量的影响比较大



### 1.3 回归分析的分类

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132415.png)



### 1.4数据的分类：

| 类型         | 说明                                           | 建模方法                                    |
| ------------ | ---------------------------------------------- | ------------------------------------------- |
| 横截面数据   | 在某一时点收集的不同对象的数据                 | 多元线性回归                                |
| 时间序列数据 | 对同一对象在不同时间连续观察所取得的数据       | 移动平均、指数平滑、ARIMA、GARCH、VAR、协积 |
| 面板数据     | 横截面数据与时间序列数据综合起来的一种数据资源 | 固定效应和随机效应、静态面板和动态面板      |



### 1.5 数据的获取

* 知乎
* 人大经济论坛
* python爬虫



## 2 线性回归

### 2.1 一元线性回归

设有一组数据 $(x_i,y_i)$，我们设置拟合曲线为 $y=kx+b$,令拟合值：
$$
\hat{y}_{i}=k x_{i}+b
$$
那么就有：
$$
\begin{aligned}
\hat{k}, \hat{b} &=\underset{k, b}{\arg \min }\left(\sum_{i=1}\left(y_{i}-\hat{y}_{i}\right)^{2}\right) \\
&=\underset{k, b}{\arg \min }\left(\sum_{i=1}\left(y_{i}-k x_{i}-b\right)^{2}\right)
\end{aligned}
$$
令：
$$
L=\sum_{i=1}^{n}\left(y_{i}-k x_{i}-b\right)^{2}
$$
现在要找 $k,b$ 使得 $L$ 最小

$L$ 在机器学习中也被称为 **损失函数** ，在 回归分析里面也常被称为**误差平方和**



### 2.2 一元线性回归模型

这里的因变量只有一个

假设 x 是自变量，y是因变量，且满足下面的线性关系：

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132416.png" style="zoom: 25%;" />



令观测值 $\widehat{y_{i}}=\widehat{\beta_{0}}+\widehat{\beta_{1}} x_{i}$
$$
\begin{aligned}
\widehat{\beta_{0}}, \widehat{\beta_{1}}&=\underset{\beta_{0}, \beta_{1}}{\arg \min }\left(\sum_{i=1}^{n}\left(y_{i}-\widehat{y_{i}}\right)^{2}\right)\\
&=\underset{\beta_{0}, \beta_{1}}{\arg \min }\left(\sum_{i=1}\left(y_{i}-\widehat{\beta_{0}}-\widehat{\beta_{1}} x_{i}\right)^{2}\right)
\end{aligned}
$$
令：$\hat{\mu_{i}}=y_{i}-\widehat{\beta_{0}}-\widehat{\beta_{1}} x_{i}$

所以：
$$
\widehat{\beta_{0}}, \widehat{\beta_{1}}=\underset{\beta_{0}, \beta_{1}}{\arg \min }\left(\sum_{i=1}^{n}\left(\widehat{\mu_{i}}\right)^{2}\right)
$$

### 2.3 对线性的理解

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132417.png)

### 2.4 回归系数的解释

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132418.png)

可以看到，引入了新的自变量价格后，对回归系数的影响非常大！！！

原因是因为 **内身性**

### 2.5 内生性

假设我们的模型为：
$$
y=\beta_{0}+\beta_{1} x_{1}+\beta_{2} x_{2}+\cdots+\beta_{k} x_{k}+\mu
$$
如果

* 误差项 $\mu$ 和其他所有自变量都无关，我们就说，该回归模型具有 **外生性**
* 如果 $\mu$ 和其他变量相关，就有 **内生性**



**包含了所有与y相关，但未添加到回归模型中的变量如果这些变量和我们已经添加的自变量相关，则存在内生性**



 内生性的蒙特卡罗模拟

```matlab
%% 蒙特卡洛模拟：内生性会造成回归系数的巨大误差
times = 300;  % 蒙特卡洛的次数
R = zeros(times,1);  % 用来储存扰动项u和x1的相关系数
K = zeros(times,1);  % 用来储存遗漏了x2之后，只用y对x1回归得到的回归系数
for i = 1: times
    n = 30;  % 样本数据量为n
    x1 = -10+rand(n,1)*20;   % x1在-10和10上均匀分布，大小为30*1
    u1 = normrnd(0,5,n,1) - rand(n,1);  % 随机生成一组随机数
    x2 = 0.3*x1 + u1;   % x2与x1的相关性不确定， 因为我们设定了x2要加上u1这个随机数
    % 这里的系数0.3我随便给的，没特殊的意义，你也可以改成其他的测试。
    u = normrnd(0,1,n,1);  % 扰动项u服从标准正态分布
    y = 0.5 + 2 * x1 + 5 * x2 + u ;  % 构造y
    k = (n*sum(x1.*y)-sum(x1)*sum(y))/(n*sum(x1.*x1)-sum(x1)*sum(x1)); % y = k*x1+b 回归估计出来的k
    K(i) = k;
    u = 5 * x2 + u;  % 因为我们回归中忽略了5*x2，所以扰动项要加上5*x2
    r = corrcoef(x1,u);  % 2*2的相关系数矩阵
    R(i) = r(2,1);
end
plot(R,K,'*')
xlabel("x_1和u'的相关系数")
ylabel("k的估计值")
```

### 2.5 核心变量和控制变量

内生性要求所有解释变量都和扰动项不想干，但是这个假定太强了，并且实际当中有很多解释变量，都需要保证他们的外生性，比较困难。



能否弱化这个条件，我们可以把解释变量分成两类

* 核心解释变量

  我们最感兴趣的变量，**在实际应用当中，我们只需要保证核心解释变量和 $\mu$ 不相关就行了**

* 控制变量

  我们可能对于这些变量本身并无太大兴趣；而之所以把它们也放入回归方程，主要是为了 “控制住” 那些对被解释变量有影响的遗漏因素

### 2.6 回归系数的解释

$$
\begin{gathered}
y_{i}=\beta_{0}+\beta_{1} x_{1 i}+\beta_{2} x_{2 i}+\cdots+\beta_{k} x_{k i}+\mu_{i} \\
\Downarrow \\
\widehat{y_{i}}=\widehat{\beta_{0}}+\widehat{\beta_{1}} x_{1 i}+\widehat{\beta_{2}} x_{2 i}+\cdots+\widehat{\beta_{k}} x_{k i}
\end{gathered}
$$

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132419.png)

### 2.7 四类回归系数的解释

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132420.png" style="zoom:50%;" />

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132421.png" style="zoom:50%;" />

### 2.8 特殊自变量

如果自变量中有 **定性变量** ，例如性别、地域等，在回归中要怎么处理呢？

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132422.png)

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132423.png)



**为了避免完全多重共线性的影响，引入虚拟变量的个数一般是分类数减1**

### 2.9 交互项

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203300132424.png)

