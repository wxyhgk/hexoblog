---
title: linux 基础运维(3)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220055181.png
tags:
    - linux
    - 笔记
---
liunux下压缩与解压

# 1. 常见的压缩与解压缩工具

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145346.png)

只有 `zip` 才能压缩多个文件或目录

# 2. 工具的使用

## zip 工具

### 压缩：

zip  压缩后的文件  需要压缩的文件

注意 zip 压缩默认压缩后的格式是 .zip ;当然也可以加后缀 .zip，一般都加上

### 选项：

-r  递归压缩，压缩目录

### 解压缩：

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145351.png)



这样可以压缩，但是如果你想让 aal 这个目录也压缩成一个压缩文件，那么就需要加选项 `-r`



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145352.png)



### gzip 工具

`gzip`  需要压缩的单个文件



选项：

-d 解压缩

-r 递归压缩目录



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145353.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145354.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145355.png)



### bzip2

压缩 

bzip2  需要压缩的文件



选项：

`-d`  解压缩



### xz

`-z`  压缩 ，默认

`-d` 解压缩，或者 `unxz`



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202260145356.png)



