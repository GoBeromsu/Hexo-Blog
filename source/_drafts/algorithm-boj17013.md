---
title: 백준 17013 골드바흐 파티션
categories:
  - algorithm
date: 2021-11-04 15:07:12
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 17013 골드바흐 파티션
## 문제

## 풀이

## 코드

```python
import sys

n = int(sys.stdin.readline())
numbers = [int(sys.stdin.readline()) for i in range(n)]
m = max(numbers)
arr = [False,False]+[True]*(max(numbers)-1)

def checkPrime(num):
    n = int(num **0.5)+1
    for i in range(2,n):
        for j in range(i*2,num,i):
            arr[j]=False

checkPrime(m)
for num in numbers:
    cnt=0
    for i in range((num//2)+1):
        if arr[i] and arr[num-i]:
            cnt+=1
    print(cnt)

```