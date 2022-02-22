---
title: linux Bash的使用方法
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202220055181.png
tags:
    - linux
    - 笔记
---
Bash 的标准输入和输出

# 1 名词解释

* 标准输入(stdin) :键盘上的输入 文件描述符->0
* 标准输出(stdout):屏幕上正确的输出 文件描述符 ->1
* 标准错误（stderr):屏幕上错误的输出 文件描述符 ->2

# 2 相关符号

`>` 标准输出重定向，覆盖重定向，`1>` 或 `>` 标准输出重定向, `2>` 标准错误重定向

`>>` 重定向追加， `1>>` 标准输出追加，`>>` 标准错误追加



`<` 标准输入

`&>` 标准输出和错误 一起重定向



![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202222329731.png)



# 3 echo 命令

echo 会将 **输入的字符串** 送往 **标准输出**，并在最后加上换行符，可以理解为打印字符串。



常见选项：

* -n 不输出最后的换行符
* -e 解释转译字符

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202222329732.png)

