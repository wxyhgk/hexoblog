---
title: linux 运维基础(2)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220055181.png
tags:
    - linux
    - 笔记
---

# linux 文件查找

## 1.1 命令查找

linux 一切皆文件

* `which` 	查找 **命令的绝对路径**
* `whereis`  查找 **命令的路径** 和 **命令的文档手册**



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145403.png)



## 1.2 文件查找(find)

`find`  命令**精确**查找，磁盘搜索，IO读写，cpu开销大



### 1.2.1 找出来输出到屏幕

`find  空格  选项  关键字`



（1）根据文件名查找

- `-name`  按照文件名查找，要考虑大小写
- `iname`  按照文件名查走，忽略大小写



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145404.png)



（2）根据文件类型查找

linux 文件类型：d	f	b	c	l	p	s



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145405.png)



（3）根据文件大小查找

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145406.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145407.png)



（4）按照文件属性查找

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145408.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145409.png)



（5）根据时间查找

| 选项     | 作用                       | 其他说明              |
| -------- | -------------------------- | --------------------- |
| `-mtime` | 按照 **文件修改时间** 查找 | -n 表n天内，+n指n天前 |
| `-atime` | 按照 **文件访问时间** 查找 |                       |
| `-ctime` | 按照 **文件创建时间** 查找 |                       |



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145410.png)

直接用天数有个问题，就是如果不足24小时是不算一天的，什么意思？

比如说 昨天的一个文件是8:00创建的，今天到了7:00 只有23个小时，也就是没有一天，所以你用的时候有时候就会出现问题，那么怎么办呢？

可以用这个命令：

```bash
find ./ -type f -daystart -mtime 2
```

加上这个 `-daystart` 选项就能避免这种情况了。



### 1.2.2 找到文件执行命令

`find  路径  选项  关键字  动作`



| 常见动作  | 说明                 |
| --------- | -------------------- |
| `-print`  | 打印到屏幕，默认选项 |
| `-delete` | 删除                 |
| `-ls`     | 列出详细信息         |



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145411.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145412.png)



这些都是默认的，我们想做其他动作比如 拷贝，移动怎么办呢？

| 选项    | 作用                 |
| ------- | -------------------- |
| `-ok`   | 这个是执行一次问一次 |
| `-exec` | 直接作用，不询问     |

使用这两个命令，需要注意

* -exec  shell命令  后面要加 空格，反斜杠，和分号
* { } 表示 find 找出来的文件



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202230145413.png)