---
emoji: ๐
categories: algorithm
title: ๋ฐฑ์ค 1303 ์ ์ - ์ ํฌ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ๋ฐฑ์ค 1303 ์ ์ - ์ ํฌ

## ๋ฌธ์ 

## ํ์ด

```PYTHON
import sys
from collections import deque


N,M = map(int,sys.stdin.readline().split())
mp = []
for i in range(M):
    mp.append(list(sys.stdin.readline().rstrip()))

visited=[[False] * N for _ in range(M)]
W, B = [], []
dx, dy = [0, 0, 1, -1], [1, -1, 0, 0]

def bfs(x, y):
    q = deque([(x, y)])
    color = mp[x][y]
    count=0
    while q:
        x, y = q.popleft()
        for i in range(4):
            nx,ny=x+dx[i],y+dy[i]
            if nx<0 or ny<0 or nx>=M or ny>=N:
                continue    
            if color==mp[nx][ny] and visited[nx][ny]==False:
                visited[nx][ny]=True
                q.append((nx,ny))
                count+=1
    if count==0:
        count=1
    if color=='W':
        W.append(count)
    else:
        B.append(count)
    
for i in range(M):
    for j in range(N):
        if not visited[i][j]:
            bfs(i, j)

answer=[]
for i in (W,B):
    ans=0
    for j in i:
        ans+=j**2
    answer.append(ans)
print(*answer)
```

* ์กธ๋ฆฐ ๊ด๊ณ๋ก ์์ด ์ข ๋๋ฝ๋ค
* ๊ณ์ ์ ํ๋ ธ๋ ํ๋๋ฐ visited๋ฅผ ๋ง๋ค ๋ ๊ฐ๋ก์ ์ธ๋ก๋ฅผ ํท๊ฐ๋ ธ๋ค.

๋ค์์ ์ข ๋ ์ ๊ฒฝ ์จ์ผ ํ  ๊ฒ

1. ๋ฐ๋ก ๋ฆฌ์คํธ๋ฅผ ์ ์ธํด์ ๊ฐ ๊ณณ์ ์ฒดํฌํ๋ผ

* ๊ดํ ๋ณต์กํด์ ธ์ ํท๊ฐ๋ฆฌ๋๋, ๊ทธ๋ฅ ์ฒดํฌํ์

2. ๋๋ฒ๊นํ  ๋ ๊ฐ์ด ์ ๋๋ก ์๋ ฅ ๋๋์ง ํ์ธํ์

์ด๋ฐ ์ ํ์ bfs ๋ฌธ์ ๋ ๊ฐ ๊ณณ์ ์ฒดํฌํด์ ์นด์ดํธ๋ง ํ๋ฉด ๋๊ธฐ ๋๋ฌธ์ ์์ฃผ ๋ฌธ์ ๋ฅผ ํ์ด์ ์ต์ํด์ง๋๋ก ํ์
