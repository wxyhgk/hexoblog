---
title: linux 基础运维(4)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220055181.png
tags:
    - linux
    - 笔记
---
# linux 打包压缩

tar可以将多个文件打包，不会去改变文件的属性信息，这个很关键！

用法：

`tar 选项  打包后的文件  需要打包的文件`

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202270004301.png "")

一般而言，把f选项放到最后面

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202270004302.png "")



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202270004303.png "")



一次性打包多个文件，比如说我们想把根下的** /boot **目录和 **/test **目录打包，怎么做呢？

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202270004304.png "")




1以上选项前面的横杠"-"可以省略
2如果已经将文件压缩打包，那么就不能追加；如果只是打包就可以追加。
3参数顺序需要注意，最好把-f参数放到所有参数后面。
4.当出现以下提示时，加一个大P参数解决。
tar：Removing 1eading`/'from member names



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202270004305.png "")



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202270004306.png "")

