---
emoji: ๐
categories: algorithm
title: ๋ฐฑ์ค 1541 ์์ด๋ฒ๋ฆฐ ๊ดํธ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
description:
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ๋ฐฑ์ค 1541 ์์ด๋ฒ๋ฆฐ ๊ดํธ

## ๋ฌธ์ 

์ธ์ค์ด๋ ์์์ +, -, ๊ทธ๋ฆฌ๊ณ  ๊ดํธ๋ฅผ ๊ฐ์ง๊ณ  ์์ ๋ง๋ค์๋ค. ๊ทธ๋ฆฌ๊ณ  ๋์ ์ธ์ค์ด๋ ๊ดํธ๋ฅผ ๋ชจ๋ ์ง์ ๋ค.

๊ทธ๋ฆฌ๊ณ  ๋์ ์ธ์ค์ด๋ ๊ดํธ๋ฅผ ์ ์ ํ ์ณ์ ์ด ์์ ๊ฐ์ ์ต์๋ก ๋ง๋ค๋ ค๊ณ  ํ๋ค.

๊ดํธ๋ฅผ ์ ์ ํ ์ณ์ ์ด ์์ ๊ฐ์ ์ต์๋ก ๋ง๋๋ ํ๋ก๊ทธ๋จ์ ์์ฑํ์์ค.

## ํ์ด

```python
import sys
from collections import deque

sen =sys.stdin.readline().rstrip()
sentence = deque([i for i in sen])
numbers,op=[],[]

temp=''
while sentence:
    x = sentence.popleft()
    if 48<=ord(x)<=57:
        temp+=x
    else:
        numbers.append(int(temp))
        temp=''
        op.append(x)
numbers.append(int(temp))

op=deque(op)
flag=True
res,idx=0,9999

for i in range(len(op)):
    if op[i]=='-':
        idx=i
        break

if idx==9999:
    print(sum(numbers))
else:
    print(sum(numbers[0:idx+1])-sum(numbers[idx+1:len(numbers)]))
```

* ๋ฌธ์ ๋ฅผ ๋๋ฐ๋ก ์ฝ์ ๊ฒ
* ์๊ฐ์ ์ข ๋ ๊น์ด ํ  ๊ฒ

๊ดํธ๋ฅผ ์ณ์ ์ด ์์ ๊ฐ์ ์ต์๋ก ๋ง๋ค๋ ค๋ฉด, -๊ฐ ๋ฑ์ฅํ ํ ๋ชจ๋  ๊ฐ์ด ์์๊ฐ ๋๋ฉด ๋๋ค.