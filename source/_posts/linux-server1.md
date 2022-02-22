---
title: linux 运维基础(1)
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220055181.png
tags:
    - linux
    - 笔记
---
# linux基础1

## 1 关机与重启

**关机与重启只有管理员才能进行操作**

关机

`shutdown -h now `  立刻马上关机

`shutdown -h 60`  60分钟之后关机

`shutdown  - c` 取消关机



重启

`reboot` 重启

`shutdown -r now` 立刻关机

`shutdown -r 10` 10分钟后重启



**ctrl + l** 清屏

## 2 linux系统目录树的结构

### 2.1 目录树结构

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/image-20220221205900043.png)

### 2.2 文件路径表示方法

绝对路径：

* 以根开头的，用 `/`



相对路径：

* 相对于**当前所在路径**而言，用 `./`

* 当前目录的上一级目录，用 `..` 或者 `../`
* 当前**用户家目录**，用 `～ `，上次工作路径用 `-`



路径切换和查看

* `pwd` 查看当前路径
* `cd` 更改当前路径



## 3 文件操作管理

linux下一切皆文件

* 所有命令都需要在一个载体下执行，这个载体就叫做 **终端**
* 终端上所有的命令都需要翻译解析一下计算机才能理解并执行
* 翻译这个的东西叫做 **SHELL解释器** ，RedHat 和 Centos默认解释器叫做 **Bash**，所以需要符合 **Bash** 的语法



```powershell
命令 可选项 参数

命令：整条 Shell 的主体
选项：会影响或微调命令的行为，用 - 或 --
参数：命令作用的对象

ls -l /root
```



### 3.1 判断文件类型

常见文件类型

* c  字符设备，**输入输出的设备**：键盘，鼠标等

  ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/image-20220221213748734.png)

  用 `file 文件` 可以判断文件的类别



* b 块设备，**存储设备**：u盘，磁盘等
* l 软连接文件 类似于 win10 下的快捷方式
* d 目录文件 类似于 win10 的文件夹
* f或- 类似于win10下的记事本，word，可以用命令进行编辑
* p 管道文件 
* s 套接文件



### 3.2 列出目录内容

ls命令

| 命令  | 作用                                  |
| ----- | ------------------------------------- |
| ls -a | all，查看目录下所有文件，包括隐藏文件 |
| ls -l | 查看详细信息                          |

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/image-20220221220305277.png)



其他命令

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/image-20220221222529826.png)



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/image-20220221222903767.png)



### 3.3 创建目录

mkdir

mkdir+某个文件夹名称就行了，很简单

mkdir -p 某个路径，一次性创建多个目录

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/image-20220221225056633.png)



### 3.4 创建文件

touch+文件就行了很简单

touch -a file -t "2022111111" 这是修改时间



### 3.5 查看文件内容

* `cat`命令：一般查看小文件，从第一行道最后一行 列出来。

  * -n ：显示行号

  * -A： 显示控制字符，如换行，制表符等

    ![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220057845.png)



* `tac` 命令:与cat相反，这个是反着看

  

* less 查看大文件，more 也可以

  * 按 空格 是一页一页翻，按 回车键 是一行一行看
  * 按 q 是退出

  

* `head`  ` tail`

  * `head `默认查看前10行  
  * `tail` 默认查看后10行 tail -2 路径 查看某个文件的倒数两行
  * `-f `表示动态查看



### 3.6 拷贝文件cp

注意是：**本地拷贝**

拷贝文件直接拷贝就行了

cp 选项 拷贝的文件 拷贝到哪去

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220036161.png)



拷贝目录需要加 -r



### 3.7 移动或重命名 mv

* 移动文件用法（不同路径下）
  mv  需要移动的文件  需要移动到的路径



* 重命名用法（相同路径）
  mv  原来的文件名字  现在的文件名字





### 3.8 删除文件rm

`rm -r`  递归删除

`rm -f `  直接删除不提示

`rm -rf *` 删除当前目录下的所有文件

