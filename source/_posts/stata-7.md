---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(7)
---
## 可重复性



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235704.png)

**为什么强调可重复性?**

* 我们都会有很多的合作者
* 我们自己也是自己的合作者--几个月以前的自己
* Journal的要求



**用 Stata 保住分析可重复性**

* Log File
  * 所有显示在 Results 上的结果都保存为文档形式
  * 类似于于 R Markdown 文件
* Do file
  * 合作者
  * 提醒自己
  * 存档

## Log File

```
log useing filename [,append replace [text|smcl] name(logname)]
```

* filename：Log file 的名字

* append：如果文件存在，附加在(append)在文件上

* repalce：如果文件存在，替换（replace）该文件
  如果文件不存在,append和replace都会创造新的文件
  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235705.png)

  如果文件存在，而你有没有指定是append还是replace，Stata就会报错来询问你
  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235706.png)

* smcl：Stata默认的log file格式，可以保存各种颜色
  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235707.png)

* test：单色，便于文本编辑器中打开
  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235708.png)

* log name：
  通常只能有一个log file
  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235709.png)

  如果你给你的log file起一个名字(不是filename文件名),那么你可以同时打开好几个log file

  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203271235710.png)

* log close
  关闭log file
  `log close logname`



  一口气关闭所有log file
  `log close_all`