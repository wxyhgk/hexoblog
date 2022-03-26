---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(6)
---
# 置信区间

| 命令         | 说明                           |
| ------------ | ------------------------------ |
| ci mean      | 连续型随机变量 mean 的置信区间 |
| proportion   | 分类变量 mean 的置信区间       |
| pwcorr       | 变量的配对相关性               |
| graph matrix | 相关性矩阵                     |



相关系数可以查看这篇文章：https://wxyhgk.github.io/2022/03/25/mathmod-5-1/

首先还是使用 **1978 Automobile Data**

```
sysuse auto,clear
```

## ci means

**ci = compute standard errors and confidence intervals**



```
ci means [varlist] [if] [in] [weight] [,options]
```

默认 **95%** 置信区间



`ci mean mpg price,level(95)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258475.png" style="zoom:67%;" />



使用 cii 可以自定义，不需要指定变量什么的

`cii mean 166 19509 4379, level(95)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258484.png" style="zoom:67%;" />



## proportion

这是分类变量的置信区间，可以使用上面说的 ci 命令：

`ci prop foreign`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258485.png" style="zoom:67%;" />



用 ci 有个缺点，就是只能使用 binary 变量（二分类变量），比如我们使用` ci prop rep78 `就会出现问题

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258486.png)



这个时候 proportion 就排上用场了，可以用 prop 简写

```
proportion varlist [if] [in] [weight] [, options]
```



`prop foreign`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258487.png" style="zoom:67%;" />



`prop rep78`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258488.png" style="zoom:67%;" />



`prop foreign rep78`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258489.png" style="zoom:67%;" />



对比 `prop foreign` 和 `prop foreign rep78` ,可以发现这两部分数据不一样，为什么会这样呢？

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258490.png)

这是因为 prop 在设置多个变量的时候，会默认去除一些缺失值。

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258491.png)

如何解决这个问题呢？

可以使用 miss 命令，`prop foreign rep78,miss`

> https://imgur.com/a/QtXv034
> 連結裡的圖為help proportion的內容。左邊是stata 15，有miss指令；右邊是stata 16，沒有miss指令。但不知道為什麼版本升級，指令反而被移除了。

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258492.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258493.png)



## pwcorr

pwcorr = Display all pairwise correlation coefficients(显示所有成对的相关系数)

```
owcorr [varlist] [if] [in] [weight] [, pwcorr_options]
```



`pwcorr price headroom mpg displacement`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258494.png" style="zoom:67%;" />



还可以展示 p 值

`pwcorr price headroom mpg displacement,sig`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258495.png" style="zoom:67%;" />





还能指定p值的范围，比如我们想指定p小于0.05的标识出来

`pwcorr price headroom mpg displacement,star(0.05)`

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258496.png)



## graph matrix

这个命令可以绘制相关性矩阵

```
graph matrix varlist [if] [in] [weight] [, options]
```



`graph matrix price headroom mpg displacement`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261258497.png" style="zoom: 50%;" />

可以看到效果还是不错的



这个是对称的，我们也可以只画一半，加一个参数 half

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261300246.png" style="zoom:50%;" />