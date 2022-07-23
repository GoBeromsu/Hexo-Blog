---
title: 폰켓몬
categories: algorithm
date: 2022-07-23 14:14:59
tags: programmers
---

## 풀이

```python
def solution(nums):
    answer=0
    s = list(set(nums))
    size = len(nums)/2 if len(nums)%2==0 else int(len(nums)/2)+1
    if size>len(s):
        answer = len(s)
    else:
        answer = size
    return answer
```

## 회고

- 너무 쉽게 풀려서 뭐지 싶었는데, 오르는 점수 보니까 쉬운 문제였다
- 별다른 로직이 없기도 했음
