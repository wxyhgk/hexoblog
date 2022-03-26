---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(5)
---

本文原始链接：[https://www.wolai.com/4wu6DSGCTmqAvwaRvx2qTT](https://www.wolai.com/4wu6DSGCTmqAvwaRvx2qTT)

首先导入数据`sysuse uslifeexp,clear`

## twoway命令入门

```text
twoway plot 变量 [if] [in] [,twoway_options]
```


- plot 选择图像的种类可以选择一下几种
	- scatter
	- line
	- connected
	- area
	- bar
- 变量：可以写**一个或多个y变量**，一个x变量
- if 定义所取的某一自变量的范围
- in 定义所取观测值的范围
- twoway_options 定义图像部分
	- 坐标轴范围
	- 标题
	- 注释
	- 标签



## 折线图

```纯文本
twoway line y1 y2...x
```




`twoway line le year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249227.png" style="zoom: 33%;" />



`twoway line le_male le_female year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249228.png" style="zoom:33%;" />



## 带数据标记的折线图

```纯文本
twoway connected y1 y2...x
```




`twoway connected le year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249229.png" style="zoom:33%;" />



`twoway connected le_male le_female year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249230.png" style="zoom:33%;" />



## 垂直线图

```纯文本
twoway dropline y1 y2...x
```





<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249231.png" style="zoom:33%;" />



`twoway dropline le_male le_female year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249232.png" style="zoom:33%;" />



## 脉冲图

```text
twoway spike y1 y2...x
```


`twoway spike le year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249233.png" style="zoom:33%;" />



`twoway spike le_male le_female year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249234.png" style="zoom:33%;" />

这里似乎只显示了一个也就是 females 的图像，males的到哪去了？是因为females把前面的males挡住了，可以换一下位置就行了

`twoway spike `**`le_female le_male`**` year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249235.png" style="zoom:33%;" />



## 面积图

```text
twoway area y1 y2...x
```




`twoway area le year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249236.png" style="zoom:33%;" />



`twoway area le_female le_male year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249237.png" style="zoom:33%;" />

## LOWESS图

`twoway lowess le year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249238.png" style="zoom:33%;" />



`lowess le year`

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203251249239.png" style="zoom:33%;" />

