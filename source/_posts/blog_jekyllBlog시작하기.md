---
emoji: ๐
categories: etc
title: Jekyll set up 
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
excerpt: "๋ธ๋ก๊ทธ ์ด๊ธฐ ์ธํ"

toc: true
toc_sticky: true
cover: https://user-images.githubusercontent.com/37897508/80951329-acfd1e80-8e32-11ea-9590-88a98c185688.png
---

๋ด๊ฐ ์ฐ๋ jekyll theme์ minimal-mistakes ๋ณดํธ์ ์ด๋ผ ์ฐธ๊ณ ํ  ๊ฒ๋ ๋ง๊ณ  setup์ด ํธํ๋ค

## Jekll setting

- ์ค๋น๋ฌผ : jekyll theme, git, ruby(๋ 2.6.4 ์ฐ๋ ์ค)

* github์ ํฌ์คํธ๋ฅผ ์ปค๋ฐํ๊ณ  ๋ธ๋ก๊ทธ๋ฅผ ์ง์ ํ์ธํ๋ ๊ฒ๋ ์ข์ง๋ง ๋๋ฌด ๋๋ ค์ local์์ ์คํํด์ ํ์ธํ๋๊ฒ ํ ์ผ์ฌ ํธํ๋ค

1. git bash๋ฅผ ๋ก์ปฌ repo์์ ์คํ
2. jeykll ๊ด๋ จ install

   ```

   $ gem install jekyll
   $ gem install minima
   $ gem install bundler
   $ gem install jekyll-feed
   $ gem install tzinfo-data
   ```

3. bundle install

   gemํ์ผ์์ ํ์ํ ๊ฒ๋ค์ ์ฝ๊ณ  ๋ค์ด๋ก๋ ๋ฐ์์ฃผ๋ ๋๋์ด์

4. jekyll serve

- --livereload : ์์ ๋ง๋ค ์๋ก ๊ณ ์นจ
- ์ฌ๊ธฐ๊น์ง ํ๋ฉด ๋ก์ปฌ์์ ์คํํ  ์ ์์

- local์์ post ๋ณผ ๋ ํฌ์คํธ ์ด๋ฆ์ด ํ๊ธ์ด๋ฉด weblick ์๋ฌ๋ฌ๋ค.

## YML ํ์

jekyll post์ ๊ฒฝ์ฐ์๋ yml ํ์์ ๋ฐ๋ผ ํฌ์คํธ ์ธ๋ถ ์ค์ ์ ํ  ์ ์๋ค.

```
---
title:  "Blog post YML ์์"
excerpt: ""

toc_sticky : true
---
```

- title : ์ ๋ชฉ
- excerpt : ๋๋ต์  ์๊ฐ(๊ฒ์๊ธ ๋ฆฌ์คํธ์ ํ์๋จ )
- categories : ์นดํ๊ณ ๋ฆฌ ๋ถ๋ฅ
  - theme ์์ฒด์ ์ผ๋ก ์๋ก์ด ์นดํ๊ณ ๋ฆฌ๋ฅผ ์๋ ฅํ  ๊ฒฝ์ฐ ๊ทธ ์นดํ๊ณ ๋ฆฌ๋ฅผ ์์ฑํด์ค๋ค.
- tags : ํ๊ทธ ๋ถ๋ฅ
- toc : ํค๋๋ฅผ ์ฝ๊ณ  ํ์
- toc_sticky : toc ๊ณ ์ 
