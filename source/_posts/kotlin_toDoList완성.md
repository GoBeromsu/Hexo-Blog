---
emoji: ๐
categories: language
title: toDoList์์ฑ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: https://user-images.githubusercontent.com/37897508/81902661-77f38780-95fb-11ea-8441-d6e2127ffd5b.png
description: project ์ ๋ฆฌ
---

# ์ฝ๋ ๋ฆฌ๋ทฐ

## What you learend in This Project

- Javascript, HTML, CSS ๊ณผ ์กฐ๊ณฐ ์นํด์ก๋ค
- Jascript์ ๊ธฐ๋ณธ ๋์์ ์๊ฒ ๋ฌ๋ค
  - ์ด ๋์์ ์ด๋ฐ ๋๋์ผ๋ก ์์ง์ด๊ตฌ๋
  - ์ ์ฐ๋ ๊ตฌ๋
  - sexyํ ์ธ์ด๊ตฐ

## html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />

    <link rel="stylesheet" href="index.css" />
    <title>Test</title>
  </head>
  <body>
    <div class="js-clock">
      <h1>00:00</h1>
    </div>
    <form class="js-form form">
      <input type="text" placeholder="what is your name?" />
    </form>
    <h4 class="js-greetings greetings"></h4>
    <form class="js-toDoForm">
      <input type="text" placeholder="write a todo" />
    </form>
    <ul class="js-toDoList" id="toDoList"></ul>
    <spanc class="js-weather"></spanc>
  </body>
  <script src="clock.js"></script>
  <script src="todo.js"></script>
  <script src="greeting.js"></script>
  <script src="bg.js"></script>
  <script src="weather.js"></script>
</html>
```

## javascript

### greeting.js

```javascript
const form = document.querySelector(".js-form"); // js-form ํด๋์ค๋ฅผ ๋ฐ์์ด
const input = form.querySelector("input"); // input tag ๋ค์ ๋ฐ์์ด
const greeting = document.querySelector(".js-greetings"); //  js-greetings ํด๋์ค๋ฅผ ๋ฐ์์ด

const USER_LS = "currentUser"; // User ํ์ธ์ ์ํ ๋ณ์
const SHOWING_CN = "showing"; // css ๋ณํ์ ์ํ ๋ณ์

function saveName(text) {
  // local storage์ currentUser๋ก saveName ํจ์์ ์๋ ฅ๋ฐ์ ํ์คํธ๋ฅผ ์ ์  ์ด๋ฆ์ผ๋ก ์์ 
  localStorage.setItem(USER_LS, text);
}

function handleSubmit(event) {
  event.preventDefault(); // placeholder ์ด๋ฒคํธ ๋ง๊ธฐ
  const currentValue = input.value; // ํ์ฌ ์๋ ฅ๋ ๊ฐ ์ ์ฅ
  paintGreeting(currentValue); // input ๊ฐ ์ธ์๋ก ๋ณด๋ด๊ธฐ
  saveName(currentValue); // ํ์ฌ ๊ฐ์ local storage์ ์ ์ฅ
}

function askForName() {
  form.classList.add(SHOWING_CN);
  form.addEventListener("submit", handleSubmit);
}

function paintGreeting(text) {
  form.classList.remove(SHOWING_CN); // ๊ธฐ์กด์ form์ input์ด ์๋ณด์ด๊ฒํจ
  greeting.classList.add(SHOWING_CN); // js-greeting h4 ํ๊ทธ๊ฐ ๋ณด์
  greeting.innerText = `Hello ${text}`; // js-greeting h4 ํ๊ทธ์ text์๋ ฅ
}

function loadName() {
  const currentUser = localStorage.getItem(USER_LS); // ์ ์ฅ๋ ์ ์  ์ด๋ฆ์ ๋ถ๋ฌ์จ๋ค

  if (currentUser === null) {
    askForName(); // currentUser๊ฐ ๋น์ด์๋ค๋ฉด askForName ํธ์ถ
  } else {
    paintGreeting(currentUser); // currentuser๊ฐ ์๋ค๋ฉด paintGreeting ํธ์ถ
  }
}

function init() {
  loadName();
}

init();
```

### bg.js

```javascript
const body = document.querySelector("body"); // body ํ๊ทธ์ ์ ๊ทผํ๋ค

const IMG_NUMBER = 4; // ์ด๋ฏธ์ง ์ต๋ ๊ฐฏ์

function paintImage(imgNumber) {
  // ๋ฐฐ๊ฒฝ ์ด๋ฏธ์ง๋ฅผ ์น ํ๋ ํจ์
  const image = new Image(); // ์ด๋ฏธ์ง ๊ฐ์ฒด๋ฅผ ์์ฑ
  image.src = `images/${imgNumber + 1}.jpg`; // ์ด๋ฏธ์ง ์์ค๋ก images ํ์ ํด๋ ์ด๋ฏธ์ง๋ค์ ์ถ๊ฐ
  image.classList.add("bgImage"); //   ์ด๋ฏธ์ง๋ฅผ bgImage๋ผ๋ ํด๋์ค๋ก ์ถ๊ฐํ๋ค
  body.prepend(image); // bgImage ํด๋์ค๋ฅผ ๋ฐ๋์ ์ถ๊ฐ
}

function getRandom() {
  // ๋๋ค์ผ๋ก ์ซ์๋ฅผ ๋ฐํํ๋ ํจ์
  const number = Math.floor(Math.random() * IMG_NUMBER);
  return number;
}

function init() {
  const randomNumber = getRandom();
  paintImage(randomNumber);
}

init();
```

### wether.js

```javascript
const COORDS = "coords";
const API_KEY = "60b305147a7e043321d283d3c83b4fa2";
const weather = document.querySelector(".js-weather"); //js-weather class๋ฅผ ๋ถ๋ฌ์ด

function getWeather(latitude, longitude) {
  fetch(
    `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=${API_KEY}&units=metric`
  )
    .then(function (json) {
      return json.json(); // json์ text๋ก ์ฝ์ด์ด??
    })
    .then(function (json) {
      console.log(json);
      const temperture = json.main.temp; // json์์ ์จ๋ ์ ์๋ฅผ ๊ฐ์ ธ์จ๋ค
      const place = json.name; // json์์ ์์น ์ ๋ณด๋ฅผ ๊ฐ์ ธ์จ๋ค
      weather.innerText = `${temperture}'C @${place}`;
    });

  // fetch๋ก url๋ก api๋ฅผ ๋ฐ์์จ๋ค
  //
}

function saveCoords(coordsObj) {
  localStorage.setItem(COORDS, JSON.stringify(coordsObj)); // local storage์ COORDS๋ ๋ณ์์ coordsObj๋ฅผ json์ผ๋ก ๋ฐ๊พธ์ด ์ ์ฅ
}

function handleGeoSuccess(position) {
  console.log("success");
  const latitude = position.coords.latitude; //api์์ ์์น ์ ๋ณด๋ฅผ ๊ฐ์ ธ์ด
  const longitude = position.coords.longitude;

  const coordsObj =
    // latitude longitude ๊ฐ์ฒด ์ ์ธ
    {
      latitude,
      longitude,
    };
  saveCoords(coordsObj);
  getWeather(latitude, longitude);
}
function handleGeoError() {
  console.log("error");
}
function askForCoords() {
  navigator.geolocation.getCurrentPosition(handleGeoSuccess); // handleGeoSuccess๋ฅผ ์ฝ๋ฐฑํจ์๋ก ํ์ฌ ์์น๋ฅผ ๋ฐ์์ด
}

function loadCoords() {
  const loadedCoords = localStorage.getItem(COORDS); // location ์ ๋ณด๋ฅผ ๋ฐ์์ด
  if (loadedCoords === null) {
    askForCoords(); // ์ ๋ณด๊ฐ ์๋ค๋ฉด askForCoords๋ก ์ด๋
  } else {
    const parseCoords = JSON.parse(loadedCoords); //json parse
    getWeather(parseCoords.latitude, parseCoords.longitude); // location  ์ ๋ณด ๋ฐํ์ผ๋ก ๋ ์จ๋ฅผ ๋ฐ์์ด
  }
}

function init() {
  loadCoords();
}

init();
```

### clock.js

```javascript
const clockContainer = document.querySelector(".js-clock"); // .js-clock์ index.html์์ ๋ถ๋ฌ์จ๋ค
const clockTitle = clockContainer.querySelector("h1"); // .js-clock์ child์ธ h1 tag๋ฅผ ๋ถ๋ฌ์จ๋ค

function getTime() {
  // ํ์ฌ ์๊ฐ์ ๊ฐ์ ธ์ค๋ ํจ์
  clockTitle.innerText = ` ${hours < 10 ? `0${hours}` : hours} : ${
    minutes < 10 ? `0${minutes}` : minutes
  } : ${seconds < 10 ? `0${seconds}` : seconds}`;

  // ` `์ ํตํด shell ์ฒ๋ผ ๋ณ์๋ฅผ ๋ฐ์์ค๊ณ  ์ธ ์ ์์
  // ์ผํญ ์ฐ์ฐ์๋ก ์ ๋ถ ์ด๊ฐ 10์ดํ ์ผ๊ฒฝ์ฐ 0์ถ๊ฐ
}

function init() {
  setInterval(getTime, 1);
}

init();
```
