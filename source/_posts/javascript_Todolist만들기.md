---
emoji: ๐
categories: language
title: javascript๋ก Todolist ๋ง๋ค๊ธฐ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: https://user-images.githubusercontent.com/37897508/81541891-c95b0700-93ae-11ea-8a7e-bafb4383a102.jpg

description: chrome extension ๋ง๋ค๊ธฐ
---

# ์ฝ๋ ๋ฆฌ๋ทฐ

## index html && css

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <link rel="stylesheet" href="index.css" />
    <title>Document</title>
  </head>
  <body>
    <div class="js-clock">
      <h1>00:00</h1>
    </div>
    <form class="js-form form">
      <input type="text" placeholder="what is your name?" />
    </form>
    <h4 class="js-greetings greetings"></h4>
    <script src="clock.js"></script>
    <script src="greeting.js"></script>
  </body>
</html>
```

```css
.form,
.greetings {
  display: none;
}

.showing {
  display: block;
}
```

### ์๋ก ์๊ฒ ๋ ๊ฒ๋ค

- html์์ class ์ ์ธ ํ  ๋ nickname์ ์ธ ์ ์๋ค
  ```html
  <form class="js-form form">
    <input type="text" placeholder="what is your name?" />
  </form>
  ```
  ```CSS
  .form,
  .greetings {
  display: none;
  }
  ```
  - ์์์ ๋ณผ ์ ์๋ค์ํผ class name์ form์ผ๋ก ํด๋ ์ธ์ํ๋ค
    - ์ธ์ ํธํ์ง ์ธ์ ์ค์ ์ด์๋ค

* script tag ์ธ ๋ src๋ก js ํ์ผ๊ณผ ์ฐ๊ฒฐํด์ผํ๋ค
  - ๊น๋จน์ง๋ง!
* css ์ฐ๊ฒฐํ๋ ๋ฒ ๊น๋จน์ง ๋ง์๋ผ
  ```html
  <link rel="stylesheet" href="index.css" />
  ```

## javascript

- ๊ธฐ๋ฅ ๋ณ๋ก jsํ์ผ์ ๋๋ ํ ํ์ผ ์์์๋ function ๋ถํ ์ ํ์ฌ ์ฝ๋๋ฅผ ๊ฐ๊ฒฐํ ํ๋ผ
  - ๊ฐ์ฒด์ ์ค์์ฑ์ด๋ผ ์๊ฐํ๋ค

### clock.js

```javascript
const clockContainer = document.querySelector(".js-clock"),
  clockTitle = clockContainer.querySelector("h1");

function getTime() {
  clockTitle.innerText = ` ${hours < 10 ? `0${hours}` : hours} : ${
    minutes < 10 ? `0${minutes}` : minutes
  } : ${seconds < 10 ? `0${seconds}` : seconds}`;
}

function init() {
  setInterval(getTime, 1);
}

init();
```

#### ์๋ก ์๊ฒ ๋ ๊ฒ๋ค

- javascript์์ html์ ์ ๊ทผํ๋ ๊ฒ๋ crawler์ ๋ค๋ฅด์ง ์๋ค
  - document๊ฐ index.html์ ์ ๋ณด๋ฅผ ๊ฐ์ฒด๋ก ๊ธ์ด์ค๋ฉด ๊ทธ ์ ๋ณด๋ฅผ ํ ๋๋ก ์ด๋ฒคํธ๋ฅผ ๋ฐ์์ํค๋ ๊ฒ์ด ๊ธฐ๋ณธ ๊ฐ๋
- ์ผํญ ์ฐ์ฐ์ ์ค๋๋ง์ ๋ณธ๋ค!
- setInterval(function, interveral time)
  - ์คํ์ํฌ ํจ์์ ํจ์๋ฅผ ๋ค์ ์คํ์ํฌ ๊ฐ๊ฒฉ์ ์ธ์๋ก ๋ฐ๋๋ค
- ,๋ฅผ ์์ฌ์ฉํ์ ์ฝ๋์ ๊ฐ๋์ฑ์ด ์ฌ๋ผ๊ฐ๋ค

### greeting.js

```javascript
const form = document.querySelector(".js-form"),
  input = form.querySelector("input"),
  greeting = document.querySelector(".js-greetings");

const USER_LS = "currentUser",
  SHOWING_CN = "showing";

function paintGreeting(text) {
  form.classList.remove(SHOWING_CN);
  greeting.classList.add(SHOWING_CN);
  greeting.innerText = `Hello ${text}`;
}

function loadName() {
  const currentUser = localStorage.getItem(USER_LS);
  if (currentUser === null) {
    // she is not
  } else {
    paintGreeting(currentUser);
  }
}

function init() {
  loadName();
}

init();
```

#### ์๋ก ์๊ฒ ๋ ๊ฒ๋ค

- html, javascript, css์ ์ฐ๊ฒฐ ๋ฐฉ์
  1. javascript์์ document๋ก html ์์ค๋ฅผ ์ฝ๊ณ  ๊ฐ์ฒด๋ก ๋ง๋ ๋ค
  2. javascript์์๋ ๋ฐ์ ์์ค๋ก html ์์ค์ ์ ๊ทผํ๋ค
     1. function
     2. variable
     3. etc
  3. html์์ ์ ์ธํ class, id, tag๋ฅผ ๋ณํ
  4. ์์๋ฅผ ๋ ๋ค๋ฉด css ์์ ์ฌ๋ฌ ์ต์์ ๋ง๋ค์ด ๋๋๋ค
  5. html tag๋ฅผ ๋ฐ๊ฟ์ผ๋ก์จ ์ด๋ฒคํธ๋ฅผ ๋ฐ์์ํด
