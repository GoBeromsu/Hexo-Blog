---
emoji: ๐
categories: algorithm
title: ๋ฐฑ์ค 1389 ์ผ๋น ๋ฒ ์ด์ปจ์ 6๋จ๊ณ ๋ฒ์น
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
description:
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ๋ฐฑ์ค 1389 ์ผ๋น ๋ฒ ์ด์ปจ์ 6๋จ๊ณ ๋ฒ์น

## ๋ฌธ์ 

BOJ ์ ์ ์ ์์ ์น๊ตฌ ๊ด๊ณ๊ฐ ์๋ ฅ์ผ๋ก ์ฃผ์ด์ก์ ๋, ์ผ๋น ๋ฒ ์ด์ปจ์ ์๊ฐ ๊ฐ์ฅ ์์ ์ฌ๋์ ๊ตฌํ๋ ํ๋ก๊ทธ๋จ์ ์์ฑํ์์ค.

์ฒซ์งธ ์ค์ ์ ์ ์ ์ N (2 โค N โค 100)๊ณผ ์น๊ตฌ ๊ด๊ณ์ ์ M (1 โค M โค 5,000)์ด ์ฃผ์ด์ง๋ค. 
๋์งธ ์ค๋ถํฐ M๊ฐ์ ์ค์๋ ์น๊ตฌ ๊ด๊ณ๊ฐ ์ฃผ์ด์ง๋ค. ์น๊ตฌ ๊ด๊ณ๋ A์ B๋ก ์ด๋ฃจ์ด์ ธ ์์ผ๋ฉฐ, A์ B๊ฐ ์น๊ตฌ๋ผ๋ ๋ป์ด๋ค. 
A์ B๊ฐ ์น๊ตฌ์ด๋ฉด, B์ A๋ ์น๊ตฌ์ด๋ฉฐ, A์ B๊ฐ ๊ฐ์ ๊ฒฝ์ฐ๋ ์๋ค. 
์น๊ตฌ ๊ด๊ณ๋ ์ค๋ณต๋์ด ๋ค์ด์ฌ ์๋ ์์ผ๋ฉฐ, ์น๊ตฌ๊ฐ ํ ๋ช๋ ์๋ ์ฌ๋์ ์๋ค. 
๋ชจ๋  ์ฌ๋์ ์น๊ตฌ ๊ด๊ณ๋ก ์ฐ๊ฒฐ๋์ด์ ธ ์๋ค. 
์ฌ๋์ ๋ฒํธ๋ 1๋ถํฐ N๊น์ง์ด๋ฉฐ, ๋ ์ฌ๋์ด ๊ฐ์ ๋ฒํธ๋ฅผ ๊ฐ๋ ๊ฒฝ์ฐ๋ ์๋ค.

## ํ์ด

```python
import sys
from collections import deque
n,m= map(int, sys.stdin.readline().split())

persons = [[] for _ in range(n+1)]
kebin = [0 for _ in range(n+1)]
for i in range(1,m+1):
    p1,p2 = map(int,sys.stdin.readline().split())
    persons[p1].append(p2)
    persons[p2].append(p1)
    persons[p1].sort()
    persons[p2].sort()

def bfs(person):
    q = deque([person])
    check,count=[],[0]*(n+1)
    while q:
        x=q.popleft()
        for i in persons[x]:
            if i not in check:
                count[i]=count[x]+1
                check.append(i)
                q.append(i)
    kebin[person]=sum(count)
for i in range(1,n+1):
    bfs(i)


print(kebin.index(min(kebin[1:])))
```

* ๋ธ๋(์น๊ตฌ)๋ฅผ ๊ฑฐ์น  ๋๋ง๋ค ํด๋น ๋ธ๋์ count๋ฅผ ์ธ์ ์ ์ฅํ๊ณ , ๋ฆฌ์คํธ kebin์ ํฉ์ ์ ์ฅํ๋ค.