---
title: 백준 15990 1,2,3, 더하기 5
categories:
  - algorithm
date: 2021-11-08 17:18:15
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->
# 백준 15990 1,2,3, 더하기 5

## 문제

정수 4를 1, 2, 3의 합으로 나타내는 방법은 총 3가지가 있다. 합을 나타낼 때는 수를 1개 이상 사용해야 한다. 단, 같은 수를 두 번 이상 연속해서 사용하면 안 된다.

1+2+1
1+3
3+1
정수 n이 주어졌을 때, n을 1, 2, 3의 합으로 나타내는 방법의 수를 구하는 프로그램을 작성하시오.

## 예제 입력

3
4 3
7 9
10 27

## 풀이

### 점화식을 잘못 구함 - 실패

```python
import sys

# 3 2 : 1+2 (2+1) : 0+1*2
# 4 3 : 1+3 (3+1) 1+2+1 : 1+1*2
# 5 4 : 2+(1+2) 2+3 (3+2) 1+(3+1) : 1+1+1*2 
# 6 6 : 1+2+1+2 2+1+2+1 1+2+3 1+3+2 2+1+3 3+2+1 : 1+(2+3) 1+(3+2) 1+(3+1) 1+(2+1+2)/ 2+(1+3) 2+(1+3) 2+(1+2+1) 
# 7 9 : 1+2+1+2+1 1+2+1+3 1+2+3+1 1+3+1+2 1+3+2+1

num = int(sys.stdin.readline())
numbers = [int(sys.stdin.readline()) for i in range(num)]
sum = [0,1,2,2] + [0]*(max(numbers)-3)

def getSum(n):
    if sum[n]==0:
        sum[n] = getSum(n-2) + getSum(n-1) -1
        return sum[n]
    else:
        return sum[n]

for n in numbers:
    print(getSum(n))
print(sum)
```

## 코드

```python
import sys

num = int(sys.stdin.readline())
numbers = [int(sys.stdin.readline()) for i in range(num)]
dp = [[0 for i in range(3)] for i in range(max(numbers)+1)]

dp[1][0]=1
dp[2][1]=1
dp[3][0],dp[3][1],dp[3][2] = 1,1,1

for n in range(4,max(numbers)+1):
    dp[n][0] = dp[n-1][1]%1000000009+dp[n-1][2]%1000000009
    dp[n][1] = dp[n-2][0]%1000000009+dp[n-2][2]%1000000009
    dp[n][2] = dp[n-3][0]%1000000009+dp[n-3][1]%1000000009

for n in numbers:
    print(sum(dp[n])%1000000009)
```
