---
title: Jupyter 基础绘图1
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210145263.png
tags:
    - 教程
    - Jupyter
---

首先是引入 **matplotlib.pyplot** 才能画图

```python
import matplotlib.pyplot as plt
```

一个示例

```python
# 1.创建画布
plt.figure(figsize=(20,8),dpi=100) # figsize=设置图像比例，dpi=设置图像清晰图
# 2.绘制图像
plt.plot([1,2,3,4],[4,8,1,5])

# 3.图像显示
plt.show()
```


![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028305.png)
    


matplotlib图像构造

![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028913.png)

# 1 实现基础绘图功能

## 1.1实现基础功能


```python
import random
```


```python
# 0.准备数据
x=range(60)
y_shanghai=[random.uniform(15,18) for i in x]

# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制图像
plt.plot(x,y_shanghai)

# 3.图像显示
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028306.png)
​    


## 1.2实现其他功能


```python
# form pylab import mpl
# #设置中文字体
# mpl.reParams["font.sans-serif"]=["SimHei"]
# mpl.rcParams["axes.unicode_minus"]=False
# 0.准备数据
x=range(60)
y_shanghai=[random.uniform(15,18) for i in x]

# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制图像
plt.plot(x,y_shanghai)

## 2.1添加x，y轴刻度
### 设置x，y轴刻度
x_ticks_lable=["11dian{}fen".format(i) for i in x]
y_ticks=range(41)

### 修改x，y轴坐标刻度显示
plt.xticks(x[::5],x_ticks_lable[::5])#坐标刻度不可以通过字符串进行修改
plt.yticks(y_ticks[::5])

## 2.2添加网格
plt.grid(True,linestyle="--",alpha=0.5)

## 2.3添加描述信息
plt.xlabel("time")
plt.ylabel("wendu")
plt.title("plot name",fontsize=20)

## 2.4 图像保存
plt.savefig("./test.png")#保存路径要放在plt.show的前面,因为plt.show()会释放资源，如果在show之后就会保存空图片

# 3.图像显示
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028307.png)
​    


# 2 在一个坐标系下绘制多个图像


## 2.1 多次plot


```python
x=range(60)
y_shanghai=[random.uniform(15,18) for i in x]
y_beijing=[random.uniform(1,3) for i in x]

# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制图像
plt.plot(x,y_shanghai,label="shanghai")
plt.plot(x,y_beijing,color="r",linestyle="--",label="beijing")

## 显示图例


## 2.1添加x，y轴刻度
### 设置x，y轴刻度
x_ticks_lable=["11dian{}fen".format(i) for i in x]
y_ticks=range(41)

### 修改x，y轴坐标刻度显示
plt.xticks(x[::5],x_ticks_lable[::5])#坐标刻度不可以通过字符串进行修改
plt.yticks(y_ticks[::5])

## 2.2添加网格
plt.grid(True,linestyle="--",alpha=0.5)

## 2.3添加描述信息
plt.xlabel("time")
plt.ylabel("wendu")
plt.title("plot name",fontsize=20)

## 2.4 图像保存
plt.savefig("./test.png")#保存路径要放在plt.show的前面,因为plt.show()会释放资源，如果在show之后就会保存空图片

##显示图例
plt.legend(loc=0)

# 3.图像显示
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028308.png)
​    


# 3 多个坐标系坐标系


```python
import matplotlib.pyplot as plt
plt.rcParams['font.sans-serif'] = [u'SimHei']
plt.rcParams['axes.unicode_minus'] = False
# 0.准备数据
x=range(60)
y_shanghai=[random.uniform(15,18) for i in x]
y_beijing=[random.uniform(1,3) for i in x]

# 1.创建画布
fig, axes=plt.subplots(nrows=1,ncols=2,figsize=(20,8),dpi=100)#nrow代表几行，ncols代表几列

# 2.绘制图像
axes[0].plot(x,y_shanghai,label="上海")
axes[1].plot(x,y_beijing,color="r",linestyle="--",label="北京")

 ## 2.1添加x，y轴刻度
 ### 设置x，y轴刻度
x_ticks_label=["11点{}分".format(i) for i in x]
y_ticks=range(41)


 ### 修改x，y轴坐标刻度显示
axes[0].set_xticks(x[::5])
axes[0].set_yticks(y_ticks[::5])
axes[0].set_xticklabels(x_ticks_label[::5])
axes[1].set_xticks(x[::5])
axes[1].set_yticks(y_ticks[::5])
axes[1].set_xticklabels(x_ticks_label[::5])

 ## 2.2添加网格
axes[0].grid(True,linestyle="--",alpha=1)
axes[1].grid(True,linestyle="--",alpha=1)

 ## 2.3添加描述信息
axes[0].set_xlabel("时间")
axes[0].set_ylabel("温度")
axes[0].set_title("上海中文11点到12点温度变化图",fontsize=20)
axes[1].set_xlabel("时间")
axes[1].set_ylabel("温度")
axes[1].set_title("北京中午11点到12点温度变化图",fontsize=20)

 ## 2.4 图像保存
plt.savefig("./test1.png")#保存路径要放在plt.show的前面,因为plt.show()会释放资源，如果在show之后就会保存空图片

 ##2.5显示图例
axes[0].legend(loc=0)
axes[1].legend(loc=0)

# 3.图像显示
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028309.png)
​    


# 4 折线图的应用


```python
import numpy as np

# 0.准备数据
x = np.linspace(-10,10,1000)
y = np.sin(x)

# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制函数图像
plt.plot(x,y)

# 3.显示图像
plt.show()
```


​    
![](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210028310.png)
​    


# 5 小结

* 添加x,y轴刻度
    * plt.xticks()
    * plt.yticks()
    注意传递过去的第一个参数必须是数字，不能是字符串，如果是字符串，就需要进行替换操作

* 添加网格
    * plt.grid(linesyle="--",alpha=1)
    
* 添加描述信息
    * plt.xlabel()
    * plt.ylabel()
    * plt.title()
    
* 图像保存
    * plt.savefig("路径")
    
* 多次plot
    * 直接进行添加就行了
    
* 显示图例
    * plt.legend(loc="best")
    * 一定要在plt.plot里面添加一个label,不如没办法显示

* 多个坐标系显示
    * plt.subplot(nrows=,ncols=)
    
* 折线图的应用
    * 数据的变化
    * 数学函数的显示
