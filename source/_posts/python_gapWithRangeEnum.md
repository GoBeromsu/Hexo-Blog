---
emoji: π
categories: language
title: range() μ enumerate() μ°¨μ΄ 
author: λ²μ
date: '2022-03-10 18:00:00'
tags: λΈλ‘κ·Έ
description:
---
<!-- 
νν λ¦¬μΌ, νμ° ν¬ κ°μ΄λ, μ€λͺ ,λ νΌλ°μ€ 
https://documentation.divio.com/tutorials/
-->
## μμ

νμ΄μ¬μμ forλ¬Έμ for [λ³μ] in [list, tuple dic λ± κ°μ²΄] ννλ‘ μ¬μ©λλ€
PSλ₯Ό νλ€λ³΄λ©΄ μΈλ±μ± ν  μΌμ΄ λ§μλ° λ μ£Όλ‘ μ£Όμ΄μ§ λ¦¬μ€νΈ λ±μ κΈΈμ΄λ₯Ό μ΄μ©ν΄μ μΈλ±μ€μ μ κ·Όνμλ€.

```python
for i in range(len(list)):
  print(list[i])
```

κ·Έλ°λ° for λ¬Έμ νμ΄μ¬ μ€νμΌλ‘ μ¬μ©νλ €λ©΄ enumetriate()λ₯Ό μ¬μ©νλκ² λμ μ νμ΄λ κΈμ λ³΄μλ€.

μ enumerate()λ₯Ό μ¨μΌνλμ§, range()μμ μ°¨μ΄μ μ λ¬΄μμΈμ§ μμλ³΄μ

## range()

range()λ νμ΄μ¬ κΈ°λ³Έ λ΄μ₯(built_in) ν¨μμ΄λ€.
μ£Όλ‘ range(stop),range(start,stop,step) λ ννλ‘ λ§€κ° λ³μλ₯Ό λ°λλ€.

[python docs](https://docs.python.org/ko/3/library/functions.html#func-range)λ₯Ό λ³΄λ©΄ range()λ ν¨μλ³΄λ€λ λ²μμ λΆλ³ μνμ€νμ΄λΌνλ€

μ¦ range()λ μ«μμ μνμ€λ₯Ό λνλ΄κΈ° μν΄ μ¬μ©λλ μμ ν  μ μλ μνμ€νμ΄λ€.

## enumerate()

enumerateλ "μ΄κ±°νλ€"λ λ»μ΄λ€. 
enumerate()λ μλμ κ°μ΄ (sequence,count) ννλ‘ μ΄κ±° κ°μ²΄λ₯Ό ννλ‘ λ°ννλ€.

```python
def enumerate(sequence,start=0):
  n=start
  for elem in sequence:
    yield n, elem
    n+=1
```

μλ₯Ό λ€μ΄ μ¬κ³μ μ΄ μ μ₯λ λ¦¬μ€νΈλ₯Ό enumerate()μ λ£μ΄λ³Έλ€λ©΄

```python
seaons=['spring','summer','fall','winter']
list(enumerate(seaons))
```

[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')] μ΄λ° μμΌλ‘ κ°μ²΄λ₯Ό λ°ννλ€.

## μ enumerate()λ₯Ό μ¬μ©νλκ±Έ κΆμ₯νλκ°

[μ€ν μ€λ²νλ‘μ°](https://stackoverflow.com/questions/24150762/pythonic-range-vs-enumerate-in-python-for-loop)μ μ΄μ λν λ΅λ³μ΄ λ¬λ €μλ€.

range()λ₯Ό μ¬μ©ν  κ²½μ° arr[i]μ²λΌ range()μμ λ°νλλ μνμ€λ₯Ό iterable κ°μ²΄μ λ€μ μ§μ΄λ£μ΄μΌνλ€.

μ΄ λ arr[i]λ λ¦¬μ€νΈμ΄κΈ° λλ¬Έμ [μλμ μΌλ‘ ννμ μ¬μ©ν κ²μ λΉν΄ μ²λ¦¬ λΉμ©μ΄ λΉμΈλ€](https://learnbatta.com/blog/why-tuple-is-faster-than-list-in-python-22/).

λν range(len()) ννλ‘ for λ¬Έμ μ¬μ©νλ©΄ indexing κ°λ₯ν(λλ Countable) κ°μ²΄λ§ μ¬μ©κ°λ₯νλ€.

λ°λ©΄μ enumerate()λ₯Ό μ¬μ©νλ€λ©΄ λͺ¨λ  λ°λ³΅λλ κ°μ²΄μμ μ¬μ© κ°λ₯νλ€.

listλ₯Ό μ¬μ©ν  κ²½μ°μ λͺ¨λ  κ°μ²΄λ€μ΄ λ°λ³΅λλμ§ μ λ’°ν  μ μμ§λ§, enumerate κ°μ κ²½μ° νΈμΆλ κ°μ²΄μ λͺ¨λ  ν­λͺ©μ΄ λ°λ³΅λλ κ²μ μ λ’°ν  μ μλ€.

μμΌλ‘λ range(len())λ³΄λ€λ enuemrateλ₯Ό μ¬μ©ν΄λ΄μΌκ² λ€.


