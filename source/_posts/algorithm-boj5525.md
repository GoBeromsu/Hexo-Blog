---
emoji: ๐
categories: algorithm
title: ๋ฐฑ์ค 5525 IOIOI
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
description:
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ๋ฐฑ์ค 5525 IOIOI

## ๋ฌธ์ 

N+1๊ฐ์ I์ N๊ฐ์ O๋ก ์ด๋ฃจ์ด์ ธ ์์ผ๋ฉด, I์ O์ด ๊ต๋๋ก ๋์ค๋ ๋ฌธ์์ด์ PN์ด๋ผ๊ณ  ํ๋ค.

P1 IOI
P2 IOIOI
P3 IOIOIOI
PN IOIOI...OI (O๊ฐ N๊ฐ)
I์ O๋ก๋ง ์ด๋ฃจ์ด์ง ๋ฌธ์์ด S์ ์ ์ N์ด ์ฃผ์ด์ก์ ๋, S์์ PN์ด ๋ช ๊ตฐ๋ฐ ํฌํจ๋์ด ์๋์ง ๊ตฌํ๋ ํ๋ก๊ทธ๋จ์ ์์ฑํ์์ค.

## ํ์ด

* ์๋ ์ฝ๋๋ 50์  ์ง๋ฆฌ ์ฝ๋์ด๋ค. ์๋ง ์๊ฐ ๋ณต์ก๋ ๋๋ฌธ์ธ๋ฏํ๋ค

```PYTHON
import sys
from collections import deque

n = int(sys.stdin.readline())
m = int(sys.stdin.readline())
s = sys.stdin.readline().rstrip()
ns = "IOI"
for i in range(1,n):
    ns+='OI'
nsLen=len(ns)
ans,cnt=0,0

while 1:
    if ns==str(s[cnt:cnt+nsLen]):
        ans+=1
    cnt+=1
    if nsLen==len(s)-cnt:
        break

print(ans)
```

* ์๋ ์ฝ๋๋ 100์ ์ด๋ค. 

```python
import sys
from collections import deque

n = int(sys.stdin.readline())
m = int(sys.stdin.readline())
s = sys.stdin.readline().rstrip()

answer,i,count=0,0,0

while i<m-1:
    if s[i:i+3]=='IOI':
        i+=2
        count+=1
        if count ==n:
            answer+=1
            count -=1
    else:
        i+=1
        count=0
print(answer)
```

* IOI๊ฐ ๋ฐ๊ฒฌ๋๋ฉด index๋ฅผ 2๊ฐ ์ด๋์ํค๊ณ  ์๋ ๊ฒฝ์ฐ์๋ index๋ฅผ 1๊ฐ ์ด๋ ์ํค๋ฉด์ ๊ฒ์ฌํ๋ค.
  * IOI๋ฅผ ์ฐพ์ ๋๋ง๋ค ์นด์ดํธ๋ฅผ ์ฌ๋ฆฐ๋ค. ์ด ์นด์ดํธ๊ฐ n๊ฐ ๋์ผํ๋ค๋ฉด ์ฃผ์ด์ง P๋ฅผ ์ฐพ์ ๊ฒ์ด๋ answer๋ฅผ 1 ์ฌ๋ฆฐ๋ค.
