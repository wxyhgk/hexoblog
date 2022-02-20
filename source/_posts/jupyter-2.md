---
title: Jupyter 基础绘图2
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210145263.png
tags:
    - Jupyter
    - 教程
---

# 常见图像绘制

Matplotlib 可以绘制 **折线图，散点图，柱状图，直方图，饼状图**

折线图之前已经说明过来，这里不再说明

## 1 散点图的绘制

首先导入 matplotlib.pyplot


```python
#导入包
import matplotlib.pyplot as plt 

from pylab import mpl
# 设置中文字体
mpl.rcParams["font.sans-serif"]=["SimHei"]
# 设置正常显示符号
mpl.rcParams["axes.unicode_minus"]=False
```


```python
# 0.准备数据
x = [225.98, 247.07, 253.14, 457.85, 241.58, 301.01, 20.67, 288.64,
163.56, 120.06, 207.83, 342.75, 147.9 , 53.06, 224.72, 29.51,
21.61, 483.21, 245.25, 399.25, 343.35]
y = [196.63, 203.88, 210.75, 372.74, 202.41, 247.61, 24.9 , 239.34,
140.32, 104.15, 176.84, 288.23, 128.79, 49.64, 191.74, 33.1 ,
30.74, 400.02, 205.35, 330.64, 283.45]

# 1.创建画布
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制散点图
plt.scatter(x, y)

# 3.显示图像
plt.show()

```


​    
![png](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210142474.png)
​    


## 2 柱状图绘制


```python
# 0.数据准备
## 电影名字
move_name=['雷神3:诸神黄昏','正义联盟','东方快车谋杀案','寻梦环游记','全球风暴','降魔传','追捕','七十七天','密战','狂兽','其它']
## 横坐标
x=range(len(move_name))
## 票房数据
y= [73853,57767,22354,15969,14839,8725,8716,8318,7916,6764,52222]
           
# 1.画布创建
plt.figure(figsize=(20,8),dpi=100)

# 2.绘制柱状图
plt.bar(x,y,color=['b','r','g','y','c','m','y','k','c','g','b'],width=0.6)
## 2.1 修改x轴
plt.xticks(x,move_name)
## 2.2 添加网格
plt.grid(linestyle="--",alpha=0.6)
## 2.3 添加标题
plt.title("电影票房对比",fontsize=20)

# 3.显示图像
plt.show()
```


​    
![png](https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202202210142475.png)
   
