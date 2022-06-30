---
title: 백준 10972 다음 순열
categories:
  - algorithm
date: 2022-01-06 14:43:03
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 10972 다음 순열

## 문제
1부터 N까지의 수로 이루어진 순열이 있다. 이때, 사전순으로 다음에 오는 순열을 구하는 프로그램을 작성하시오.

사전 순으로 가장 앞서는 순열은 오름차순으로 이루어진 순열이고, 가장 마지막에 오는 순열은 내림차순으로 이루어진 순열이다.

## 문제 풀이

next_permutation 알고리즘을 알면 쉽게 풀 수 있다.

순열 1 3 4 2 가 있다 가정하자

1. 뒤에서부터 뒷 숫자가 앞 숫자보다 큰 경우를 찾는다.
    * (1,3) (3,4) (4,2) 이면 (3,4)를 찾는다.
    * 3과 4의 인덱스를 X,Y라 하자
2. 다시 뒤에서부터 3(인덱스 X의 값)보다 큰 값이 있으면 X와 스왑한다
3. Y부터 순열의 끝까지 오름차순 정렬하고 이어 붙힌다

## Code

```python
import sys

num = int(sys.stdin.readline())
numbers = list(map(int,sys.stdin.readline().split()))
x,y = 0,0
for i in range(num-1,0,-1):
    if numbers[i]>numbers[i-1]:
        x,y= i-1,i
        break
for i in range(num-1,0,-1):
    if numbers[x]<numbers[i]:
        numbers[x],numbers[i] = numbers[i],numbers[x]
        break
numbers = numbers[:y]+sorted(numbers[y:])
print(*numbers)
```