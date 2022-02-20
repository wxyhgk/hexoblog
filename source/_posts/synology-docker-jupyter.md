---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202041589.png
tags:
  - 教程
  - 群晖
  - docker
  - jupyter
title: 群晖docker安装jupyter
---

# 一 拉取镜像

搜索 **jupyter** 然后下载就行了

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037594.png)

下载好后安装部署

点击启动进入高级设置

## 1 空间设置

`/home/jovyan/jupyter work`

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037595.png)

## 2 端口设置

本地端口改成没有被占用的端口就行

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037596.png)

## 3 环境设置

增加一个环境变量：**JUPYTER_ENABLE_LAB**

填入：**yes**

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037597.png)

然后启动就行了

## 4 获取token

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037598.png)

# 二 修改程密码登录

完成上面步骤之后就可以用 ip +你设置的端口号访问了。

会出现下面的要你填

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037599.png)

输入你的token和你想设置的密码，就能成功登录了。

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037600.png)

但是这样有个问题就是每次都要输入token和密码，特别麻烦，而且token还是很长的，所以就需要改成密码登录，我看了官方的文档看不懂，然后在网上查了很多资料才知道怎么修改

打开docker进入终端，向我这样输入

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202202037601.png)

输入：

`ipython`

然后会让你填

`[1]`

`[2]`

分别填入：from notebook.auth import passwd 和 passwd() 就行了

最后会出现这个 out[2] 后面带一大堆数字，复制下来后面要用

然后**进入群晖的ssh，注意是群晖的ssh，不是dock中！！！！！**

输入：`jupyter notebook --generate-config`  来生成配置文件

然后：`vim ~/.jupyter/jupyter_notebook_config.py`  修改配置文件

然后输入：

```bash
c.NotebookApp.ip='*'
c.NotebookApp.password = u'刚刚的out[2]的大段文字'
c.NotebookApp.open_browser = True
c.NotebookApp.port =8888
```

修改后保存，以后登录就直接可以用密码登录了！

# 三 参考文章

[折腾NAS 篇五：利用docker安装Jupyter交互式编程和笔记工具_服务软件_什么值得买](https://post.smzdm.com/p/az5expz0/)

[Synology 安裝jupyter-notebook](https://www.jianshu.com/p/042b7a0e2204)

[远程运行jupyter notebook：密码登录和token登录_小白水手的博客-CSDN博客_jupyter notebook 登录](https://blog.csdn.net/ACBattle/article/details/89401165)