---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221333771.png
tags:
  - 教程
  - stata
  - 笔记
title: stata教程(1)
---
# 初步数据观测

sysuse auto ,clear

## describe 命令

describe [varlist]

![Untitled](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221328713.png)

describe short 

![Untitled](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221328719.png)

describe price

![Untitled](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221328720.png)

## count

count

count if

![Untitled](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221328721.png)

## isid（Is ID or not）

isid varlist

## unique

首先用 ssc install unique 安装这个包，然后才能用

![Untitled](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203221328722.png)