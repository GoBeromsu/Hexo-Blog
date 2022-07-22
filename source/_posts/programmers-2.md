---
title: 로또의 최고 순위와 최저 순위 
date: 2022-07-22 10:57:44
tags: Programmers
---

## 풀이

- 순서에 상관 없이 번호만 일치하면 된다
- 바꿀 수 있는 번호는 0이다

로또 당첨 번호 받아서 순차적으로 안에 값이 있는지 확인해서, 없는 것만 찾으면 될 듯하다
최소 당첨 번호는 일치하는 숫자의 갯수이다. 최대 당첨 번호는 전체 자릿 수에서 일치하지 않는 번호만 빼면 된다

```python
def solution(lottos, win_nums):
    answer = []
    correct,zero = 0,0
    for l in lottos:
        if l==0:
            zero+=1
        elif l in win_nums:
            correct+=1
    
    mini,maxi=0,0
    maxi = correct+zero
    mini = correct
    
    if maxi==0 or maxi ==1:
        answer.append(6)    
    else:       
        answer.append(7-maxi)
    if mini==0 or mini==1:
        answer.append(6)
    else:
        answer.append(7-mini)
    
    return answer
```

## 회고

- 로직은 매우 쉬운데, 내 생각이 좀 분산된 듯하다
- 예외처리 잘하자 그냥 조건만 잘 읽으면 예외처리는 껌이야