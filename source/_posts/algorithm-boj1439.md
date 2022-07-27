---
title: 백준 1439 뒤집기
categories: algorithm
date: 2022-07-27 13:42:55
tags:
---

## 풀이

```python
import sys

st = sys.stdin.readline().rstrip()
stl=[]
temp=''
flag=st[0]
for s in st:
    if flag!=s:
        stl.append(temp)
        temp=s
        flag=s
    else:
        temp+=s
stl.append(temp)

zcount=0
ocount = 0
for st in stl:
    if st[0]=='0':
        zcount+=1
    else:
        ocount+=1
print(min(zcount,ocount))
```

- 뒤집는 횟수는 결국은 1과 0 뭉텅이 중 뭐가 제일 많이 나왔느냐라 생각했다
- 처음엔 횟수로 나눴는데 생각을 잘못해서 오류가 떴었다. 그렇게 푸는게 시간이 덜 들어갈 듯하다

## 회고

- solved.ac 기준 silver 3이상으로 풀자
  - 일단은 조곰 생각하면 풀어버린다
  - 티어가 안올라가니까 추가적인 동기부여가 없는 듯
