--- 
emoji: π
categories: algorithm
title: λ°±μ€ 9375 ν¨μμ μ ν΄λΉ
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->

# λ°±μ€ 9375 ν¨μμ μ ν΄λΉ

## λ¬Έμ 

ν΄λΉμ΄λ ν¨μμ λ§€μ° λ―Όκ°ν΄μ νλ² μμλ μ·λ€μ μ‘°ν©μ μ λ λ€μ μμ§ μλλ€. μλ₯Ό λ€μ΄ μ€λ ν΄λΉμ΄κ° μκ²½, μ½νΈ, μμ, μ λ°μ μμλ€λ©΄, λ€μλ μ λ°μ§λ₯Ό μΆκ°λ‘ μκ±°λ μκ²½λμ  λ μ¦λ₯Ό μ°©μ©νκ±°λ ν΄μΌνλ€. ν΄λΉμ΄κ° κ°μ§ μμλ€μ΄ μ£Όμ΄μ‘μλ κ³Όμ° ν΄λΉμ΄λ μλͺΈμ΄ μλ μνλ‘ λ©°μΉ λμ λ°μ λμλ€λ μ μμκΉ?

### μλ ₯

μ²«μ§Έ μ€μ νμ€νΈ μΌμ΄μ€κ° μ£Όμ΄μ§λ€. νμ€νΈ μΌμ΄μ€λ μ΅λ 100μ΄λ€.

* κ° νμ€νΈ μΌμ΄μ€μ μ²«μ§Έ μ€μλ ν΄λΉμ΄κ° κ°μ§ μμμ μ n(0 β€ n β€ 30)μ΄ μ£Όμ΄μ§λ€.
* λ€μ nκ°μλ ν΄λΉμ΄κ° κ°μ§ μμμ μ΄λ¦κ³Ό μμμ μ’λ₯κ° κ³΅λ°±μΌλ‘ κ΅¬λΆλμ΄ μ£Όμ΄μ§λ€. κ°μ μ’λ₯μ μμμ νλλ§ μμ μ μλ€.
* λͺ¨λ  λ¬Έμμ΄μ 1μ΄μ 20μ΄νμ μνλ²³ μλ¬Έμλ‘ μ΄λ£¨μ΄μ ΈμμΌλ©° κ°μ μ΄λ¦μ κ°μ§ μμμ μ‘΄μ¬νμ§ μλλ€.

### μΆλ ₯

κ° νμ€νΈ μΌμ΄μ€μ λν΄ ν΄λΉμ΄κ° μλͺΈμ΄ μλ μνλ‘ μμμ μμ μ μλ κ²½μ°λ₯Ό μΆλ ₯νμμ€.

## νμ΄

```python
import sys

n = int(sys.stdin.readline())

for _ in range(n):
    number = int(sys.stdin.readline())
    if number==0:
        print(0)
        continue
    
    clothes=dict()
    for _ in range(number):
        clo_name,clo_type=map(str,sys.stdin.readline().split())
        if clo_type in clothes.keys():
            clothes[clo_type]+=1
        else:
            clothes[clo_type]=1

        cnt=1
        for key in clothes.keys():
            cnt*=clothes[key]+1
    print(cnt-1)
```

### μ²μ νμ΄ λ μλͺ»ν μ 

λμλλ¦¬λ‘ κ°λ€μ μ λ¦¬νκ³ , combinationμ μ¬μ©ν΄μ λ¬Έμ λ₯Ό νμλ€.
νμ§λ§ μκ° μ΄κ³Όλ₯Ό λ°μλ€. μκ°μ΄ ν¨μ¨μ μ΄μ§ μμλ€.

λλ¦ κ³μ°μ μ€μ¬λ³΄λ €κ³  λμλλ¦¬μ μ·μ κ°―μλ₯Ό λ£κ³ , μ·μ κ°―μλΌλ¦¬ μ‘°ν©μ κ΅¬νκ³ , μ‘°ν© μμ μ«μλ₯Ό κ³±ν μ΄ν©μ΄ ν΄μ§μ΄κ° μμ μ μλ μ·μ κ°μ§μμ΄κΈ° λλ¬Έμ΄λ€.

### λ λ²μ§Έ νμ΄

μ¬λ¬ ν΄μ€λ€μ λ³΄λ€λ³΄λ, [ν΄μ§μ΄κ° μμ μ μλ μ·μ μ‘°ν©(μλͺΈ ν¬ν¨) - 1(μλͺΈμΈ κ²½μ°)]λ‘ κ΅¬νλ©΄ μμ΄ μκ°λ³΄λ€ μμ²­ κ°λ¨ν΄μ§λ€.

λ μ€λ λ°°μ΄ μ μ μμΈ μ²λ¦¬μ΄λ€. νμ€νΈ μΌμ΄μ€κ° μ£Όμ΄μ§ λ ν΄μ§μ΄κ° μ·μ΄ μλ κ²½μ°κ° μλ€. μ΄ λ λ°λ‘ 0μΌλ‘ μμΈ μ²λ¦¬λ₯Ό ν΄μΌνλλ° μ²μ ν λλ μ κ²½μ°μ§ μμλ€.