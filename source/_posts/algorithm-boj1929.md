---
emoji: π
categories: algorithm
title: λ°±μ€ 1929 μμ κ΅¬νκΈ°
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->

# λ°±μ€ 1929 μμ κ΅¬νκΈ°
## λ¬Έμ 
Mμ΄μ Nμ΄νμ μμλ₯Ό λͺ¨λ μΆλ ₯νλ νλ‘κ·Έλ¨μ μμ±νμμ€.
## νμ΄

* Nμ΄νμ μμλ€μ λͺ¨λ κ΅¬ν ν Mκ³Ό N μ¬μ΄μ μμλ₯Ό μΆλ ₯νλ€

## CODE

```
import sys
M,N = map(int, sys.stdin.readline().split())
arr = [False,False] + [True] * (N-1)
for i in range(2,N+1):
    for j in range(2*i,N+1,i):
        arr[j] = False
for i in range(M,N+1):
    if arr[i] == True:
        print(i)
```