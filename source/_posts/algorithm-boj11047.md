---
title: λ°±μ€ 11047 λμ  0
categories: algorithm
emoji: π
author: λ²μD
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->

# λμ  0

## λ¬Έμ 
μ€κ·κ° κ°μ§κ³  μλ λμ μ μ΄ Nμ’λ₯μ΄κ³ , κ°κ°μ λμ μ λ§€μ° λ§μ΄ κ°μ§κ³  μλ€.

λμ μ μ μ ν μ¬μ©ν΄μ κ·Έ κ°μΉμ ν©μ Kλ‘ λ§λ€λ €κ³  νλ€. μ΄λ νμν λμ  κ°μμ μ΅μκ°μ κ΅¬νλ νλ‘κ·Έλ¨μ μμ±νμμ€.


## νμ΄

```python
import sys

n,k = map(int,sys.stdin.readline().split())
coins=[int(sys.stdin.readline()) for i in range(n)]
cnt=0


for i in range(n-1,-1,-1):
    if k==0:
        break
    if coins[i]>k:
        continue
    cnt+=k//coins[i]
    k%=coins[i]
print(cnt)
```