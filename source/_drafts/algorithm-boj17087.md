---
title: 백준 17087 숨바꼭질 6
categories:
  - null
date: 2021-11-03 11:24:40
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->
# 백준 17087 숨바꼭질 6
## 문제

최대 보폭을 구하는 문제

## 풀이

## 코드

```PYTHON
import sys

D = []
N,S = map(int, sys.stdin.readline().split())
A= list(map(int,sys.stdin.readline().split()))

def gcd(x,y):
    if x%y==0:
        return y
    else:
        return gcd(y,x%y)

for a in range(len(A)):
    D.append(abs(S-A[a]))

result = D[0]
for d in range(1,len(D)):
    result = gcd(D[d], result)
print(result)
```
