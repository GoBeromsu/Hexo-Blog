---
emoji: π
categories: algorithm
title: λ°±μ€ 1931 νμμ€ λ°°μ 
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->
# λ°±μ€ 1931 νμμ€ λ°°μ 

## λ¬Έμ 

ν κ°μ νμμ€μ΄ μλλ° μ΄λ₯Ό μ¬μ©νκ³ μ νλ Nκ°μ νμμ λνμ¬ νμμ€ μ¬μ©νλ₯Ό λ§λ€λ €κ³  νλ€. κ° νμ Iμ λν΄ μμμκ°κ³Ό λλλ μκ°μ΄ μ£Όμ΄μ Έ μκ³ , κ° νμκ° κ²ΉμΉμ§ μκ² νλ©΄μ νμμ€μ μ¬μ©ν  μ μλ νμμ μ΅λ κ°μλ₯Ό μ°Ύμλ³΄μ. λ¨, νμλ νλ² μμνλ©΄ μ€κ°μ μ€λ¨λ  μ μμΌλ©° ν νμκ° λλλ κ²κ³Ό λμμ λ€μ νμκ° μμλ  μ μλ€. νμμ μμμκ°κ³Ό λλλ μκ°μ΄ κ°μ μλ μλ€. μ΄ κ²½μ°μλ μμνμλ§μ λλλ κ²μΌλ‘ μκ°νλ©΄ λλ€.

## νμ΄

μ²μ νμ΄λ νμμ€ λ°°μ  ν κ³³μ μ²΄ν¬ν΄μ, κ° κ³³μ μ κ°κ³ , λ°λ‘ μ΄μ΄μ§λ νμ μκ°μ μ΄μ΄κ° λλ§λ€ μΉ΄μ΄νΈνλ λ°©μμΌλ‘ νμλ€.
νμ§λ§ μκ° μ΄κ³Ό

λ¬Έμ λ₯Ό μλͺ» μ΄ν΄νμλ€. κΌ­ μ΄μ΄μ§ νμλ μλ€.

```python
import sys
time = int(sys.stdin.readline())
conference = [list(map(int,sys.stdin.readline().split())) for _ in range(time)]

count=0
def conf(start,end,cnt,check):
    global count
    for i in range(time):
        if check[i]:
            if i==time-1:
                count=max(count,cnt)
                break
            else:
                continue
        elif conference[i][0]==end+1:
            check[i]=True
            conf(conference[i][0], conference[i][1], cnt+1,check)
            check[i]=False

for i in range(time):
    check=[False]*time
    check[i]=True
    conf(conference[i][0], conference[i][1], 1,check)
print(count)
```

λΉ¨λ¦¬ λλλ κ² μ€ λΉ¨λ¦¬ μμνλ μμλ‘ λΉ λ₯΄κ² μ§μ΄ λ£μΌλ©΄ λ λΉ λ₯΄κ² λ΅μ κ΅¬ν΄λΌ μ μλ€.

```python
import sys

time = int(sys.stdin.readline())
conference = [list(map(int,sys.stdin.readline().split())) for _ in range(time)]

conference = sorted(conference,key=lambda x:[x[1],x[0]])

mx=0
start=0

for c in conference:
    if c[0] >= start:
        start= c[1]
        mx+=1
print(mx)
```