---
emoji: ๐
categories: sql
title: ์ค์ฑํ ์ฌ๋ถ ํ์ํ๊ธฐ - ํ๋ก๊ทธ๋๋จธ์ค SQL ๊ณ ๋์  KIT
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
description:
---
<!-- 
ํํ ๋ฆฌ์ผ, ํ์ฐ ํฌ ๊ฐ์ด๋, ์ค๋ช ,๋ ํผ๋ฐ์ค 
https://documentation.divio.com/tutorials/
-->

# ์ค์ฑํ ์ฌ๋ถ ํ์ํ๊ธฐ

## ๋ฌธ์ 

ANIMAL_INS ํ์ด๋ธ์ ๋๋ฌผ ๋ณดํธ์์ ๋ค์ด์จ ๋๋ฌผ์ ์ ๋ณด๋ฅผ ๋ด์ ํ์ด๋ธ์๋๋ค. ANIMAL_INS ํ์ด๋ธ ๊ตฌ์กฐ๋ ๋ค์๊ณผ ๊ฐ์ผ๋ฉฐ, ANIMAL_ID, ANIMAL_TYPE, DATETIME, INTAKE_CONDITION, NAME, SEX_UPON_INTAKE๋ ๊ฐ๊ฐ ๋๋ฌผ์ ์์ด๋, ์๋ฌผ ์ข, ๋ณดํธ ์์์ผ, ๋ณดํธ ์์ ์ ์ํ, ์ด๋ฆ, ์ฑ๋ณ ๋ฐ ์ค์ฑํ ์ฌ๋ถ๋ฅผ ๋ํ๋๋๋ค.

๋ณดํธ์์ ๋๋ฌผ์ด ์ค์ฑํ๋์๋์ง ์๋์ง ํ์ํ๋ ค ํฉ๋๋ค. ์ค์ฑํ๋ ๋๋ฌผ์ SEX_UPON_INTAKE ์ปฌ๋ผ์ 'Neutered' ๋๋ 'Spayed'๋ผ๋ ๋จ์ด๊ฐ ๋ค์ด์์ต๋๋ค. ๋๋ฌผ์ ์์ด๋์ ์ด๋ฆ, ์ค์ฑํ ์ฌ๋ถ๋ฅผ ์์ด๋ ์์ผ๋ก ์กฐํํ๋ SQL๋ฌธ์ ์์ฑํด์ฃผ์ธ์. ์ด๋ ์ค์ฑํ๊ฐ ๋์ด์๋ค๋ฉด 'O', ์๋๋ผ๋ฉด 'X'๋ผ๊ณ  ํ์ํด์ฃผ์ธ์.

## ํ์ด

```SQL
SELECT ANIMAL_ID,NAME,CASE WHEN(SEX_UPON_INTAKE LIKE '%NEUTERED%' OR SEX_UPON_INTAKE LIKE '%SPAYED%') THEN 'O' ELSE 'X' END AS ์ค์ฑํ FROM ANIMAL_INS ORDER BY ANIMAL_ID
```

* ์กฐ๊ฑด๋ฌธ์ ์ฌ์ฉํ  ์ค ์์์ผํ๋ค.

์กฐ๊ฑด๋ฌธ์ SQL์์ 2 ๊ฐ์ง๊ฐ ์๋ค. (CASE ์ If )
(๋์ค์ ๊ณต๋ถํ๋ค ๋ฐฐ์ฐ๋ฉด ๋ ๊ธฐ์ ํ๊ฒ ์)

CASE์ ๊ฒฝ์ฐ ์๋์ ๊ฐ์ ํ์์ผ๋ก ์ฌ์ฉํ๋ค.
WHEN์ ์ฌ๋ฌ ๊ฐ ์ฌ์ฉํด์ ๋ค์ค ์กฐ๊ฑด๋ฌธ์ผ๋ก๋ ์ฌ์ฉํ  ์ ์๋ค.

```SQL
CASE WHEN ์กฐ๊ฑด๋ฌธ THEN ์ฐธ์ธ ๊ฒฝ์ฐ์ ๊ฐ ELSE ๊ฑฐ์ง์ธ ๊ฒฝ์ฐ์ ๊ฐ END ์ปฌ๋ผ ๋ช
```

If ๋ฌธ์ ์๋์ ๊ฐ๋ค

```if
IF (์กฐ๊ฑด๋ฌธ) ์ฐธ์ผ ๊ฒฝ์ฐ์ ๊ฐ ELSE ๊ฑฐ์ง์ผ ๊ฒฝ์ฐ์ ๊ฐ END ์ปฌ๋ผ๋ช
```