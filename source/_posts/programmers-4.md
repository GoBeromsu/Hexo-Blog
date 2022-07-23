---
title: 더 맵게
categories: algorithm
date: 2022-07-23 14:28:09
tags: programmer
---

## 풀이

```python
def solution(scoville, K):
    answer = 0
    
    while True:
        scoville.sort(reverse=True)
        if len(scoville)==1 and scoville[0]<K:
            return -1
        elif scoville[-1] >=K:
            break
        n1 = scoville.pop()
        n2 = scoville.pop()
        scoville.append(n1+2*n2)
        answer+=1
    
    return answer
```

- 보자마자 떠오른 아이디어는 반복문 안에서 스택 사용해서 계속 정렬하면서 값을 구하는 것이었다
- 답은 맞는데 정렬하는 부분에서 시간 초과가 당연히 발생한다

```python
import heapq

def solution(scoville, K):
    answer = 0

    scoville.sort()

    while True:
        if len(scoville)==1 and scoville[0]<K:
            return -1
        if scoville[0] >=K:
            break
        n1 = heapq.heappop(scoville)
        n2 = heapq.heappop(scoville)
        heapq.heappush(scoville,n1+2*n2)
        answer+=1
    return answer
```

- 파이썬의 자료구조 heapq는 트리 구조로 데이터가 저장 되어 자동으로 입력을 할 때 정렬이 되는 특징이 있다
  - 이를 이용하여 문제 해결!

## 회고

- 자연스럽게 문제를 풀 때 자료구조를 먼저 찾고 적용한 흐름은 잘했다
- 아쉬운 점이라면, 자동 완성 등 없이 문제를 푸니까 불편함이 확연하다. 좀 고집이나 싶기도 하다
- 파이썬이 편해서 파이썬으로 공부하긴 하는데 다른 언어로 공부해야하나 싶다.
  - 물론 반대편에서는 로직만 같다면 구현할 수 있는거 아니냐란 생각도 들어 일단 꾸준히 함에 집중하자