---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262109898.png
tags:
  - 量子化学
  - 笔记
title: 共价键理论(1)
math: true
---
# 一. 波恩-奥卡海姆 近似

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261644603.png" style="zoom:25%;" />



由于 原子核 比 电子 大上千倍，且核的速度远小于电子的速度，所以可以把核当成不动的，也就是可以忽略核的动能



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261644604.png" style="zoom:25%;" />

具体形式就是这样的：
$$
(-\frac{\hbar^{2}}{2 m} \sum_{i} \nabla_{i}^{2}+\sum_{k} \sum_{l>k} \frac{Z_{k} Z_{l} e^{2}}{4 \pi \varepsilon_{0} R_{k l}}-\sum_{k} \sum_{i} \frac{Z_{k} e^{2}}{4 \pi \varepsilon_{0} r_{k i}}+\sum_{i} \sum_{j>i} \frac{e^{2}}{4 \pi \varepsilon_{0} r_{i j}})\Psi=E\Psi
$$
由于原子核位置是确定的，所以

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261644605.png" style="zoom: 50%;" />

这部分就是不变的。



# 二. 氢分子离子结构

## 1. 列出方程



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261901094.png" style="zoom:33%;" />



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261648188.png" style="zoom: 50%;" />

由于只有一个电子，所以不包含电子的排斥能



为了更方便求解，我们使用 **原子单位制**(a.u.) ，然后可以得到下面的方程
$$
\left(-\frac{1}{2} \nabla^{2}-\frac{1}{r_{\mathrm{A}}}-\frac{1}{r_{\mathrm{B}}}+\frac{1}{R}\right) \Psi(x, y, z)=E \Psi(x, y, z)
$$
关于 **原子单位制** 的说明：

一个原子单位长度为 ： 
$$
a_{0}=\frac{4 \pi \varepsilon_{0} \hbar^{2}}{m_{e} e^{2}}=0.52917720859 \times 10^{-10} \mathrm{~m}
$$

$$
4 \pi \varepsilon_{0}=1 \text { a. u. }, \hbar=\sqrt{\frac{a_{0} m_{e} e^{2}}{4 \pi \varepsilon_{0}}}=1 \text { a. } u
$$

## 2. 精确求解

$$
\left( -\frac{1}{2}\nabla ^2-\frac{1}{r_{\mathrm{A}}}-\frac{1}{r_{\mathrm{B}}}+{\color[RGB]{178, 34, 34} \frac{\boldsymbol{1}}{\boldsymbol{R}}} \right) \Psi (x,y,z)=E\Psi (x,y,z)
\\
$$

这里面 ${\color[RGB]{178, 34, 34} 1/R}$ 为常数，我们把这部分移到右边去，合并到特征值 E 当中，可以得到：
$$
\left( -\frac{1}{2}\nabla ^2-\frac{1}{r_{\mathrm{A}}}-\frac{1}{r_{\mathrm{B}}} \right) \Psi _{\mathrm{el}}=\left( E-{\color[RGB]{178, 34, 34} \frac{\boldsymbol{1}}{\boldsymbol{R}}} \right) \Psi _{\mathrm{el}}
$$


我们使用 **共焦椭圆坐标系** 求解

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261722749.png" style="zoom:33%;" />

共焦椭圆坐标系中 采用变量 $\phi,\xi,\eta$ ：
$$
\psi_{\mathrm{el}}=L(\xi) M(\eta)(2 \pi)^{-1 / 2} \mathrm{e}^{\mathrm{i} m \phi}
$$

## 3. 变分原理和线性变分法

### **变分原理：**

$$
W=\frac{\int \phi^{*} \hat{H} \phi \mathrm{d} \tau}{\int \phi^{*} \phi \mathrm{d} \tau} \geqslant E_{0}
$$

根据边界条件选取一个试探函数$\phi$，根据变分原理，用数学中极小值的求法
$$
\left\{\begin{array}{l}\partial W / \partial c_{1}=0 \\ \partial W / \partial c_{2}=0 \\ \cdots \\ \partial W / \partial c_{n}=0\end{array}\right.
$$
确定一系列参数，让$\phi$的值达到最好



### **线性变分法：**

我们可以使用线性变分函数来做，并且这个是最容易计算的

采用线性变分函数，$\phi=\sum_{i} c_{i} \psi_{i}$，$\psi_i$ 是已知的

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105222.png" style="zoom: 50%;" />

由于 $\phi_i,\hat{H}$ 是已知的，所以上面红色部分是可求出来的。

然后我们根据
$$
\left\{\begin{array}{l}\partial W / \partial c_{1}=0 \\ \partial W / \partial c_{2}=0 \\ \cdots \\ \partial W / \partial c_{n}=0\end{array}\right.
$$
可以得到：
$$
\sum_{i} c_{i}\left(H_{i k}-W S_{i k}\right)=0
$$
然后我们可以得到 久期方程
$$
\left(\begin{array}{cccc}
H_{11}-S_{11} W & H_{12}-S_{12} W & \cdots & H_{1 n}-S_{1 n} W \\
H_{21}-S_{21} W & H_{22}-S_{22} W & \cdots & H_{2 n}-S_{2 n} W \\
\vdots & \vdots & \vdots & \vdots \\
H_{n 1}-S_{n 1} W & H_{n 2}-S_{n 2} W & \cdots & H_{n n}-S_{n n} W
\end{array}\right)\left(\begin{array}{c}
c_{1} \\
c_{2} \\
\vdots \\
c_{n}
\end{array}\right)=\left(\begin{array}{c}
0 \\
0 \\
0 \\
0
\end{array}\right)
$$
这个里面我们要求是 $c_i$,但是我们的 $W$ 不知道

根据线性代数的知识，我们要让这个方程的行列式为0.
$$
\left|H_{i k}-W S_{i k}\right|=\left|\begin{array}{cccc}
H_{11}-S_{11} W & H_{12}-S_{12} W & \cdots & H_{1 n}-S_{1 n} W \\
H_{21}-S_{21} W & H_{22}-S_{22} W & \cdots & H_{2 n}-S_{2 n} W \\
\vdots & \vdots & \vdots & \vdots \\
H_{n 1}-S_{n 1} W & H_{n 2}-S_{n 2} W & \cdots & H_{n n}-S_{n n} W
\end{array}\right|=0
$$
通过这个我们就可以求解出 $W$，然后回代到原始的矩阵方程中，就可以解出 $c_i$



**使用变分法可以在不解 Schrödinger 方程的情况下,解得体系的基态能量及波函数。变分法是量子力学中最常用的两种近似方法之一(另一种为微扰法)。**



## 4. 变分法求解 H2+



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203261901094.png" style="zoom:33%;" />

当
$$
\begin{aligned}
&\boldsymbol{R} \rightarrow \infty, \boldsymbol{r}_{\mathbf{A}} \rightarrow \infty \quad \phi \approx \psi_{B}=\frac{1}{\sqrt{\pi}} \mathrm{e}^{-r_{b}} \\
&\boldsymbol{R} \rightarrow \infty, \boldsymbol{r}_{\mathbf{B}} \rightarrow \infty \quad \phi \approx \psi_{A}=\frac{1}{\sqrt{\pi}} \mathrm{e}^{-r_{a}}
\end{aligned}
$$
尝试使用变分函数采用原子轨道的线性组合 **(LCAO-Linear Combination of Atomic Orbitals , Lennard-Jones, 1929)**
$$
\phi=C_{\mathrm{A}} \psi_{\mathrm{A}}+C_{\mathrm{B}} \psi_{\mathrm{B}}
$$
<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105223.png" style="zoom:50%;" />

注意这些积分都是已知的，可以求出来的



移项之后可以得到：
$$
W\left(c_{\mathrm{A}}^{2}+2 c_{\mathrm{A}} c_{\mathrm{B}} S+c_{\mathrm{B}}^{2}\right)=c_{\mathrm{A}}^{2} H_{\mathrm{AA}}+2 c_{\mathrm{A}} c_{\mathrm{B}} H_{\mathrm{AB}}+c_{\mathrm{B}}^{2} H_{\mathrm{BB}}
$$
然后做偏微分：

对 $c_A,c_B$ 做偏微分：
$$
\begin{aligned}
&W\left(2 c_{\mathrm{A}}+2 c_{\mathrm{B}} S\right)+\frac{\partial W}{\partial c_{\mathrm{A}}}\left(c_{\mathrm{A}}^{2}+2 c_{\mathrm{A}} c_{\mathrm{B}} S+c_{\mathrm{B}}^{2}\right)=2 c_{\mathrm{A}} H_{\mathrm{AA}}+2 c_{\mathrm{B}} H_{\mathrm{AB}} \\
&W\left(2 c_{\mathrm{A}} S+2 c_{\mathrm{B}}\right)+\frac{\partial W}{\partial c_{\mathrm{B}}}\left(c_{\mathrm{A}}^{2}+2 c_{\mathrm{A}} c_{\mathrm{B}} S+c_{\mathrm{B}}^{2}\right)=2 c_{\mathrm{A}} H_{\mathrm{AB}}+2 c_{\mathrm{B}} H_{\mathrm{BB}}
\end{aligned}
$$
然后我们之前的要求是求最小值，所以**一阶偏导都是0**

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105224.png" style="zoom:50%;" />

然后可以整理得到：
$$
\left\{\begin{array}{l}
c_{\mathrm{A}}\left(H_{\mathrm{AA}}-W\right)+c_{\mathrm{B}}\left(H_{\mathrm{AB}}-W S\right)=0 \\
c_{\mathrm{A}}\left(H_{\mathrm{AB}}-W S\right)+c_{\mathrm{B}}\left(H_{\mathrm{BB}}-W\right)=0
\end{array}\right.
$$
 注意这个里面$c_A,c_B$是变量，是我们要求的，要让这个方程有解，我们要求久期行列式为0
$$
\left|\begin{array}{cc}
H_{\mathrm{AA}}-W & H_{\mathrm{AB}}-W S \\
H_{\mathrm{AB}}-W S & H_{\mathrm{BB}}-W
\end{array}\right|=0
$$
对于 $H_2^+$ 来说，两个核是相等的，所以 $H_{AA}=H_{BB}$
$$
\begin{aligned}
&E_{1}=W_{1}=\frac{H_{\mathrm{AA}}+H_{\mathrm{AB}}}{1+S} \\
&E_{2}=W_{2}=\frac{H_{\mathrm{AA}}-H _{\mathrm{AB}}}{1-S}
\end{aligned}
$$
求出波函数
$$
\begin{gathered}
\phi_{1}=\frac{1}{\sqrt{2+2 S}}\left(\psi_{\mathrm{A}}+\psi_{\mathrm{B}}\right) \\
\phi_{2}=\frac{1}{\sqrt{2-2 S}}\left(\psi_{\mathrm{A}}-\psi_{\mathrm{B}}\right)
\end{gathered}
$$

## 5. 几个积分的说明

### 重叠积分

$$
S_{\mathrm{AB}}=\int \psi_{\mathrm{A}}^{*} \psi_{\mathrm{B}} \mathrm{d} \tau=\int \psi_{\mathrm{B}}^{*} \psi_{\mathrm{A}} \mathrm{d} \tau=S_{\mathrm{BA}}
$$

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105225.png" style="zoom:50%;" />

**反映两个原子轨道在空间的重叠程度**

 

### 库伦积分

$$
\begin{aligned}
H_{\mathrm{AA}} &=\int \psi_{\mathrm{A}}^{*} \hat{H} \psi_{\mathrm{A}} \mathrm{d} \tau=E_{\mathrm{H}}+\frac{1}{R}-\int \psi_{\mathrm{A}}^{*} \frac{1}{r_{b}} \psi_{\mathrm{A}} \mathrm{d} \tau \\
&=E_{\mathrm{H}}+\left(\frac{1}{R}+1\right) e^{-2 R}=E_{\mathrm{H}}+J
\end{aligned}
$$



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105226.png" style="zoom: 40%;" />



### 交换积分

$$
\begin{gathered}
H_{\mathrm{AB}}=\int \psi_{\mathrm{A}}^{*} \hat{H} \psi_{\mathrm{B}} \mathrm{d} \tau=E_{H} S+\frac{S}{R}-\int \psi_{\mathrm{A}}^{*} \frac{1}{r_{a}} \psi_{\mathrm{B}} \mathrm{d} \tau=E_{H} S+K \\
K=\frac{S}{R}-\mathrm{e}^{-R}(1+R)=\left(\frac{1}{R}-\frac{2 R}{3}\right) \mathrm{e}^{-R}
\end{gathered}
$$

<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105227.png" style="zoom:50%;" />

交换积分表明当电子同时属于两个或两个以上轨道时，比它只属于单一轨道具有更低的能量，这个能量降低来源于共振，所以被称为交换积分，用 $\beta$ 表示



能量曲线核分子轨道能级
$$
\begin{aligned}
&E_{2}=E_{H}+\frac{J-K}{1-S} \\
&E_{1}=E_{H}+\frac{J+K}{1+S}
\end{aligned}
$$
<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105228.png" style="zoom: 50%;" />

只选取氢原子基态(1s)作尝试函数得到的分子轨道不能定量说明$H^+$的成键,但随着尝试函数的改进(如加入两个氢原子的2s和2p轨道或更多、或考虑收缩效应和极化效应增加参数),可以得到与Schrödinger方程精确求解接近乃至一致的结果。



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105229.png" style="zoom:50%;" />



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105230.png" style="zoom:50%;" />



<img src="https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203262105871.png" style="zoom:50%;" />

成键轨道上，电子在两核间出现几率多(比单独两个氢原子时)，电子与两核吸引增加，电子吸引着两核。

电子屏蔽了两核之间的排斥力，使排斥位能减小，这就是原子间存在较强的相互作用的原因。 

