---
emoji: π
categories: algorithm
title: algorithm_boj2178
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->

# λ°±μ€ 2178 λ―Έλ‘ νμ

## λ¬Έμ 

## νμ΄

* μ²« λ²μ§Έ νμ΄

```python
import sys
sys.setrecursionlimit(15000)

N,M = map(int, sys.stdin.readline().split())
MAX =sys.maxsize
mp = [[MAX]*(M+1) for _ in range(N+1)]

for n in range(1,N+1):
    cnt=1
    for m in list(map(int,sys.stdin.readline().rstrip())):
        mp[n][cnt]=m
        cnt+=1
ans=[]
def solve(x,y,count):
    if x==N and y==M:
        ans.append(count)
        return
    if x==0 or y==0 or x==N+1 or y==M+1:
        return
    if mp[x][y]==0 or mp[x][y]==2:
        return
    elif mp[x][y]==1:
        mp[x][y]=2
        solve(x, y+1, count+1)
        solve(x+1, y, count+1)
        solve(x, y-1, count+1)
        solve(x-1, y, count+1)
solve(1, 1,1)
print(min(ans))
```

μμ μ½λλ νλ¦° μ½λμ΄λ€. μ¬κ· ν¨μλ₯Ό μ΄μ©ν΄μ νμν΄μ λͺ©μ μ§μ λλ¬νμ λμ μΉ΄μ΄νΈλ₯Ό μΆκ°νλλ‘ νλ€.

μλ μ½λλ bfsλ‘ λ€μ νμ΄ μ μΆν μ λ΅ μ½λμ΄λ€.

```python
import sys
from collections import deque

N,M = map(int,sys.stdin.readline().split())
mp=[]

for _ in range(N):
    mp.append(list(map(int,sys.stdin.readline().rstrip())))

dx=[-1,0,1,0]
dy=[0,1,0,-1]

visited = [[0]*M for _ in range(N)]

q=deque([(0,0)])
while q:
    x,y =q.popleft()
    if x==N-1 and y==M-1:
        print(visited[x][y]+1)
    for i in range(4):
        nx,ny=x+dx[i],y+dy[i]

        if 0<= nx <N and 0<= ny<M:
            if visited[nx][ny] ==0 and mp[nx][ny]==1:
                visited[nx][ny] = visited[x][y]+1
                q.append((nx,ny))
```

* λ­κ° λ¬Έμ μΌκΉ? μ²μ μ½λλ λλ¦ bfs λλμΈλ° μΆμ΄ μ bfsλ‘ μ°Ύμ κ²½λ‘κ° μ΅λ¨ κ²½λ‘μΈμ§ μ°Ύμλ³΄μλ€

bfsλ λμ΄ μ°μ  νμμ΄λ€. μ¦ λ£¨νΈ λΈλλΆν° μμν΄μ κ±°λ¦¬κ° 1,2,3,.... μΈ μμ λΈλλ€μ μ°¨λ‘λλ‘ λ°©λ¬Ένλ€.
μ¦ μ΄λ κ² μννλ©΄ μμ λΈλλ€μ λ£¨νΈ λΈλλ‘λΆν° κ±°λ¦¬κ° 1,2,3 μ΄λ―λ‘ μ΅μ κ±°λ¦¬λ₯Ό λ³΄μ₯λ°κ² λλ€.