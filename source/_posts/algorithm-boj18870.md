---
emoji: π
categories: algorithm
title: λ°±μ€ 18870 μ’ν μμΆ
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->

# λ°±μ€ 18870 μ’ν μμΆ

## λ¬Έμ 

μμ§μ  μμ Nκ°μ μ’ν X1, X2, ..., XNμ΄ μλ€. μ΄ μ’νμ μ’ν μμΆμ μ μ©νλ €κ³  νλ€.

Xiλ₯Ό μ’ν μμΆν κ²°κ³Ό X'iμ κ°μ Xi > Xjλ₯Ό λ§μ‘±νλ μλ‘ λ€λ₯Έ μ’νμ κ°μμ κ°μμΌ νλ€.

X1, X2, ..., XNμ μ’ν μμΆμ μ μ©ν κ²°κ³Ό X'1, X'2, ..., X'Nλ₯Ό μΆλ ₯ν΄λ³΄μ.

## νμ΄

```python
import sys

n = int(sys.stdin.readline())
numbers = list(map(int,sys.stdin.readline().split()))
sNumbers = sorted(list(set(numbers)))
numDic={}
for num in numbers:
    numDic[num]=0

for i in range(len(sNumbers)):
    numDic[sNumbers[i]]=i

for i in range(n):
    print(numDic[numbers[i]], end=' ' )

```

μκ°ν΄λ³΄λ μ£Όμ΄μ§ μ«μλ€μ μ€λ³΅μ μ κ±°νκ³ , μ λ ¬νλ©΄ κ° μΈλ±μ€κ° μκΈ°λ³΄λ€ μμ μμ μ«μκ° λλ€.

-10 -9 1 2 3 μ²λΌ μ λ ¬λ μνμμ -10μ 0κ°, -9λ 1κ°μμΌλ‘ κ΅¬ν  μ μλ κ²μ΄λ€.