---
emoji: π
categories: algorithm
title: λ°±μ€ 4673 - μν λλ²
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->

# λ°±μ€ 4673 - μν λλ²

## λ¬Έμ 

10000λ³΄λ€ μκ±°λ κ°μ μν λλ²λ₯Ό ν μ€μ νλμ© μΆλ ₯νλΌ

### μν λλ²λ

μμ μ μ nμ λν΄μ d(n)μ nκ³Ό nμ κ° μλ¦¬μλ₯Ό λνλ ν¨μλΌκ³  μ μνμ. μλ₯Ό λ€μ΄, d(75) = 75+7+5 = 87μ΄λ€.
μ΄ λ nμ d(n)μ μμ±μλΌνλ€. μ¦ 75λ 87μ΄λ€.

μν λλ²λ μμ±μκ° μλ μμ΄λ€.

## λ¬Έμ  νμ΄

### μν λλ²λ₯Ό μ΄λ»κ² μ°Ύμ κ²μΈκ°?

μν λλ²λ μ μ²΄ μ μμμ μμ±μκ° μλ μ«μλ€μ μ°¨μ§ν©μ΄λ€.
μν λλ²λ₯Ό μ§μ  κ΅¬νκΈ° λ³΄λ¨ μμ±μκ° μλ μ«μλ€μ κ΅¬ν΄μ μ κ±°νλκ² λ λΉ λ₯Όκ±°λΌ μκ°νλ€.

### νμ΄ μμ

1. 0μΌλ‘ μ΄κΈ°νλ index 10000κ° λ°°μ΄ arrμ μμ±
2. μλ ₯ κ° nμ λ°λΌ μμ±μλ₯Ό λ°ννλ ν¨μ checkD μ μΈ
3. μΈλ±μ€ 1~10000μ checkD()μ λ£μ΄ arrμ μμ±μλ₯Ό μ²΄ν¬νλ€
4. arr λ΄μ μ²΄ν¬λμ§ μμ μΈλ±μ€(μν λλ²)λ₯Ό μΆλ ₯νλ€

### Code

```python
arr =[0 for i in range(10000)]
count=1

def checkD(n:int):z
    sum=n
    divValue=0
    while True:
        dLength=len(str(n))
        if(dLength==1):
            sum+=n
            break
        else:
            number= (10**(dLength-1))
            divValue=int(n/number)
            sum+=divValue
            n=n%(divValue*number)
    return sum    

for i in range(1,len(arr)+1):
    target=checkD(i)
    if (target>=10000):
        continue
    else:
        arr[target] = 1


for i in range(1,len(arr)):
    if (arr[i]!=1):
        print(i)

```
