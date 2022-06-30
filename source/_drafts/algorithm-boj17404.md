---
title: 백준 17404 RGB 거리 2
categories:
  - algorithm
date: 2021-12-11 11:02:36
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->
# 백준 17404 RGB 거리 2
## 문제 
RGB거리에는 집이 N개 있다. 거리는 선분으로 나타낼 수 있고, 1번 집부터 N번 집이 순서대로 있다.

집은 빨강, 초록, 파랑 중 하나의 색으로 칠해야 한다. 각각의 집을 빨강, 초록, 파랑으로 칠하는 비용이 주어졌을 때, 아래 규칙을 만족하면서 모든 집을 칠하는 비용의 최솟값을 구해보자.

1번 집의 색은 2번, N번 집의 색과 같지 않아야 한다.
N번 집의 색은 N-1번, 1번 집의 색과 같지 않아야 한다.
i(2 ≤ i ≤ N-1)번 집의 색은 i-1, i+1번 집의 색과 같지 않아야 한다.
## 풀이

## 코드
// 수정 필요
```python
import sys
input = sys.stdin.readline

n = int(input())
colors = [list(map(int,input().split())) for _ in range(n)]
result, inf = 1e9, 1e9

for color in range(3):
    dp = [[0 for _ in range(3)] for _ in range(n)]
    for i in range(3):
        if i == color:
            dp[0][i] = colors[0][i]
        else:
            dp[0][i] = inf
    for i in range(1, n):
        dp[i][0] = colors[i][0] + min(dp[i-1][1],dp[i-1][2])
        dp[i][1] = colors[i][1] + min(dp[i-1][0],dp[i-1][2])
        dp[i][2] = colors[i][2] + min(dp[i-1][0],dp[i-1][1])

    for i in range(3):
        if i != color:
            result = min(result, dp[-1][i])
print(result)
```