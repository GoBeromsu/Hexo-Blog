---
emoji: ๐
categories: language
title: ์ฝํ๋ฆฐ 2์ผ์ฐจ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: 
description:
---

## 2์ผ ์ฐจ๋ฅผ ์์ํ๋ฉด์

๊ธ์ ์ธ ๋๋ง๋ค ์ฝ๋๋ฅผ ๋ค ๋ถ์ฌ ๋ฃ์ ์ ์์ผ๋ ์ปค๋ฐ์ ํ  ๋ ๊ธฐ๋ฅ ๋ณ๋ก ๋๋ ์ ํด์ผ๊ฒ ๋ค๋ ์๊ฐ์ด ๋ค์๋ค. ๊ทธ๋ฅ ๋จ๊ธฐ๊ธฐ ์ฉ๋๋ผ ํํ ํ  ๋ ๋นผ๋ฉด ๊ฑฐ์ ์ ๊ฒฝ ์์ผ๋๋ฐ ์ด๋ฐ๊ฒ ๊ธฐ๋ณธ์ด์ง ์๋ ์ต๊ด ๋ค์ฌ์ผ๊ฒ ๋ค.

## ํ๋ฉด ์ถ๊ฐ ๋ฐ ์ฐ๊ฒฐ

- ์๋ฆฌ๋ ๊ฐ๋จํ๋ค. ์กํฐ๋นํฐ ์ถ๊ฐ, manifest์ ์กํฐ๋นํฐ ์ถ๊ฐ, xml ํ์ผ ์ถ๊ฐ
  - ์กํฐ๋นํฐ(๊ธฐ๋ฅ), xml(ํ๋ฉด), manifest(ํ๋ฝ ๋ฐ๊ธฐ?)

```kotlin
        button_list.setOnClickListener {
            var intent = Intent(this, PlaylistActivity::class.java)
            startActivity(intent)
        }
```

- ์์ ์ฝ๋๋ mainActivity์ ๋ฒํผ ์ฝ๋์ด๋ค
  - intent ์์ PlaylistActivity ์ถ๊ฐ
  - ์กํฐ๋นํฐ ์ถ๊ฐ

## ๋ ์ฝ๋ฉ ๋ ํ์ผ ์ฝ์ด์ค๊ธฐ

```kotlin
class PlaylistActivity : AppCompatActivity() {

    var mp3Path: String = Environment.getExternalStorageDirectory().absolutePath + "/Download/"
    var listFiles = File(mp3Path).listFiles()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.playlist)

        var fileName: String? = null
        var extName: String? = null
        var mp3List = mutableListOf<String>()

        for (file in listFiles) {
            fileName = file.getName()
            extName = fileName.substring(-3)
            if (extName == "mp3") {
                mp3List.add(fileName)
            }
        }

        button_back.setOnClickListener {
            var intent = Intent(this, MainActivity::class.java)
            startActivity(intent)
        }
    }
```

1. Download ํด๋ ๋ด ํ์ผ๋ค์ listfiles()๋ก ๊ฐ์ ธ์จ๋ค
2. ๊ฐ์ ธ์จ ํ์ผ๋ค ์ค ํ์ฅ์(๋ค์ 3์๋ฆฌ)๊ฐ mp3์ธ ํ์ผ์ ์ด๋ฆ์ mp3List์ ๋ฃ๋๋ค

* ์ด์  mp3 ํ์ผ๋ง ๋ถ๋ฌ์์ ์ถ๋ ฅํ๋ฉด ๋๋ค.

### ์๋ฌ ์ฌํญ

* ํ์ผ์ด ๋ฐฐ์ด์ ์ถ๊ฐ๊ฐ ์๋๊ธธ๋ ๋ญ์ง? ํ๋๋ฐ ์๋ ์ฝํ๋ฆฐ์์ arraylist๋ ์ถ๊ฐ ๋ถ๊ฐ๋ฅ์ด๋๋ค
  * ๊ทธ๋์ mutablelist๋ก ๋ฐ๊ฟ์ ์ ์ธํ๋ค.
* ๋ฆฌ์คํธ ๋ทฐ๋ฅผ ๋ง๋๋ ค๊ณ  ํ๋๋ฐ ๊ณ์ ์คํจํ๋ค. 
  * ๋ฆฌ์คํธ ๋ทฐ๋ ์ด๋ํฐ๊ฐ ํ์ํ๋ฐ ์ด๋ํฐ์ ๋ํ ์ดํด๊ฐ ๋ถ์กฑํ๋ค.
* ์ผ๋จ ์ด๋ํฐ๊ฐ ๊ตฌํ์ด ์๋์ ๋นผ๊ณ  ์คํํ๋๋ฐ ํ๋ฉด์ด ๊บผ์ ธ์ ๋ญ๊ฐํ๋๋ ์๋๋ก์ด๋๊ฐ ์๋ ๊ทธ๋ฐ๊ฐ ์๋ฌ๊ฐ ๋ฐ์ํ๋ฉด ๊ทธ๋ฅ ์๋๋ค
  * ๋งํ๊ณ  ๋ณด๋ ๋น์ฐํ๊ฑฐ๊ฐ๋ค

## ์์ผ๋ก ํ ์ผ

* ๋๋ฒ๊น ํ  ๋ ํธํ๊ฒ ์ค๊ฐ ์ค๊ฐ ์งํ์ฌํญ ์ถ๋ ฅํ๊ฒ ๋ง๋ค์ด์ผ๊ฒ ๋ค
  * println๊ฐ์ ๊ฑธ๋ก