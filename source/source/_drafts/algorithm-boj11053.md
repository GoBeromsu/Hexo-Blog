---
title: 백준 11053 가장 긴 증가하는 부분 수열
categories:
  - algorithm
date: 2021-11-09 17:26:36
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->
# 백준 11053 가장 긴 증가하는 부분 수열
## 문제
수열 A가 주어졌을 때, 가장 긴 증가하는 부분 수열을 구하는 프로그램을 작성하시오.

예를 들어, 수열 A = {10, 20, 10, 30, 20, 50} 인 경우에 가장 긴 증가하는 부분 수열은 A = {10, 20, 10, 30, 20, 50} 이고, 길이는 4이다.
### 입력
첫째 줄에 수열 A의 크기 N (1 ≤ N ≤ 1,000)이 주어진다.

둘째 줄에는 수열 A를 이루고 있는 Ai가 주어진다. (1 ≤ Ai ≤ 1,000)

## 풀이
### 앞에서부터 자기보다 큰 수들로 이으면 되지 않을까? - 실패
```python
import sys
num = int(sys.stdin.readline())
numbers = list(map(int, sys.stdin.readline().split()))
dp = [[] for i in range(num)]

for i in range(num):
    dp[i].append(numbers[i])
    for j in range(i+1,num):
        if dp[i][-1]<numbers[j]:
            dp[i].append(numbers[j])

result = len(dp.pop())
while dp:
    temp = len(dp.pop())
    if result<temp:
        result = temp
print(result)

6 : 1 5 6 2 3 4 : 4
1:1 5 :2 6:3 2:2 3:3 4:4

```


## 코드
