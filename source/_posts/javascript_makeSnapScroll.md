---
emoji: ๐
categories: language
title: ๋ฐ๋๋ผ ์๋ฐ์คํฌ๋ฆฝํธ๋ก Snap scroll ๊ตฌํ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
description: ๋๋ฆ์ ๊ณํ์ ์์๋ค ์ฝ์งํ๊ธฐ ์ ๊น์ง
---

## ์ฌ์  ์กฐ์ฌ

### Snap-Scroll ๊ตฌํ ๋ฐฉ์

์ค๋ ์คํฌ๋กค์ [fullPage.js](https://alvarotrigo.com/fullPage/ko/)๋ ์ด๋ฒ์ CSS ์๋ฐ์ดํธํ๋ฉด์ ์ถ๊ฐ๋ CSS-Snap-Scroll ๊ธฐ๋ฅ์ผ๋ก ๊ตฌํํ๋ค

๋ณดํต ์คํฌ๋กค์ ํธ๋ฆฌ๊ฑฐ๋ก ์ฌ์ฉํด ํ์ด์ง๋ฅผ ๋ฐ๊พธ๋๊ฑธ ๋ชฉ์ ์ผ๋กํ๋๋ฐ ๋๊ฐ์ ๊ฒฝ์ฐ ํ ํ์ด์ง ๋ด์์ ์ ๋ชฉ ๋จ์๋ก ์ ๋๋ฉ์ด์์ ๊ตฌํํ๊ณ  ์ถ์๋ค.

์คํฌ๋กค์ ํ ๋ฒ ํ๋ฉด ๋ค์ ์ ๋ชฉ๊น์ง ์ฃผ๋ฅด๋ฅต ๋ด๋ ค๊ฐ๋ ์ ๋๋ฉ์ด์์ ์์ํ๋๋ฐ ์ฐพ์๋ณด๋ ๊ฐ์ฅ ๋น์ทํ ์ ๋๋ฉ์ด์์ด Snap-scroll ์ ๋๋ฉ์ด์์ด์๋ค. ํ์ง๋ง fullPage.js๋ css ๋ด์ฅ Snap-Scroll ๊ธฐ๋ฅ์ ์ฌ์ฉํ์ง๋ง ์คํจํด์ ๋ฐ๋๋ผ ์๋ฐ์คํฌ๋ฆฝํธ๋ก ๊ตฌํํด๋ณด๊ธฐ๋ก ํ๋ค

(2021.09.22) CSS-SNAP-Scroll ๋์ ํด๋ดค๋๋ฐ ์๋๋ค. ๋ด๊ฐ ํฌ์คํธ๋ฅผ ์ฐ๋ฉด ํํ๋ฆฟ ์์ง์ ๊ฑฐ์ณ์ ํฌ์คํธ๋ฅผ html๋ก ๋ณํํ๋ค. page-content div ํ์์ h2 ํ๊ทธ ๊ธฐ์ค์ผ๋ก div๋ฅผ ๋ฌถ์ด ์ฌ๋ฆฌ๋ ค๋ฉด ์์ง์ ๋ฏ์ด ๊ณ ์ณ์ผํ๋ ๊ฒ๋ ๋ฌธ์ ์ธ๋ฐ CSS-SNAP-Scroll์ ์ฐ๋๋ผ๋ ๋ด ์๊ฐ๋๋ก ๊ตฌํํ๋ ค๋ฉด ๋ณ๋์ ์คํฌ๋กค์ ๋ ์จ์ผํ๋ค

#### ๋ธ๋ก๊ทธ ์์ค ๋ถ์

ํ์ฌ ๋ด๊ฐ ์ฐ๊ณ  ์๋ theme์ [Butterfly](https://github.com/jerryc127/hexo-theme-butterfly)์ด๋ค.
butterfly ํ๋ง์ layout ๋๋ ํฐ๋ฆฌ ํ์์ post.pug๋ฅผ ๋ณด๋ฉด ํฌ์คํธ์ ๋ด์ฉ๋ค์ด page-content ํด๋์ค ํ์์ ๋ฟ๋ ค์ง๋ค.

![post-pug](/img/makeSnapScroll_pug.jpg)
![๋ธ๋ก๊ทธ ํฌ์คํธ์ html ์์ค](/img/makeSnapScroll_pageContent.jpg)

post ๋ ์ด์์์ /source/css/\_layout/post.styl์ ์ ์๋์ด ์๋ค.
๋ ์ด์์์ css ํ๋ฆฌํ๋ก์ธ์์ธ styl์ ์ฌ์ฉํด ์๋ ์ฌ์ง์ beautify()์ฒ๋ผ ํจ์๋ก ํ์๋ค์ ๋ฌถ์ด์ ์ฌ์ฉํ๊ณ  ์์๋ค.

![post.styl](/img/makeSnapScroll_css.jpg)

## ๊ตฌํ

### ๋ชฉํ && ์์ด๋์ด

ํ๊ทธ๋ค๊ณผ ํ์ฌ ๋ทฐํฌํธ์ ์ ๋ ์์น๋ฅผ ๊ณ์ฐ ํ ๋ทฐํฌํธ์ ํ๊ณผ ๊ฐ์ฅ ๊ฐ๊น์ด ํ๊ทธ๋ก ์ด๋ํ๊ฒ ํ๋ค

- ๋ทฐํฌํธ ๋ด์ H2 Tag๊ฐ ์ ์ผํ  ๋๋ง ์ ๋๋ฉ์ด์์ ์คํ ์ํจ๋ค
- ๋ทฐํฌํธ์ 3 ๋ฑ๋ถํ์ฌ ์ต์๋จ์ ์ ์ธํ ์์ญ์ h2 ํ๊ทธ๊ฐ ์์ ๋ ์ ๋๋ฉ์ด์์ ์คํํ๋ค
- ๋ค์ด ์คํฌ๋กค ํ  ๋๋ง ์ ๋๋ฉ์ด์์ ์คํํ๋ค

#### ์์ด๋์ด

1. h2 ํ๊ทธ๋ค์ ์์น๋ฅผ ์ธ์ ๋ธ๋ผ์ฐ์ ์ ์ ์ฅํ์
2. ํ๊ทธ๋ค์ ์ ๋์์น๋ง ๊ธฐ์ตํด๋๊ณ , ๋ทฐํฌํธ ์์ ์๋์ง๋ง ์ฒดํฌํด์ ์ ๋๋ฉ์ด์์ ์คํ์ํค๋ฉด ๋์ง ์์๊น?

### Source Code

```js
const h2Tags = document.querySelectorAll("h2");
const viewPortHeight = document.documentElement.clientHeight;
let bPosition = document.documentElement.scrollTop;
const h2Height = 42;
const viewPortDownBuffer = 150;
let count;

const setTagsStorage = function () {
  count = 0;
  for (tag of h2Tags) {
    count++;
    sessionStorage.setItem(count, tag.offsetTop - h2Height);
    console.log("tag" + count + " : " + sessionStorage.getItem(count));
  }
};
setTagsStorage();

const getTag = function (tagNum) {
  return parseInt(sessionStorage.getItem(tagNum));
};

const getTagsLength = function () {
  return h2Tags.length;
};

// ๋ทฐํฌํธ ๋์ด์ 2/3 ~ 1 ์์ ํ๊ทธ๊ฐ ์๋๊ฐ
const checkInTag = function () {
  for (count = 1; count <= getTagsLength(); count++) {
    if (
      window.pageYOffset <= getTag(count) &&
      getTag(count) < window.pageYOffset + (viewPortHeight - viewPortDownBuffer)
    ) {
      return true;
    }
  }
  return false;
};

const checkTagOnTop = function () {
  for (count = 1; count <= getTagsLength(); count++) {
    if (
      window.pageYOffset < getTag(count) &&
      getTag(count) < window.pageYOffset + 20
    ) {
      return true;
    }
  }
  return false;
};

const checkDown = function () {
  const aPosition = document.documentElement.scrollTop;
  if (bPosition < aPosition) {
    bPosition = aPosition;
    return true;
  }
  bPosition = aPosition;
  return false;
};
const snapScroll = function () {
  if (!checkTagOnTop() && checkInTag()) {
    scrollBy(0, 10);
  }
};

window.addEventListener("scroll", function () {
  if (checkDown()) {
    snapScroll();
  }
});
```

### function ์ค๋ช

#### setTagsStorage

```js
const setTagsStorage = function () {
  count = 0;
  for (tag of h2Tags) {
    count++;
    sessionStorage.setItem(count, tag.offsetTop - h2Height);
  }
};
```

setTagsStorage๋ ๋ฌธ์์ ์๋จ๋ถํฐ ์์ฐจ์ ์ผ๋ก h2 ํ๊ทธ๋ค์ ์์น๋ฅผ ์ธ์ ์คํฐ๋ฆฌ์ง์ ์ ์ฅํ๋ ํจ์์ด๋ค

ํ๊ทธ ๊ฐ๋ค์ ์ ์ฅํ๊ธฐ ์ํด์๋ ์ธ์ ์คํฐ๋ฆฌ์ง๋ฅผ ์ด์ฉํ๋๋ฐ ํ๊ทธ๋ค์ ์์น๋ง ์ ์ฅํ๋ฉด ๋๋ ๊ฐ๋จํ ์ผ์ด๋ผ ๋ฐ์ดํฐ๋ฒ ์ด์ค๋ฅผ ์ด์ฉํด์ผํ  ํ์์ฑ์ ๋ชป ๋๊ปด ๋ธ๋ผ์ฐ์ ์ ์ ์ฅํ๋๊ฒ ๋์ ๊ฒ ๊ฐ๋ค ์๊ฐํ๊ธฐ ๋๋ฌธ์ด๋ค

๋ธ๋ผ์ฐ์ ์ ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ๋ ๋ฐฉ๋ฒ์ผ๋ก๋ ๋ก์ปฌ ์คํฐ๋ฆฌ์ง, ์ธ์ ์คํฐ๋ฆฌ์ง ๋ฑ์ด ์๋๋ฐ ๋ก์ปฌ ์คํฐ๋ฆฌ์ง ๊ฐ์ ๊ฒฝ์ฐ ๋ธ๋ผ์ฐ์ ์ ๊ฐ์ด ์ ์ฅ๋ ํ ์ฌ์ฉ์๊ฐ ๋ฐ๋ก ์ ๊ฑฐํ์ง ์์ ๊ฒฝ์ฐ ๊ณ์ ์ ์ฅ๋๊ธฐ ๋๋ฌธ์ ์ฌ์ฉํ์ง ์์๋ค.

์ธ์ ์คํฐ๋ฌ์ง ๊ฐ์ ๊ฒฝ์ฐ๋ ๋ธ๋ผ์ฐ์ ๋ฅผ ๋ซ์ ๋ ์ ์ฅ๋ ๊ฐ๋ค์ด ์ง์์ง๋ค.

(2021.10.03) ๊ทธ๋ผ์๋ ํ์ด์ง๋ฅผ ๋ ๋  ๋ ์ธ์ ์คํฐ๋ฆฌ์ง ๊ฐ์ ์ง์ฐ๋๊ฒ ์ข์๋ฐ ์์ง ๊ตฌํํ์ง ์์๋ค. ์ผ๋จ์ ํ์ด์ง๋ฅผ ์ฎ๊ธธ ๋ ๋ง๋ค ํ๊ทธ ๊ฐ๋ค์ ๋ฎ์ด ์์์ ์๋ํ๊ณ  ์๋ค.
#### getTags

```js
  const getTag = function (tagNum) {
    return parseInt(sessionStorage.getItem(tagNum));
  };
```

getTag๋ ๋ธ๋ผ์ฐ์ ์ ์ ์ฅ๋์ด ์๋ ๊ฐ๋ค์ ํค ๊ฐ์ ์ด์ฉํด ๊ฐ์ ธ์ค๋ ๋ฉ์๋์ด๋ค.
์ธ์ ์คํฐ๋ฆฌ์ง์ ์ ์ฅ๋ value๋ String์ด๋ผ์ ์ ์๋ก ๋ฐ๊ฟ์ค ํ ๋ฐํํ๊ฒ ํ์๋ค.

#### getTagsLength
```js
  const getTagsLength = function () {
    return h2Tags.length;
  };
```

h2Tags๋ document์ ์ฟผ๋ฆฌ ์๋ ํฐ๋ก ๋ฌธ์ ๋ด h2 ๊ฐ๋ค์ด ์ ์ฅ๋์ด ์๋ ๋ธ๋ ๋ฐฐ์ด์ด๋ค.

๋ฌธ์ ๋ด h2 ๊ฐ๋ค์ด ์ผ๋ง๋ ์ ์ฅ๋์ด ์๋์ง ์ ์ ์๋ค.

#### checkInTag
```js
  const checkInTag = function () {
    for (count = 1; count <= getTagsLength(); count++) {
      if (
        window.pageYOffset <= getTag(count) &&
        getTag(count) <
          window.pageYOffset + (viewPortHeight - viewPortDownBuffer)
      ) {
        return true;
      }
    }
    return false;
  };
```

checkInTag๋ ํ์ฌ ๋ทฐํฌํธ(๋ธ๋ผ์ฐ์ ๊ฐ ์ ์ ์๊ฒ ํ์ฌ ๋ณด์ฌ์ฃผ๊ณ  ์๋ ํ๋ฉด)์ ํ๊ทธ๊ฐ ์๋ค๋ฉด true๋ฅผ ๋ฐํํ๋ ํจ์์ด๋ค
๋จ ๋ทฐํฌํธ์์ ํ๋จ์์๋ ์ ๋๋ฉ์ด์์ ๋ฐ์์ํค๊ณ  ์ถ์ง ์์ viewPortDownBuffer๋ฅผ ์ด์ฉํด ๋ทฐํฌํธ ํฌ๊ธฐ๋ฅผ ์ ํํ๋ค.

#### checkTagOnTop
```js
  const checkTagOnTop = function () {
    for (count = 1; count <= getTagsLength(); count++) {
      if (
        window.pageYOffset < getTag(count) &&
        getTag(count) < window.pageYOffset + 20
      ) {
        return true;
      }
    }
    return false;
  };
```

๋ทฐํฌํธ ์ต์๋จ์ ํ๊ทธ๊ฐ ํ์ฌ ์์นํด ์๋ค๋ฉด true๋ฅผ ๋ฐํํ๋ ํจ์์ด๋ค. 
์คํฌ๋กค ์๋๊ฐ ๋๋ฌด ๋น ๋ฅด๋ฉด ์ ํด ๋์ ๊ฐ์ ์ง๋๊ฐ๋ฒ๋ฆฌ๋ ๋ฒ๊ทธ๊ฐ ์์ด์ ๋ทฐํฌํธ ์๋จ ๊ฐ๊ณผ ๋น๊ตํ๋๊ฒ ์๋๋ผ ๋ทฐํฌํธ ์๋จ ์ผ์  ๋ฒ์ ๋ด์ ์๋์ง ์ฒดํฌํ๊ฒ ํจ์๋ฅผ ์์ ํ๋ค.


#### checkDown
```js
  const checkDown = function () {
    const aPosition = document.documentElement.scrollTop;
    if (bPosition < aPosition) {
      bPosition = aPosition;
      return true;
    }
    bPosition = aPosition;
    return false;
  };
```

์คํฌ๋กค ์ด๋ฒคํธ๊ฐ ๋ฐ์ํ๋ฉด ์คํฌ๋กค์ ํ์ฌ ์์น์ ๋ง์ง๋ง ์์น๋ฅผ ๋น๊ตํด ์คํฌ๋กค์ด ์๋๋ก ๋ด๋ ค๊ฐ๊ณ  ์๋์ง ํ์ธํ๋ ํจ์์ด๋ค.

์ ๋๋ฉ์ด์์ ๋ค์ด ์คํฌ๋กคํ  ๋๋ง ์ ๋๋ฉ์ด์์ ๋ฐ์์ํค๊ณ  ์ถ์ด์ ์ถ๊ฐํ๋ค.

#### snapScroll ์ ๋๋ฉ์ด์ ๊ตฌํ
```js
  const snapScroll = function () {
    if (!checkTagOnTop() && checkInTag()) {
      scrollBy(0, 10);
    }
  };

  window.addEventListener("scroll", function () {
    if (checkDown()) {
      snapScroll();
    }
  });
```

scrollby๋ ํ์ฌ ์์น์์ ์คํฌ๋กค์ ์ง์ ํ ํฝ์๋งํผ ์ด๋์ํค๋ ํจ์์ด๋ค. 
์์ ์์ ํ check ํจ์๋ค์ ์คํฌ๋กค ์ด๋ฒคํธ๊ฐ ๋ฐ์ํ  ๋ ๋ง๋ค ์ฒดํฌํด์ ์ด๋ํ๊ฒ ๋ง๋ค์๋ค.


## ํผ๋๋ฐฑ

1. ์๊ณ ๋ฆฌ์ฆ ๊ณต๋ถ์ ํ์์ฑ์ ๋๊ผ๋ค.
    ๊ฐ๋ฐ์ ๋ฌธ์  ํด๊ฒฐ์ ์ฐ์์ด๋ค. ์ฝ๋๋ฅผ ๋ช ๋ฒ ๊ฐ์ ์๋ค๋ณด๋, ๊ทผ๋ณธ์ ์ผ๋ก ์๊ณ ๋ฆฌ์ฆ ๋ฅ๋ ฅ์ด ์ข์๋ค๋ฉด ๋ ๋น ๋ฅด๊ฒ ๋ง๋ค ์ ์์ง ์์์๊น ์ถ์๋ค. ์ง๊ธ ๋ด๊ฐ ์ง๋ ์ฝ๋๊ฐ ์ผ๋ง๋ ํจ์จ์ ์ธ์ง ๊ฐ๋ ์ด ์๋๋๊น ์กฐ์ฌ์ค๋ฝ๊ธฐ๋ ํ๊ณ , ๊ฐ์๊ธฐ ๋ธ๋ผ์ฐ์ ์์ ๋ฉ๋ชจ๋ฆฌ ์๋ชจ๊ฐ ์ฌํ๋ค๊ณ  ์๋ฆผ์ด ๋จ๊ณ  ํ๋ ์ด๋์ ๋ค๋ค ์๊ณ ๋ฆฌ์ฆ ๊ณต๋ถ๋ฅผ ํ๋๊ตฌ๋ ์์ผ ์์๊ฐ๋ ์๊ฐ์ด์๋ค.
2. ํ์คํธ ์ผ์ด์ค๋ ์ฝ๋๋ฅผ ์์ฑํ์ง ์๊ณ  ๋ง๋ค์๋ค
    console.log๋ฅผ ์ด์ฌํ ์ฐ์ด๊ฐ๋ฉฐ ํจ์๋ค์ ๊ตฌํํ์ง๋ง, ํ์คํธ ์ฝ๋๋ฅผ ์ฌ์ฉํ์ง ์์๊ฒ ์์ฝ๋ค. ์ฝ๋๊ฐ ๋ช ์ญ ์ค ๋ฐ์ ์๋๋๋ฐ ์ค๊ฐ ์ค๊ฐ ํค๋งจ์ ์ด ์๋๋ฐ ์ข ๋ ๋ ํค๋งฌ ์ ์์ง ์์์๊น ์ถ๋ค