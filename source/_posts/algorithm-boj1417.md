---
title: 백준 1417 국회의원 선거
categories: algorithm
date: 2022-07-27 13:07:35
tags:
---

## 풀이

```python
import sys
import heapq

num = int(sys.stdin.readline())
heap = []
ds = 0
for n in range(num):
    nm = int(sys.stdin.readline())
    if n==0:
        ds=nm
    else:
        heapq.heappush(heap, -nm)
count = 0
while heap:
    max = -heapq.heappop(heap)
    if ds>max:
        break
    ds+=1
    heapq.heappush(heap,-max+1)
    count+=1


print(count)
```

- 우선순위를 부여해서 값을 구하면 될거라 생각했다
  - 이런 정렬 자료구조에서 보통은 오름차순 정렬이 되서 값이 나오는데 이름 내림차순으로 바꿀 필요가 있었다
  - heapq를 사용했고, 값을 넣을 때 음수로 바꿔서 넣음으로써 내림차순을 구현했다

## 배열에 우선순위를 부여하자

### 우선순위 큐

```python
from queue import PriorityQue # Class Import
que = PriorityQueue()# 우선 순위 큐 생성
```

- 우선순위 큐는 iterable 하지 않기 때문에 인덱스로 접근이 불가능
  - print하면 출력이 아니라 object 주소가 나온다
- 기본적으로 오름차순 정렬이 되어 있다
  - 내림차순 하는 법을 찾고 있었는데 차라리 heapq를 사용하는게 더 편할거라 생각해서 바꿨다

### Heap

- 완전 이진 트리의 일종으로 우선순위 큐를 위하여 만들어진 자료구조이다.
- 힙은 일종의 반 정렬 상태를 유지한다
  - 큰 값이 상위 레벨에 있고 작은 값이 하위 레벨에 있지만 엄격하진 않다
- 구현하기가 쉽고, 배열을 이용하기 때문에 알고리즘 문제 풀 때 유용하다

## 회고

- 좀 더 파고들어서 공부할 필요가 있다.
- 그렇게 어려운 문제는 아니었는데 아이디어 떠올리는데서 조곰 헤맸다