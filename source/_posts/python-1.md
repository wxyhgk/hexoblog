---
index_img: https://cdn.jsdelivr.net/gh/wxyhgk/paper-picture/202203292031954.png
tags:
  - 笔记
  - Python
math: true
title: Python-day4
---
> 这些算法自己想不到，蛮难的，需要多看


## 循环结构

### for in循环

计算1~100的求和


```python
sum = 0
for x in range(101):
    sum +=x
print(sum)
```

    5050


求出100内所有偶数的和


```python
sum = 0
for x in range(2,101,2):
    sum+=x
print(sum)
```

    2550

### while 循环
做一个猜数字小游戏，出一个100内的随机整数，玩家输入自己猜的数字，计算机给出相应的提示信息，如果猜对了，计算机提示用户一共猜了多少次，游戏结束，否则游戏继续


```python
import random

a=random.randint(1,100)
counter=0
while True:
    counter+=1
    num=int(input('请输入：'))
    if num < a:
        print('大一点')
    elif num>a:
        print('小一点')
    else:#else while
        print('你猜对了')
        break
print('你总共猜了%d次' % counter)
if counter >7:
    print('猜的次数太多了你该补充智商了')
```

    请输入： 50


    小一点


    请输入： 10


    大一点


    请输入： 10


    大一点


    请输入： 50


    小一点


    请输入： 40


    小一点


    请输入： 30


    小一点


    请输入： 20


    小一点


    请输入： 10


    大一点


    请输入： 15


    大一点


    请输入： 17


    大一点


    请输入： 18


    大一点


    请输入： 19


    你猜对了
    你总共猜了12次
    猜的次数太多了你该补充智商了

## 小项目
做一个乘法口诀表


```python
for i in range(1, 10):

    for j in range(1, i + 1):

        print('{}x{}={}\t'.format(j, i, i * j), end='' )#print默认是打印一行，结尾加换行。end=' '意思是末尾不换行，加空格

    print('\n')
```

    1x1=1	
    
    1x2=2	2x2=4	
    
    1x3=3	2x3=6	3x3=9	
    
    1x4=4	2x4=8	3x4=12	4x4=16	
    
    1x5=5	2x5=10	3x5=15	4x5=20	5x5=25	
    
    1x6=6	2x6=12	3x6=18	4x6=24	5x6=30	6x6=36	
    
    1x7=7	2x7=14	3x7=21	4x7=28	5x7=35	6x7=42	7x7=49	
    
    1x8=8	2x8=16	3x8=24	4x8=32	5x8=40	6x8=48	7x8=56	8x8=64	
    
    1x9=9	2x9=18	3x9=27	4x9=36	5x9=45	6x9=54	7x9=63	8x9=72	9x9=81	


​    

输入一个正整数，判读是不是素数


```python
from math import sqrt

num=int(input('请输入一个整数'))
sqrt_num=int(sqrt(num)) # 质因数分解 从1算到它的平方根就可以了。没有必要继续算。

is_prime=True
for x in range(2,sqrt_num+1):
    if num % x ==0:
        is_prime=False
        break
if is_prime and num !=1: # 这里排除了1，1既不是素数也不是合数 
        print('%d是素数' % num)
else:
    print('%d 不是素数' % num)
```

    请输入一个整数 10


    10 不是素数


输入两个正整数，计算他们的最大公约数和最小公倍数


```python
x=int(input('输入一个数'))
y=int(input('输入另一个数'))

if x>y:
    x,y=y,x

for i in range(x,0,-1):#最大公约数就是最大的都能整除的数 所以range是反着的
    if x % i ==0 and y % i ==0:
        print('%d和%d的最大公约数是%d' % (x,y,i))
        print('%d和%d的最小公倍数是%d' %(x,y,x*y//i)) # // 代表取整，取小数的整数部分，向下取整
        break
```

    输入一个数 10
    输入另一个数 7


    7和10的最大公约数是1
    7和10的最小公倍数是70



```python
row=int(input('请输入行数:'))

for i in range(row):
    for _ in range(i+1): # 我们可以使用"_"来表示它只是一个临时值：
        print('*',end='')
    print()
```

    请输入行数: 10


    *
    **
    ***
    ****
    *****
    ******
    *******
    ********
    *********
    **********



```python
row=int(input('请输入行号'))

# 这个好巧妙哦！
for i in range(row):
    for j in range(row):
        if j<row-i-1:
            print(' ',end=' ')# python中“end=”是“print()”函数中的一个参数，会使该函数关闭“在输出中自动包含换行”的默认行为。print默认是打印一行，结尾加换行，end传递一个空字符串，表示这个语句没结束。
        else:
            print('*',end=' ')
    print()
```

    请输入行号 10


                      * 
                    * * 
                  * * * 
                * * * * 
              * * * * * 
            * * * * * * 
          * * * * * * * 
        * * * * * * * * 
      * * * * * * * * * 
    * * * * * * * * * * 



```python
row=int(input('请输入小于5行的数字'))
for i in range(row):
    for _ in range(row-i-1):
        print(' ',end='')
    for _ in range(2*i+1):
        print('*',end='')
    print()
```

    请输入小于5行的数字 5


        *
       ***
      *****
     *******
    *********


