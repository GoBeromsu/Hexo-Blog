---
title: 백준 11055 가장 큰 증가 부분 수열
categories:
  - algorithm
date: 2021-11-16 15:43:32
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->
# 백준 11055 가장 큰 증가 부분 수열
## 문제
수열 A가 주어졌을 때, 그 수열의 증가 부분 수열 중에서 합이 가장 큰 것을 구하는 프로그램을 작성하시오.

예를 들어, 수열 A = {1, 100, 2, 50, 60, 3, 5, 6, 7, 8} 인 경우에 합이 가장 큰 증가 부분 수열은 A = {1, 100, 2, 50, 60, 3, 5, 6, 7, 8} 이고, 합은 113이다.
## 풀이
## 코드
```python
import sys

num = int(sys.stdin.readline())
numbers = list(map(int,sys.stdin.readline().split()))

dp = [x for x in numbers]
for n in range(num):
    for j in range(n):
        if numbers[n]>numbers[j]:
            dp[n]=max(dp[j]+numbers[n],dp[n])
print(max(dp))
```