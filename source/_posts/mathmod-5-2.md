---
title: 第五讲-相关系数(2)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203250041414.png
tags:
    - 教程
    - 数学建模
    - 笔记
math: true
---
相关文件链接：[点我查看](https://ougrk-my.sharepoint.com/:f:/g/personal/task_ougrk_onmicrosoft_com/EgWiIB6TUxpClwP-COy4AsMBrG37rpD0GLlDCxqsqCqX9w?e=oZSQgJ)

## 一. 假设检验

这一次主要说 **假设检验** 的内容

对皮尔逊逊相关系数进行假设检验

* **第一步**
  提出原假设 $H_0$ 和备择假设 $H_1$
  假设我们计算出了一个皮尔逊相关系数 r ,我们想检验它是否显著的异于0.

* **第二步**
  在原假设成立的条件下，利用我们要检验的量构造出一个符合某一分布的统计变量
  （这里的分布一般有4种：标准正态分布，t 分布，卡方分布，F分布）
  对于皮尔逊相关系数而言，满足一定条件，我们可以构造统计量:
  $$
  t=r \sqrt{\frac{n-2}{1-r^{2}}}
  $$
  我们可以证明这个是服从自由度为 $n-2$的$t$分布

* **第三步**
  将我们要检验的这个值带入到这个统计量中，可以得到一个特定的值，也就是检验值。
  假设我们现在计算出来的相关系数是 0.5 ，样本数为 30，那么我们可以得到 
  $$
  t^{*}=0.5 \sqrt{\frac{30-2}{1-0.5^{2}}}=3.05505
  $$

* **第四步**
  由于我们知道统计量的分布情况，所以我们可以画出该分布的 pdf，并给定一个置信区间，然后根据这个置信区间，找到临界值，最后做一个比较，画出接受与和拒绝域。

  常见的置信水平有三个 ：90%，95%，99%，**其中 95% 最常用**
  
  <img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203270131603.png" style="zoom: 15%;" />

### p值检验

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426505.png" style="zoom:33%;" />

紫色部分为 p 值，也就是 **拒绝域的面积**，p 越小更加容易拒绝。

比如得到的检验值 $t^*=3.05505$,根据这个，我们可以计算出 $p = 0.0049$



论文中经常出现 $0.5$，$0.5 *$，$0.5 **$，$0.05 ***$ 这样的数字，代表什么呢？

说的是 **显著性标记**

* 0.5 * 代表 在 $95 \%$ 指在 **95% 置信水平上拒绝原假设**
* 0.5** 代表 $1\% $ 显著水平
* 0.5 *** 代表 $0.1\%$  显著性水平



Matlab 中使用 `[R,P]=corrcoef(test)` 就能找到系数矩阵和p值

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426506.png" style="zoom:50%;" />

如果我们还想一个显著性的标记，用matlab得自己手动标记，所以这个时候，我们用 spss 就会方便很多



### 假设检验条件

皮尔逊相关系数的检验是需要条件的

*  实验数据通常假设是成对的来自于**正态分布的总体**
* 实验数据不能差距太大
* 每组样本是独立抽样的



现在我们要对数据进行 **正态分布检验**



## 二. 正态分布检验

### 1 雅克‐贝拉检验(Jarque‐Bera test) 

**这个检验要求样本数大于 30**

首先来说一下什么是 **偏度** 什么是 **峰度** 

（1）**偏度**

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426508.png" style="zoom:50%;" />

（2）**峰度**

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426509.png" style="zoom:50%;" />

正态分布的峰度为3 (有些地方定义的正态分布峰度为0)

**Matlab软件中使用的是第一种定义**



现在来说一下$JB$检验的步骤

对于一个随机变量$X $ ,假设其偏度为 $S$ ,峰度为 $K$ ,那么我们可以构造 $JB$ 统计量:
$$
J B=\frac{n}{6}\left[S^{2}+\frac{(K-3)^{2}}{4}\right]
$$
可以证明，如果$X$ 是正态分布，那么大样本情况下$JB \sim \chi^2(2)$ （自由度为2的卡方分布）



MATLAB 中进行 JB 检验的语法：`[h,p] = jbtest(x,alpha)`

当输出 h 等于 1 时，表示拒绝原假设； 

h 等于 0 则代表不能拒绝原假设。



alpha就是显著性水平，一般取0.05，此时置信水平为1‐0.05=0.95

x就是我们要检验的随机变量，**注意这里的x只能是向量**,不能是矩阵

```matlab
%% 正态分布检验
% 检验第一列数据是否为正态分布
[h,p] = jbtest(Test(:,1),0.05)
% 用循环检验所有列的数据
n_c = size(Test,2); % number of column 数据的列数
H = zeros(1,6);
P = zeros(1,6);
for i = 1:n_c
	[h,p] = jbtest(Test(:,i),0.05);
	H(i)=h;
	P(i)=p;
end

disp(H)
disp(P)
```



### 2 夏皮洛‐威尔克检验

**小样本3≤n≤50**

matlab 中没有自带的这个检验，我们可以用 SPSS 做比较方便



操作步骤

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426510.png" style="zoom:50%;" />



然后就可以得到下面的图了

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426511.png)

### 3 Q-Q图

在统计学中，Q‐Q图（Q代表分位数Quantile）是一种通过比较两个概率分布的分位数对这两个概率分布进行比较的概率图方法.



首先选定分位数的对应概率区间集合，在此概率区间上，点(x,y)对应于第一个分布的一个分位数x和第二个分布在和x相同概率区间上相同的分位数。



这里，我们选择正态分布和要检验的随机变量，并对其做出QQ图，

可想而知，如果要检验的随机变量是正态分布，那么QQ图就是一条直线。



**要利用Q‐Q图鉴别样本数据是否近似于正态分布,只需看Q‐Q图上的点是否近似地在一条直线附近。（要求数据量非常大）**



第一列数据的qq图

`qqplot(Test(:,1))`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271426512.png" style="zoom: 67%;" />
