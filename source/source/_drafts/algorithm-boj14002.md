---
title: 백준 140002 가장 긴 증가하는 부분 수열 4
categories:
  - algorithm
date: 2021-11-10 00:37:37
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 140002 가장 긴 증가하는 부분 수열 4
## 문제
수열 A가 주어졌을 때, 가장 긴 증가하는 부분 수열을 구하는 프로그램을 작성하시오.

예를 들어, 수열 A = {10, 20, 10, 30, 20, 50} 인 경우에 가장 긴 증가하는 부분 수열은 A = {10, 20, 10, 30, 20, 50} 이고, 길이는 4이다.
## 풀이

## 코드
```python
import sys

num = int(sys.stdin.readline())
numbers = list(map(int,sys.stdin.readline().split()))

dp = [1 for i in range(num)]

for i in range(num):
    for j in range(i):
        if numbers[i]>numbers[j]:
            dp[i] = max(dp[i],dp[j]+1)
        
maxLen = max(dp)
print(maxLen)
idx = dp.index(maxLen)
result = []

while idx>=0:
    if dp[idx]==maxLen:
        result.append(numbers[idx])
        maxLen-=1
    idx-=1
while result:
    print(result.pop(),end=' ')
```
