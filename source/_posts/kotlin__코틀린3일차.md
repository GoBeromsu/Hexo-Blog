---
emoji: ๐
categories: language
title: ์ฝํ๋ฆฐ3์ผ์ฐจ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: 
description:
---

## ์๊ฐ ์ถ๋ ฅ ์ค๋ฅ ์์ 

- ๋ถ๋ชํ ์๊ฐ๊ณผ ํจ๊ป ์์ ๋๋๋ก ํด๋์๋๋ฐ [์ฐ๋ ๊ธฐ ๊ฐ].mp3๋ก ์ ์ฅ๋์ ์์ ํ๋ค!

```kotlin
  val timeFormat = SimpleDateFormat("yyyyMMddHHmm")
  val time = timeFormat.format(java.util.Date())
  val fileName: String = time + ".mp3"
```
* SimpleDateFormat()์ ์ด์ฉํด ์๊ฐ ํฌ๋งท์ ์ค์ ํ๋๋ ํด๊ฒฐ๋์๋ค.

## listview listener ์ค์ 

```kotlin
        setContentView(R.layout.playlist)
        view_mp3.adapter = ArrayAdapter(this, android.R.layout.simple_list_item_1, mp3List)

        view_mp3.onItemClickListener =
            AdapterView.OnItemClickListener { parent, view, position, id ->
                val seletedVoice = parent.getItemAtPosition(position) as String

                Toast.makeText(this, "${Environment.getExternalStorageDirectory()}/Download/"+seletedVoice, Toast.LENGTH_SHORT).show()

                audioPlay.setDataSource("${Environment.getExternalStorageDirectory()}/Download/"+seletedVoice)
                
                audioPlay.prepare()
                audioPlay.start()
            }
```

* ArrayAdapter๋ก ๋ฆฌ์คํธ๋ทฐ์ ๋ฐฐ์ด์ ์ฐ๊ฒฐํ๋ค
* onItemClickListener๋ฅผ ์ ์ํ๋ค
  * ํด๋ฆญํ ์์ดํ์ ํฌ์ง์์ ๋ฌธ์์ด๋ก ๋ฐ๋๋ค
    * ๋ฐ์ ๋ฌธ์์ด์ ์ด๋ฆ์ toast๋ก ์๋ฆผ
    * download ํ์ ํ์ผ ์ค ๊ฐ์ ์ด๋ฆ์ mp3 ํ์ผ์ ์ฐพ์ ์ฌ์

* mediaplay์์ prepare ํ์ง ์์ผ๋ฉด start ๋ชปํจ

## ํฅํ ๊ณํ

* ์ฌ์๋ ๋๊ณ  ๋ฆฌ์คํธ๋ทฐ๋ ์์ฑํ๋๋ฐ ์ฌ๊ธฐ์ ์์ฑ๋๋ฅผ ๋ ๋์ฌ์ผํ ๊น?
  * ์ฐ์ฐํ  ๊ฑฐ ๊ฐ๊ธฐ๋ ํ๊ณ  ํ  ๊ณ ๋ฏผ ์ค์ด๋คใฃ
* ์ ๋ณด๊ฐ ํํธํ๋์ด์์ด์ ๊ณต๋ถํ๋๋ฐ ์ด๋ ต๋ค
  * docs ๋ณด๋ฉด์ ๊ณต๋ถํ๋ ์ฆ