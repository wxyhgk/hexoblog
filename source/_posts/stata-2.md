---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(2)
---
# 统计描述指标

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329761.png)

## codebook 数据字典

```bash
codebook [varlist] [if] [in] [,options]
```

* [ ]代表不是必须的

- varlist ：变量名单=一个或多个变量
- if 逻辑判断
- in 第几个到第几个观测值
- options 跟在逗号后面，一些可以自定义的选项

---

开始之前还是使用 `sysuse auto,clear` 导入自带的 auto 数据

我们来看看 price 这个变量的 codebook

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329762.png)

现在加上一个 if 逻辑判断，找出 price 大于 5000的数据

`codebook price if price>5000`

代表找出大于5000的

`codebook price in 10/20`

找出10到20变量这些数据

可以使用 help codebook 查看选项也就是 `codebook [varlist] [if] [in] [,options]`  中的 `option`

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329763.png)

虽然选项很多，但是一般不用，我们用 codebook 一般是对数据进行一个初步了解

## summarize

**作用 ：**显示出 中位数，标准差，最大值，最小值

**语法：summarize [varlist] [if] [in] [weight] [,option]**

推荐使用 `sum` 或者 `summ` ，完全等同于 `summarize`

来看看 price 的summarize

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329764.png)

对比codebook的结果

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329762.png)

似乎并没有什么区别，但是我们可以用 `help summarize` 看看

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329765.png)

这里有个 `detail`  选项，后面的解释是：可以显示额外的统计量，这个是比较关键的，所以我们在 stata 中试试这个

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221329766.png)

从图中可以看到给出的信息更详细了