---
emoji: π
categories: algorithm
title: λ°±μ€ 17299 μ€λ±ν°μ
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->
# λ°±μ€ 17299 μ€λ±ν°μ
## λ¬Έμ 

ν¬κΈ°κ° NμΈ μμ΄ A = A1, A2, ..., ANμ΄ μλ€. μμ΄μ κ° μμ Aiμ λν΄μ μ€λ±ν°μ NGF(i)λ₯Ό κ΅¬νλ €κ³  νλ€.

Aiκ° μμ΄ Aμμ λ±μ₯ν νμλ₯Ό F(Ai)λΌκ³  νμ λ, Aiμ μ€λ±ν°μλ μ€λ₯Έμͺ½μ μμΌλ©΄μ μμ΄ Aμμ λ±μ₯ν νμκ° F(Ai)λ³΄λ€ ν° μ μ€μμ κ°μ₯ μΌμͺ½μ μλ μλ₯Ό μλ―Ένλ€. κ·Έλ¬ν μκ° μλ κ²½μ°μ μ€λ±ν°μλ -1μ΄λ€.

μλ₯Ό λ€μ΄, A = [1, 1, 2, 3, 4, 2, 1]μΈ κ²½μ° F(1) = 3, F(2) = 2, F(3) = 1, F(4) = 1μ΄λ€. A1μ μ€λ₯Έμͺ½μ μμΌλ©΄μ λ±μ₯ν νμκ° 3λ³΄λ€ ν° μλ μκΈ° λλ¬Έμ, NGF(1) = -1μ΄λ€. A3μ κ²½μ°μλ A7μ΄ μ€λ₯Έμͺ½μ μμΌλ©΄μ F(A3=2) < F(A7=1) μ΄κΈ° λλ¬Έμ, NGF(3) = 1μ΄λ€. NGF(4) = 2, NGF(5) = 2, NGF(6) = 1 μ΄λ€.

__μ€λ±ν°μ__ λ ν μΈλ±μ€μ μ€λ₯Έ νΈμ μλ μκΈ°λ³΄λ€ λ±μ₯ν νμκ° ν° μ μ€ κ°μ₯ μΌμͺ½μ μλ μμ΄λ€.

## νμ΄

λ―Έλ¦¬ resultλ₯Ό -1λ‘ μ μΈν΄λκ³ , λμλλ¦¬μ λΉλμλ₯Ό μ μ₯νλ€.

μ£Όμ΄μ§ κ°μ΄ μ μ₯λ listμΈ arrμ κ°μ΄ μ€νμ λ§μ§λ§ κ°μ λΉλμλ₯Ό λΉκ΅νλ€.

μ€νμ λ§μ§λ§ κ°μ λΉλμκ° arrμ κ°μ λΉλμ λ³΄λ€ μλ€λ©΄ arrμ κ°μ μ€νμ μ μ₯λ κ°μ μ€ν°μμ΄λ€.

### ν΅μ¬ μμ΄λμ΄

* μ€νμ μΈλ±μ€λ₯Ό μ μ₯νλ€

## CODE

```python
import sys

result = [-1 for i in range(int(sys.stdin.readline()))]
arr = list(map(int, sys.stdin.readline().split()))
dic={}
stack = []
for i in arr:
    if i in dic:
        dic[i]+=1
    else:
        dic[i]=1

for s in enumerate(arr):
    while stack and dic[arr[stack[-1]]]<dic[s[1]]:
        result[stack.pop()]=s[1]
    stack.append(s[0])

print(*result)
```