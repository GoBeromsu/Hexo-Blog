---
title: algorithm_boj2805
categories:
  - null
date: 2021-10-27 22:10:10
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

## 높이를 1부터 다 구함

```python
import sys

N,M = map(int,sys.stdin.readline().split())
nums = list(map(int, sys.stdin.readline().split()))

dic={}
idx = 1

while 1:
    sum=0
    for num in nums:
        if num-idx>0:
            sum+=num-idx
    if sum<M:
        print(idx-1)
        break
    idx+=1  
```

## 이분 탐색

```python
import sys

N,M = map(int,sys.stdin.readline().split())
nums = list(map(int, sys.stdin.readline().split()))

idx = 1

left,right = 1,max(nums)

while(left<=right):
    sum=0
    mid = (left+right)//2
    for num in nums:
        if num>mid:
            sum+=num-mid
        if sum>=M:
            break
    if sum>=M:
        left=mid+1
    else:
        right=mid-1
    
print(right)
```