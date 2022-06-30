---
title: 백준 1759 암호 만들기
categories:
  - algorithm
date: 2022-01-09 19:17:02
tags:
cover:
description:
---
<!-- 
튜토리얼, 하우 투 가이드, 설명 ,레퍼런스 
https://documentation.divio.com/tutorials/
-->

# 백준 1759 암호 만들기
## 문제

## 풀이

## 코드
```python
import sys

# 알파벳 오름차 순
# 최소 한 개의 모음과 두 개의 자음으로 이루어져야함
# 암호는 L 자리, 주어진 알파벳은 C

L,C = map(int,sys.stdin.readline().split())
alp = sorted(sys.stdin.readline().split())

vowel =set(['a','e','i','o','u'])
con= set([x for x in alp if x not in vowel])

def solve(cur,syntax):
    result=[]
    if len(syntax)==L:
        if len(set(syntax)& vowel)>0 and len(set(syntax)& con)>1:
            return [''.join(syntax)]
    else:
        for i in range(cur,C):
            result+=solve(i+1, syntax+[alp[i]])
    return result

for p in solve(0, []):
    print(p)
```