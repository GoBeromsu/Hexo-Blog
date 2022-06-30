---
title: 백준 2156 포도주 시식
categories:
  - algorithm
date: 2021-11-15 16:38:01
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 2156 포도주 시식
## 문제
효주가 마실 수 있는 포도주의 최댓 값을 구하는 문제이다

1. 포도주 잔을 선택하면 그 잔에 들어있는 포도주는 모두 마셔야하고, 마신 후에는 원래 위치에 둬야한다
2. 연속으로 놓여있는 3잔을 모두 마실 수 없다.

## 풀이

## Code
```python
import sys

num = int(sys.stdin.readline())
numbers = [0]*10003
for i in range(1,num+1):
    numbers[i]=int(sys.stdin.readline())
dp = [0]*10003
dp[1]=numbers[1]
dp[2]=numbers[1]+numbers[2]

for i in range(3,num+1):
    dp[i]=max(dp[i - 1], dp[i - 3] + numbers[i - 1] + numbers[i], dp[i - 2] + numbers[i])
print(dp[num])

```