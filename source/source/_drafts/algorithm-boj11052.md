---
title: 백준 11052 카드 구매하기 
categories:
  - algorithm
date: 2021-11-07 16:45:22
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 11052 카드 구매하기
## 문제

## 풀이
4 장을 구매해야하는데 각 각 1 5 6 7 이 주어졌을 때
카드 한 장 사는 경우

dp[1] = 1
dp[2] = 1+1 or 5 = 5
dp[3] = 1+1+1 or 1+5 or 6 = 6 
dp[4] = 1+1+1+1 or 1+1+5 or 5+5 or 1+6 or 7 = 10

dp[N] = dp[] + P[]