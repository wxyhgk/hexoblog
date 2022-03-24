---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(3)
---
histogram(直方图)

graph box (箱形图)

violin plot (小提琴图)



首先还是导入 **1978 Automobile Data**

`sysuse auto,clear`

## histogram

```
histogram varname [if] [in] [weight] [,[continuous_opts | discrete_opts] options]
```

* varname :不是varlist，因此**只能有一个变量**
* histogarm 可以简写为 hist



最常用的三种形式：

* hist varname
* hist varname,freq
* hist  varname,by(varname2)



使用`hist price` 可以得到下面的图 hist 样式默认是 `Density`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005565.png" alt="" style="zoom: 25%;" />



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005567.png" alt="" style="zoom: 50%;" />



还能改变一下 `Density` 比如：

`hist price,freq`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005568.png" alt="" style="zoom:25%;" />



再看看其他的命令

`hist price,percent` 

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005569.png" alt="" style="zoom:25%;" />



更多的可以用 `help hist` 查看更多的选项

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005570.png" alt="" style="zoom: 33%;" />



注意到上面的个数（bin）都是8个

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005571.png" alt="" style="zoom: 33%;" />

如果改变这个呢，比如我想增加或减少这个数字。



可以这么操作

`hist price,freq bin(10)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232005572.png" alt="" style="zoom:25%;" />

其他的可以自己试



对于数据量足够多，可以做一个拟合

`hist price ,bin(10) normal`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028067.png" alt="" style="zoom: 25%;" />



可以用by命令进行一个分组

`hist price ,by(foreign)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028069.png" alt="" style="zoom: 33%;" />

## graph box

先来了解一下箱线图

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232012504.png" style="zoom:50%;" />

命令：

```
graph box yvars [if] [in] [weight] [,options]
```

`graph box price`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028070.png" alt="" style="zoom:33%;" />

或者

```
graph hbox yvars [if] [in] [weight] [,options]
```

`graph hbox price`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028071.png" alt="" style="zoom:33%;" />





## violin plot

小提琴图不是 stata 自带的画图命令,需要安装，用

```
ssc install vioplot
```

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028072.png" alt="" style="zoom:67%;" />

小提琴图的介绍，比箱图更加好用。

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028073.png)



`vioplot price`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028074.png" alt="" style="zoom:33%;" />



对比国内外的数据

`vioplot price, over(foreign)`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203232028075.png" alt="" style="zoom:50%;" />
