---
title: 백준 1343 폴리오미노
categories: algorithm
date: 2022-07-25 21:36:04
tags:
---
## 풀이

```python
import sys

st = sys.stdin.readline().rstrip()
stl = []

def solve(st):
    answer=''
    temp=''
    for s in st:
        if temp=='':
            temp+=s
        elif temp[0]==s:
            temp+=s
        else:
            stl.append(temp)
            temp=s
    stl.append(temp)
    if len(st)==0:
        return -1
    for st in stl:
        if st[0]=='X':
            if len(st)%2!=0:#짝수가 아닌 것은 만들 수 없으니까 제거 한다
                return -1
            x = len(st)//4
            y= len(st)-x*4
            answer+='A'*x*4
            answer+=y*'B'
        else:
            answer+=len(st)*'.'
    return answer

print(solve(st))
```

- 사전 순으로 나오라는 말은 그냥 A가 먼저 나오면 되니까 4로 나눠지는 몫으로 A를 입력 후 남는 값에 B를 넣었다
  - 당연히 홀수인 경우는 미리 예외 처리 했다

## 회고

- solve() 등을 만들어서 예외처리를 그냥 return -1하니까 문제 풀 때 편하다
- 구현력이 꽤나 떨어짐을 느낀다. 쉬운 문제부터 차근차근 해결해 나가자
  - 일단은 그리디 문제 풀면서 조곰씩 폼을 올릴 생각이다
