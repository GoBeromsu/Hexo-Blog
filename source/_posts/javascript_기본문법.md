---
emoji: ๐
categories: language
title: javascript ๋ฌธ๋ฒ ๋ง๋ณด๊ธฐ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: https://user-images.githubusercontent.com/37897508/81468381-2cfffb80-921a-11ea-8481-241cf78073d4.png

description: prompt, if๋ฌธ, ๋ผ๋ฆฌ์ฐ์ฐ์
---

## javascript ๊ธฐ๋ณธ ๋ฌธ๋ฒ

- ์ธ์ด๋ฅผ ์ด๊ฑฐ์ ๊ฑฐ ์จ๋ณด๋ค๋ณด๋ ๋๋ผ๋ ๊ฑด๋ฐ ๊ฑฐ์ ๋น์ท ๋น์ทํ๋ค
- [์ํ์ฝ๋ฉ](https://opentutorials.org/course/743/4650) ๋ณด๊ณ  ํํ ๋ฆฌ์ผ ๋ฐ๋ผํ๊ณ  ์ ์ฝ๋ฉ ์๋๋ฉด node.js ๋ง์ ธ๋ณผ๊น ์๊ฐ ์ค์ด๋ค

- **์ ์ค์ก๋ค ์ค๋  ๋ฏธ์ณค์ด**
  - Javascirpt๊ฐ ์๋๊ฐ ํ๋ฆ์ ๋ฐ๋ผ ํ์ฅ์ฑ์ด๋ผ ํด์ผํ๋ ํ  ์ ์๋๊ฒ ๋ง์ ์ก๋๋ฐ ์์ฐ ๊ทธ๋ฅ ๋ค ํ  ์ ์์ด ๋ฉ์ ธ ์ญ๋์ ์ด์ผ ์ฝ์ค,,,
  - ์ด์ง ๊ทธ๋์ ๋ธ๋ง๋ ์ฝ๋์ ๋ฐ๋๋ผ.JS ๋ฐ๋ผํด๋ณผ๊น ์๊ฐ์ค

## ์ฃผ์

- //
  - ํ ์ค ์ฃผ์
- /\* \*/
  - ์ฌ๋ฌ ์ค ์ฃผ์

## ๋ฌธ์

- ๋ฌธ์๋ ' '๋ " " ์ค ํ๋๋ก ๊ฐ์ธ์ผํ๋ค.
- ๋ฌธ์๋ฅผ ๋ํ  ๋ + ์ฌ์ฉ

  ```javascript
  alert("์๋" + "์๋ฐ ๋๋์ด๋๊น?");
  ```

- .length : ๋ฌธ์์ด์ ๊ธธ์ด๋ฅผ ๊ณ์ฐํ๋ ๋ฉ์๋

## ๋ณ์

- ๋ชจ๋  intruction์ ๋ค๋ฅธ ์ค์ ์ ์ธ๋์ด์ผ ํ๋ค
  - ๊ทธ๋ฌ๊ณ  ์ถ์ง ์์ผ๋ฉด ; ์ด์ฉํ์
- ๋ณ์ ์์ฑ, ์ด๊ธฐํ, ์ฌ์ฉ ๋จ๊ณ๋ก ์ฌ์ฉํ์
  - ๊ธฐ๋ณธ์ด๋ค!

```javascript
let a = 221;
let b = a - 5;
console.log(b);
```

- const : ์์
- let : ๋ฐ๋์ด๋ ๋๋ ๋ณ์
- variable : ๋ณ์
  - let์ฒ๋ผ ๋ฐ๋ ์ ์์
- ์ฒซ ์ฌ์ฉ์ const, ํ์ํ  ๋๋ง let!


## ์ฐ์ฐ์

- = : ๋์ ์ฐ์ฐ์
- == : ๋๋ฑ ์ฐ์ฐ์
  - ๊ฐ์ด ๊ฐ์๊ฐ?
- === : ์ผ์น ์ฐ์ฐ์
  - ์ข์ฐ ํญ์ด ์ผ์นํ๋๊ฐ?
- != : ๊ฐ์ง ์๋ค
- && : AND ์ฐ์ฐ์
- || : OR ์ฐ์ฐ์
- ! : ๊ฐ์ ์ญ์ ์ํด, ๋ถ์ ํ๋ ๊ฒ์ด์ง
  - 0 ๋ ๊ด์ต์ ์ผ๋ก false๊ฐ ๋  ์ ์๋ค

## ์กฐ๊ฑด๋ฌธ

```javascript
if (id == "beomsu") {
  alert("์์ด๋๊ฐ ์ผ์นํ๋๊ตฐ");
} else {
  alert("์์ด๋๊ฐ ์ผ์นํ์ง ์์ต๋๋ค");
}
```

- ์ฌ์ค ๋ณ ์ฐจ์ด๊ฐ ์๋ค

## ๋ฐ๋ณต๋ฌธ

```javascript
while (true) {
  document.write("์๋?");
}
```

- document๋ javascript๋ฅผ ์ด์ฉํด ์นํ์ด์ง ๋ฌธ์๋ฅผ ์ ๋๋ฐ ์ฝ์์์ ํ๋ฉด ์๋ณด์ธ๋ค
  - console.log๋ก ๋์ ํ  ์ ์์

## ํจ์

๊ธฐ๋ณธ ํ์์ ์ญ์๋ ๋น์ทํ๋ค

```javascript
function ํจ์๋ช(์ธ์1,์ธ์2... ๋ง์ง๋ง ์ธ์){
  ์ฝ๋
  return ๋ฐํ๊ฐ
}
```

## ๋ฐฐ์ด

- ๋ฐฐ์ด ์ ์ธ์ ์๋์ ๊ฐ์ด ํ๋ฉฐ ๋๋ค

```javascript
const somthing = "something";

const daysOfWeek = ["mon", "true", "sun", true, something];
```

- indexing
  - daysOfWeek[2] --> sun


### ๋ฐฐ์ด ๊ฐ์ง๊ณ  ๋์๋ณด๊ธฐ

- .push()
  - ๊ดํธ ์์ ๊ฐ์ ์ธ๋ฑ์ค์ ๋ฃ์ด์ค
- .shift()
  - ์ธ๋ฑ์ค์ ์ฒซ๋ฒ์งธ ๊ฐ์ ์ญ์ 
- .pop()
  - ์ธ๋ฑ์ค์ ๋ง์ง๋ง ๊ฐ์ ์ญ์ 
- .sort()
  - ์ ๋ ฌ ํจ์
- .reveser()
  - ์ญ์ ์ ๋ ฌ

## ๊ฐ์ฒด

์ฌ๊ธฐ๋ถํฐ ์ข ์ฌ๋ฐ๋ค

- ์ฒ์์ ๋ดค์ ๋ ๋์๋๋ฆฌ ๊ฐ๋ค ์๊ฐํ๋๋ฐ ์ด ํ์์ผ๋ก ๊ฐ์ฒด๋ฅผ ์ ์ฅํ๊ณ  ์๋ค. ์๊ธฐ๋ค
  - ์ ์๋ฆ;; json์ด javascript Object Notion์ด๋ ๋ป์ธ๋ฐ ์ด์ฉ์ง json์ด๋ ๋๊ฐ๋ค ์์ฃผ ๊ทธ๋ฅ ํํํ๋๊ฒ ์ ๊ธฐํ๋ค

```javascript
var beomsu = {
  name: "beomsu",
  show: function () {
    alert(this.name);
  },
};
beomsu.show();
```

์์ ์ฝ๋๋ฅผ ์คํ์ํค๋ฉด ์๋์ ๊ฐ์ ํ๋ฉด์ ํ์ธํ  ์ ์๋ค.

- ์ฝ๋ ๋ฆฌ๋ทฐ
  - name์ beomsu ์ ์ฅ
  - show๋ผ๋ function ์ ์ธ
    - show ํจ์๋ ์ด ํด๋์ค์ name์ ์ ๊ทผํด ์ด๋ฆ์ ์ถ๋ ฅํ๋ค

![image](https://user-images.githubusercontent.com/37897508/81466619-02a84100-920e-11ea-835d-234d734b4598.png)

## ๋ชจ๋

- ์์ฃผ ์ฌ์ฉ๋๋ ์ฝ๋๋ฅผ ๋ณ๋์ ํ์ผ๋ก ๋ง๋ค์ด ํ์ํ  ๋ ๊ฐ์ ธ๋ค๊ฐ ์ฐ๋๊ฑฐ์ง
- ์ด์ ๋ฐ๋ผ์ ์ ์ง๋ณด์ ๋ฐ ๋ฉ๋ชจ๋ฆฌ ๋ญ๋น ๊ฑฐ๊ธฐ์ ์น๋ธ๋ผ์ฐ์ ์์ ์ฌ์ฉํ๋ค๋ฉด ์๋๊ฐ ๊น์ง ๋นจ๋ผ์ง๋ ๊ฑฐ์ง

* ์๋ js์ html ํ์ผ์ ๊ฐ์ ๋๋ ํฐ๋ฆฌ์ ์์ด์ฉ

```javascript
var beomsu = {
  name: "beomsu",
  show: function () {
    alert(this.name);
  },
};
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <script src="test.js"></script>
    <title>Document</title>
  </head>
  <body>
    <script>
      alert(beomsu.show());
    </script>
  </body>
</html>
```

- html ์ฝ๋๋ฅผ ๋ณด๋ฉด head์์ script source๋ฅผ ๋ฐ์ ์ค๋ ๊ฑธ ๋ณผ ์ ์๋ค. ์ ๋ฐ ๋๋์ผ๋ก ์์ฃผ ์ฌ์ฉํ๋ ๋ชจ๋์ ๋ฐ์์ค๋ฉด ๋๋ค. ๋ญ jquery์ด๋ฐ ๊ฒ๋ค ๋ง์ด๋ค
- ๋์  ํ๊ฒฝ๋ง๋ค ์์ค๋ฅผ ๋ฐ์์ค๋ ๋ฐฉ๋ฒ์ด ๋ค๋ฅด๋ค
  - ์๋ฅผ ๋ค์ด node.js๋ web์ ์ฐจ์ด๋๊น

## DOM(Document Object Module)

- document๋ก javascript์์ css์ ์ ๊ทผ ํ  ์ ์๋ค.
- JS์์ ๋ด HTML์ ๋ชจ๋  ๊ฒ๋ค์ ๊ฐ์ฒด๋ก ๋ฐ๊ฟ ๋ฒ๋ ค ์ ๊ทผ ๊ฐ๋ฅํ๊ฒ ํ๋ ๊ฒ์ด์ง

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="CSS.css" />
  </head>
  <body>
    <h1 id="title" class="btn">Hi this is my first test</h1>
  </body>
  <script type="text/javascript" src="test.js"></script>
</html>
```

```javascript
const title = document.querySelector("#title");

const CLICKED_CLASS = "clicked";

function handleClick() {
  const hasClass = title.classList.contains(CLICKED_CLASS);
  if (!hasClass) {
    title.classList.add(CLICKED_CLASS);
  } else {
    title.classList.remove(CLICKED_CLASS);
  }
}

function init() {
  title.addEventListener("click", handleClick);
}

init();
```

```css
body {
  background-color: palegoldenrod;
}

.color {
  color: tomato;
}
.clicked {
  color: teal;
}
.btn {
  cursor: pointer;
}
```