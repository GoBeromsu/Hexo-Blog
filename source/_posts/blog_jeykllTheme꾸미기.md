---
emoji: ๐
categories: etc
title: jeykll theme ๊พธ๋ฏธ๊ธฐ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: https://user-images.githubusercontent.com/37897508/80951329-acfd1e80-8e32-11ea-9590-88a98c185688.png
---

## minimal_mistakes skin ๋ณ๊ฒฝ

ํ์คํ ๋ง์ด ์ฐ์ด๋ ํ๋ง์ธ ๋งํผ ํ๋ง์์์๋ skin์ ๋ณ๊ฒฝํ  ์ ์๋ค.
๊ฐ์ธ์ ์ผ๋ก default skin์ ์น์นํ๊ธฐ๋ํ๊ณ  ๋ต๋ตํด์ ๋ contrast skin์ผ๋ก ๋ณ๊ฒฝํ๋ค.

- \_config.yml - minimal_mistakes_skin

```
minimal_mistakes_skin: "default" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum" "sunrise"
```

Dark๋ ๊ด์ฐฎ์๋ฏ? ์์ดํฐ ๋คํฌ๋ชจ๋ ๋๋๋๋๋ฐ ๊ธ ์ฐ๋ ์ง๊ธ์ด ๋ด์ด๋ผ ๊ทธ๋ฅ ํ๊ณ  ์ถ์ง ์๋ค.

๊ทผ๋ฐ ๋ง์ ์จ๋ณด๋ ์๊ฐ์ด ์ด์ํ๋ค. ๋๋ค๋ฐ์ค์์ ์๊น ๋ฝ์์ ์ด๊ฑฐ๊ฐ์? ์ด๋ฆ์ ์ถฉ์คํ ์คํจ์ธ๊ฐ

## Site default logo image ๋ณ๊ฒฝ

- \_config.yml - logo

```
logo : /assets/images/500x300.png
```

- logo ๊ฐ ๋ญ๊ณ ํ๋ Blog title ์์ ์ด๋ฏธ์ง๋ก ๋์์ง๋ค.

![test](https://user-images.githubusercontent.com/37897508/78419499-447b2000-7681-11ea-9b9b-8353098b52c7.jpg)

๋ณดํต์ assets ํ์ ํด๋์ images๋ผ๋ ํด๋๋ฅผ ๋ง๋ค์ด ์ฌ์ง์ ์ ์ฅํ๊ณ  ์๋๊ฒฝ๋ก๋ก ์ด๋ฏธ์ง๋ฅผ ๊ฐ์ง๊ณ  ์จ๋ค.

- (theme docs์์๋ ๊ถ์ฅํ๋ ๋ด์ฉ์ด๋๋ผ)

## Navigation Bar ์์ 

- \_data/navigation.yml:

```
main:
  - title: "Home"
    url: https://goberomsu.github.io/

  - title: "Categories"
    url: /categories/
  - title: "Tags"
    url: /tags/
```

- title : navigation์ ํ์๋  ์ด๋ฆ
- url : ๋งํฌ (permerlink, hotlink ๋ค ๋๋ค. )

## Font ํฌ๊ธฐ ๋ณ๊ฒฝ

- \_sass/minimal-mistakes/\_variables.scss

```
$doc-font-size: 14 !default;
```

default๊ฐ 16์ธ๋ฐ ์กฐ๊ธ ํฐ๊ฑฐ ๊ฐ์ 14๋ก ๋ฐ๊ฟจ๋ค.

## Text Color ๋ณ๊ฒฝ

- \_sass/minimal-mistakes/skins/ํด๋นํ๋ง.scss

contrast skin์ผ๋ก ๋ฐ๊ฟจ๋๋ฐ ๋ค ์ข์๋ฐ ๋ญ๋๊น Post๊ฐ ํ๋๊ธ์จ๋ก ๋จ๋๊ฒ ๋ง์ ์๋ค์ด์ ์ง์  ๋ค์ด๊ฐ์ ๋ฐ๊ฟจ๋ค.

```
/* Colors */

$text-color: #000 !default;
$muted-text-color: $text-color !default;
$primary-color: #ff0000 !default;
$border-color: mix(#fff, $text-color, 75%) !default;
$footer-background-color: #000 !default;
$link-color: #000000 !default;
$masthead-link-color: $text-color !default;
$masthead-link-color-hover: $text-color !default;
$navicon-link-color-hover: mix(#fff, $text-color, 80%) !default;

```

![test](https://user-images.githubusercontent.com/37897508/78421354-e99df480-7691-11ea-826c-45caa0f47d63.JPG)

visual stuido code๋ฅผ ์ด์ฉํ  ๊ฒฝ์ฐ ๋ง์ฐ์ค ์ปค์๊ฐ #์ ๊ฐ๊น์ด๊ฐ๋ฉด RGB ์ค์  GUI๊ฐ ๋ฌ๋ค.
๊ทธ๋์ ์ง์  ์์ ์ฝ๋๋ฅผ ์๋ ฅํ๊ฑฐ๋ ๊ทธ๋ฅ ๊ณ ๋ฅด๋ฉด ๋๋ค.

## Breadcrumbs ๋ฌ๊ธฐ

- breadcrum ์ด๋ ๊ฒ์๋ฌผ์ ํ์ฌ ๊ฒฝ๋ก๋ฅผ ํ์ํด ์ฃผ๋ ๊ฒ
- \_config.yml -> breadcrumbs : **true** ๋ณ๊ฒฝ
