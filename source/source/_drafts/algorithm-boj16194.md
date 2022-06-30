---
title: 백준 16194 카드 구매하기 2
categories:
  - algorithm
date: 2021-11-08 15:34:46
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 161914 카드 구매하기 2
## 문제
### 입력
첫째 줄에 민규가 구매하려고 하는 카드의 개수 N이 주어진다. (1 ≤ N ≤ 1,000)

둘째 줄에는 Pi가 P1부터 PN까지 순서대로 주어진다. (1 ≤ Pi ≤ 10,000)

### 출력

첫째 줄에 민규가 카드 N개를 갖기 위해 지불해야 하는 금액의 최솟값을 출력한다.

## 풀이

## 답

```python
import sys

num = int(sys.stdin.readline())
P = [0]+list(map(int,sys.stdin.readline().split()))
dp = [False for i in range(num+1)]

# 카드 1개 1
# 카드 2개 1+1 5
# 카드 3개 1+1+1 1+5 6
# 카드 4개 1+1+1+! 1+6 1+1+5 7 5+5
for i in range(1,num+1):
    for j in range(i+1):
        if dp[i]==False:
            dp[i]=dp[i-j]+P[j]
        else:
            dp[i] = min(dp[i],dp[i-j]+P[j])

print(dp[num])
```