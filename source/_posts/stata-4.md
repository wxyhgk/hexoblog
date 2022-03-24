---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(4)
---

首先还是导入数据 `sysuse auto,clear`

## Stata主题(Scheme)

使用 help scheme 可以查看一些主题

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255001.png" style="zoom: 33%;" />

默认主题就是 s2color，类似于下面这样的图像

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255002.png" style="zoom:33%;" />

更加推荐的主题是 **s1mono**

如何设置主题呢？

```
set scheme s1mono
```

这样设置主题后，Stata重启后会回到原主题

我们可以使用 `set scheme s1mono,perm` 设置为永久 s1mono 主题

## Scatter plot 散点图

```
[twoway] scatter varlist [if] [in] [weight] [,options]
```

最基础的形式： twoway scatter y x

进阶模式：twoway scatter y1 y2 y3 ... x 

赶紧试试，`twoway scatter mpg weight`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255003.png" style="zoom:33%;" />

一个变量和多个变量的关系可以看看

`twoway scatter weight length price`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255004.png" style="zoom:33%;" />

改变点的 形状，颜色，大小等

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255005.png)



可选的 msymbol 

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255006.png" style="zoom: 50%;" />

可选的 mcolor

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255007.png" style="zoom: 50%;" />



可选的 msize

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255008.png" style="zoom:50%;" />

来试一下

`twoway scatter mpg weight,msymbol(D) mcolor(blue) msize(medium)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255009.png" style="zoom:50%;" />

## Option：by

这个可以按照某变量分类分别绘制散点图

```
twoway scatter y变量 x变量,by(某变量分类)
```

`twoway scatter mpg weight,by(foreign)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255010.png" style="zoom:50%;" />

最后如果我们想两个分类放到一张图怎么办呢

`twoway (scatter mpg weight if foreign==0) (scatter mpg weight if foreign==1) ,legend(label(1 “Domestic”) label(2 “Foreign”))`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203241255011.png" style="zoom:50%;" />