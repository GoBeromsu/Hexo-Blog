---
title: ๋ฐฑ์ค 1260 DFS์ BFS
emoji: ๐
categories: algorithm
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ๋ฐฑ์ค 1260 DFS์ BFS

## ๋ฌธ์ 

## ํ์ด

```PYTHON
import sys
from collections import deque

n,m,v =map(int,sys.stdin.readline().split())
nodes = [[] for _ in range(n+1)]
check = [False for _ in range(n+1)]

for i in range(m):
    node1,node2 = map(int,sys.stdin.readline().split())
    nodes[node1].append(node2)
    nodes[node2].append(node1)
for i in range(1,n+1):
    nodes[i].sort()

def bfs(v):
    check[v]=True
    q = deque([v])
    while q:
        node=q.popleft()
        print(node,end=' ')
        for i in nodes[node]:
            if check[i]==False:
                q.append(i)
                check[i]=True
            
def dfs(v):
    print(v,end=' ')
    check[v]=True
    for i in nodes[v]:
        if not check[i]:
            dfs(i)

dfs(v)
check=[False]*(n+1)
print()
bfs(v)

```