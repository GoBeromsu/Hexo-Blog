---
emoji: ๐
categories: algorithm
title: ๋ฐฑ์ค 2407 ์กฐํฉ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
description:
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ๋ฐฑ์ค 2407 ์กฐํฉ

## ๋ฌธ์ 

nCm์ ์ถ๋ ฅํ๋ค.

## ํ์ด

```python
import sys
from itertools import combinations

n,m = map(int,sys.stdin.readline().split())
numbers=[0 for i in range(101)]
numbers[1],numbers[2]=1,2
for i in range(3,n+1):
    numbers[i]=numbers[i-1]*i

print(numbers[n]//(numbers[m]*numbers[n-m]))
```