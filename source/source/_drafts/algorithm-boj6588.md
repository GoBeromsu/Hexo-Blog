---
title: 백준 6588 골드바흐의 추측
categories:
  - null
date: 2021-11-02 13:30:33
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 6588 골드바흐의 추측

이래저래 시간초과가 나길래 당황스러웠던 문제이다

## 문제

## 풀이

## 코드
```python
import sys

decimal = [False,False]+[True]*999999

for i in range(2,1001):
    if decimal[i]==True:
        for j in range(i*2,1000001,i):
            decimal[j]=False

while 1:
    n = int(sys.stdin.readline())
    if n ==0:
        break

    a=0
    b=n
    for _ in range(1000000):
        if decimal[a] and decimal[b]:
            print(f"{n} = {a} + {b}")
            break
        a+=1
        b-=1
        
    else:
        print("Goldbach's conjecture is wrong.")
        break
```
## Reference

[백준 6588 파이썬 풀이: 골드바흐의 추측](https://yoonsang-it.tistory.com/52)