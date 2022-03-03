---
title: linux 基础运维(5c)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220055181.png
tags:
    - linux
    - 笔记
---
### date 命令

`date` 命令（重点）

date 打印或设置当前系统日期和时间

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052759.png)

### hwclock

`hwclock` 设置硬件使时间

hwclock --hctosys 设置系统时间为硬件时间

hwclock --systohc 设置硬件时间为系统时间



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052761.png)



### timedatectl

`timedatectl` 这个命令可以查询或修改系统时间

`timedatectl set-time 时间` 



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052762.png)

这里设置了 NTP 的意思是时刻同步我们系统时间的，关闭之后才能设置

`timedatectl set-time no` 这个可以让 NTP 关闭

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052763.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052764.png)



`timedatectl set-time 日期时间` 可以同时一次设置 **系统时间** 和 **硬件时间**



可以只设置时间：

`timedatectl set-time 11:11:11` 这个是设置时间



列出时区：`timedatectl list-timezones`

`timedatectl set-timezone ZONE`  设置时区



`chronyc makestep` 可以同步，但是用这个命令是需要 `ntp` 开启的

`timedatectl set-ntp yes`  

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052765.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052766.png)





需求：

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052767.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052768.png)

$()：括号里面的内容先执行，`$`的作用是打印出来



需求 创建一个文件：当前系统日期3天以后的文件

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052769.png)

### cal

`cal` 查看日历

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203040052770.png)

