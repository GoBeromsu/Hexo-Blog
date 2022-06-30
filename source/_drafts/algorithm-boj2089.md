---
title: 백준 2089 -2 진수
categories:
  - algorithm
date: 2021-11-04 14:16:16
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 2089 -2 진수
## 문제

## 풀이

## 코드

```python
import sys

num =int(sys.stdin.readline())

if num ==0:
    print(0)

result =[]
while num:
    if num %2==1:
        result.append(1)
        num = num//-2+1
    else:
        result.append(0)
        num = num//-2

while result:
    print(result.pop(),end='')
```