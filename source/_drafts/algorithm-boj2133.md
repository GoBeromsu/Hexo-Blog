---
title: 백준 2133 타일 채우기
categories:
  - algorithm
date: 2021-12-03 17:26:37
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 2133 타일 채우기

## 문제

## 풀이

## 코드

```python
import sys

n = int(sys.stdin.readline())
dp = [0] * 31
dp[2]=3
for i in range(4,31,2):
    dp[i] = dp[i-2]*3+ sum(dp[:i-3])*2 + 2

print(dp[n])
```