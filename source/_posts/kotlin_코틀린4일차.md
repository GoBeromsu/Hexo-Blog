---
emoji: ๐
categories: language
title: ์ฝํ๋ฆฐ4์ผ์ฐจ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: 
description:
---

## Time Picker ์ถ๊ฐ

- ๊น๋ํ๊ฒ ์๊ฐ์ ์ค์ ํ๊ธฐ ์ํด time Picker์ ์ด์ฉํ๊ธฐ๋ก ํ๋ค.
  - second๊น์ง ํํ ๊ฐ๋ฅํ๋ ๊ฒ์ ์ํด์ gradle๋ก ๋ชจ๋์ ์ถ๊ฐ๋ก ๋ฐ์๋ค

```xml
implementation 'com.kovachcode:timePickerWithSeconds:1.0.1'
```

```kotlin
        val timePicker = MyTimePickerDialog(
            this,
            MyTimePickerDialog.OnTimeSetListener() { timePicker: TimePicker, hoursOfDay: Int, minute: Int, seconds: Int ->

                timeText.setText(
                     String.format("%02d", hoursOfDay) +
                            ":" + String.format("%02d", minute) +
                            ":" + String.format("%02d", seconds)
                );
            },
            Calendar.HOUR_OF_DAY,
            Calendar.MINUTE,
            Calendar.SECOND,
            true
        )

        timePicker.show()

    }
```

- ์ผ๋จ์ ์คํํ๋ฉด ๋ฉ์ธ ํ๋ฉด์์ ์ค์ ๋ ์๊ฐ์ ์ถ๋ ฅ์ํค๊ฒ ์ค์ ํด ๋์๋ค.
- ํจํค์ง๋ฅผ ๋ฐ๊ธด ํ๋๋ฐ ์ค๋๋๊ธฐ๋ ํ๊ณ  ์๋ฐ ์ฝ๋๋ผ ์ฝํ๋ฆฐ์ผ๋ก ๋ฐ๊ฟ์ ๋ฃ์๋ค.

## Setting๋ ์๊ฐ Countํ๊ธฐ

```kotlin
val timePicker = MyTimePickerDialog(
            this,
            MyTimePickerDialog.OnTimeSetListener() { timePicker: TimePicker, hoursOfDay: Int, minute: Int, seconds: Int ->
                sumOfTime = hoursOfDay * 60 * 60 + minute * 60 + seconds
                var Timer = object : CountDownTimer(sumOfTime!!.toLong(), 100) {
                    override fun onTick(millisUntilFinished: Long) {
                        timeText.setText("${millisUntilFinished} ๋จ์์ต๋๋ค")
                    }

                    override fun onFinish() {
                        Toast.makeText(this@MainActivity, "CountDown Finished.", Toast.LENGTH_SHORT)
                            .show()
                    }
                }
                Timer.start()
            },
            Calendar.HOUR_OF_DAY,
            Calendar.MINUTE,
            Calendar.SECOND,
            true
        )

```

- sumOfTime์ผ๋ก ์,๋ถ,์ด๋ฅผ ์ด๋ก ํ์ฐํด์ ์นด์ดํธ ๋ค์ด ํ๋๋ก ํ๋ค.
  - ์๋๋ฉด ์ผ๋จ ๊ณํ์ด Graphic์ผ๋ก ์ด๋ฅผ ํผ์ผํธ๋ก ๊ตฌํํ  ์๊ฐ์ด๋ผ ์ผ๋ถ๋ฌ ํฉ์ณค๋ค.
- CounDownTimer๋ฅผ ์ด์ฉํ๋ค
  - onTick์ ํฑ๋น ํ  ํ๋
  - onFinish๋ ํ์ด๋จธ ๋๋ฌ์ ๋ ํ  ํ๋์ด๋ค

## functijon ๋ถํ 

- ์ญ์ ์๋ฐ๋ ์ฝํ๋ฆฐ์ด๋ ๊ฐ์ฒด ์งํฅ์ด ์ต๊ณ  ์๋๊ฐ
  - ๋๋ฒ๊น ํ  ๋ ๊ท์ฐฎ๊ธฐ๋ ํ๊ณ  function์ ๋๋ด๋ค.

### SetTimer

```kotlin
    fun setTimer() {
        val timePicker = MyTimePickerDialog(
            this,
            MyTimePickerDialog.OnTimeSetListener() { timePicker: TimePicker, hoursOfDay: Int, minute: Int, seconds: Int ->
                sumOfTime = hoursOfDay * 60 * 60 + minute * 60 + seconds
                storeTime(sumOfTime)
                startTimer()
            },
            Calendar.HOUR_OF_DAY,
            Calendar.MINUTE,
            Calendar.SECOND,
            true
        )
        timePicker.show()
    }
```

- timePicker๋ฅผ ์ด์ฉํ๊ณ  ์๊ฐ ์ค์  ๊ด๋ จ ๊ธฐ๋ฅ์ ๋ชจ์๋์๋ค.

### startTimer

```kotlin

    fun startTimer() {

        var countDownTime = sumOfTime
        timerTask = timer(period = 1000) {

            countDownTime--

            runOnUiThread { timeText.setText("$countDownTime") }
        }
    }
```

- 1์ด์ฉ COUNTDOWNํ๋ ํจ์์ด๋ค.
- kotlin์์ ์ง์ํ๋ timer๋ฅผ ์ด์ฉํ๋ค.

### storeTime

- sumOfTime๋ผ๋ ์ ์ญ ๋ณ์์ ์๊ฐ์ ์ ์ฅํด๋๋ค.
  - ๋์ค์ DB๊น์ง ์ธ ๋จ๊ณ๊ฐ ์จ๋ค๋ฉด ๋ฐ๊ฟ ์๊ฐ์ด๋ค
- ํ์คํ ๊น๊ผผํ๊ตฐ

```kotlin
    fun storeTime(Time: Int): Int {
        sumOfTime = Time
        Toast.makeText(this@MainActivity, "${sumOfTime}์ storeTime์์ ํธ์ถ๋จ", Toast.LENGTH_SHORT)
            .show()
        return sumOfTime
    }
```
## ์ถ๊ฐํด์ผํ  ๊ธฐ๋ฅ

* Timer ๊ธฐ๋ฅ ์์ฑ
  * stop
  * initailize
  * ์นด์ดํธ๊ฐ ์์๊ฐ ๋์ง ์๋๋ก ์ค์ 
* ๊ทธ๋ํฝ ๊ธฐ๋ฅ ์ค์ 

## ํ ์ค๋์ ํ๊ธฐ

* ์๊ฐ๋ณด๋ค ๊ตฌํ ์๋๊ฐ ๋น ๋ฅด๋ค
* DB๊น์ง ์ถ๊ฐํด ๋ณผ๊น?
* ์ธ๋ ๋ง๋ค๊ณ  ๋ค๋ฅธ ๊ฒ๋ ๋ง๋ค์ด๋ณด์
* ํ๋ค๋ณด๋ ์ ์  ์๋๊ฐ ๋ถ๋ค
* ํ๋ฃจ์ 2์๊ฐ ์ ๋ ๊ด์ฐฎ๋ค ์ทจ๋ฏธ๋ ์ญ์ ์ฝ๋ฉ์ธ๊ฐ