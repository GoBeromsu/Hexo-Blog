---
emoji: ๐
categories: language
title: ์ฝํ๋ฆฐ5์ผ์ฐจ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover:
description:
---

# 2์ฃผ๊ฐ ์ด๋ฐ ๋๋ง๊ฐ๋?

7์ ๋ง์ ์ ๋ณด์ฒ๋ฆฌ ์ฐ์๊ธฐ์ฌ ์ํ์ด ์์ด์ ๊ทธ๊ฑฐ ๋นก ์ค๋นํด์ผ๊ฒ ๋ค๋ ์๊ฐ์ ๊ณ์ ๊ทธ ๊ณต๋ถ๋ง ํ๋ค. ๋ญ ์ฌ์ค ํ๊ณ์ธ๊ฑฐ ๊ฐ๊ธดํ์ง๋ง ๊ฒฐ๋ก ์ ์ผ๋ก ์ ๋ณด์ฒ๋ฆฌ ๋ถ์์ผ๋๊น ํํ ์๋ค! ๊ทธ๋ฌ๊ณ ๋ ์ค๊ฐ์ค๊ฐ ์ ํญ์ด๋ ๊ตฌ๊ธ๋ง์ผ๋ก ์ด๋ป๊ฒ ํ๋ฉด ๋ ์๋ง๋ค๊น? ์ฐพ์๋ณด๋ค๋ณด๋ ์๊ฐ์ด ํ๊ฐ๋ฒ๋ ธ๋ค

# ์งํ ๊ณผ์ 

1.0 ๋ฒ ํ ๋ฒ์ ?์ ๋ค ๋ง๋ค์๋ค. ๋ด๊ฐ ์ํ๋๊ฑด ๊ฐ๋จํ๊ฒ ๊ทธ๋ฅ ์นด์ดํธ ํ์ด๋จธ ์๊ฐ ๊ฒฝ๊ณผ๋ฅผ ๊ทธ๋ํฝ์ผ๋ก ๋ณด์ฌ์ฃผ๊ณ  ์ถ์๋ค.

## ๋ญ ๋ฐฐ์ ๋?

* ์๋๋ก์ด๋ ์คํ๋์ค๋ ์นํด์ก๋ค
  * ์ด๋ ๊ฒ ๋์๊ฐ๋ค. ์ด๋ฐ ๊ธฐ๋ฅ์ด ์๋ค(๋จ์ถํค๋ฅผ ์ข ๋ ์ธ์ ๋ค๋๊ฐ, ๋ฌ๊ธํฌ ์ค๋ฅ์ ์์ธ)
* ํ์ผ ๊ตฌ์กฐ๋ ์นํด์ก๋ค.
  * maven, gradle ์๋ฆฌ ๊ฐ์ ๊ฒ๋ค
* ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ ์ข ๋์๋ดค๋ค.
  * ๊นํ๋ธ ๋์๋ค๋๋ฉด์ ์ฝ๋๋ฅผ ๋ณด๊ณ  ์ฐธ๊ณ ํ๋ค.
  * ๋ผ์ด๋ธ๋ฌ๋ฆฌ๋ฅผ ๋ฐ์์์ ์ข ์จ๋ดค๋ค.
* OOP์ ๋ํ ๊ฐ์ฆ์ด ์๊ฒผ๋ค.
  * ๋ด๊ฐ ๋ด๋ ์ง๊ธ ์ง  ์ฝ๋ ๋์ฅํ์ด๋ค ํด
  * ์ด๋๋ก ํ์ํ๋ฉด ๋๋ฆฌ๋๋ ๊ฑฐ์ผ ๋ถ๋ฐํ์

## ์ธ๋ถ ๊ธฐ๋ฅ

### TIMER

```kotlin
    fun startTimer(hours: Int, minutes: Int, seconds: Int) {

        var seconds = seconds
        var minutes = minutes
        var hours = hours

        timerTask = timer(period = 1000) {
            sumOfTime--
            seconds--
            if (seconds < 0) {
                minutes--
                seconds = 59
            }
            if (minutes < 0) {
                hours--
                minutes = 59
            }

            var timerSeconds = seconds.toString()
            var timerMinutes = minutes.toString()
            var timerHours = hours.toString()


            if (seconds < 10) {
                timerSeconds = "0$seconds"
            }
            if (minutes < 10) {
                timerMinutes = "0$minutes"
            }
            if (hours < 10) {
                timerHours = "0$hours"
            }
            runOnUiThread {

                timeText.setText("$timerHours : $timerMinutes : $timerSeconds")
            }
            if (sumOfTime==0){
                timerTask!!.cancel()
                timeText.setText("00 : 00 : 00")
            }
        }

        btn_reset.setOnClickListener() {
            timerTask!!.cancel()
            sumOfTime = 0
            setTimePicker()
        }

    }
```
* 3ํญ ์ฐ์ฐ์๋ฅผ ์จ์ ๋ ์ฝ๋๋ฅผ ์ค์ด๊ณ  ์ถ์๋ฐ ์ฝํ๋ฆฐ์ ์๋ค๋ค? ๋ญ ๋์  ๊ตณ์ด์ ์์ญ์ด๊ธดํ๋๋ผ
* ์์ฌ์ด๋๋ก 00:00:00 ํฌ๋งท์ ๋ง์ถ๊ณ  ์ถ์ด์ string์ผ๋ก ๋ฐ๊ฟ์ ์ ์ฉํ๋ค.
* ์๋ reset ๊ธฐ๋ฅ๋ ๋ง๋ค์๋๋ฐ ๋ง์ ์๋ ๋ค.
  * ์ ๊ฒ ์ ์ ๊ธฐ ์์ด์ผ ํ๋ ์ถ์๋ฐ timer ์ธ์คํด์ค๋ฅผ ์๋ชป๋ง๋ค์๋ค. ๋ด์ ์ด๋ ๊ฒ ์ํ ๊ฑฐ๋ค


### ProgressBar

```xml
    <com.sfyc.ctpv.CountTimeProgressView
        android:id="@+id/countTimeProgressView"
        android:layout_width="match_parent"
        android:layout_height="443dp"
        android:paddingTop="30dp"
        app:backgroundColorCenter=" #FFFFFF"
        app:borderBottomColor="#000000"
        app:borderDrawColor="#CDC8EA"
        app:borderWidth="5dp"
        app:countTime="5000"
        app:markBallColor="#002FFF"
        app:markBallFlag="true"
        app:markBallWidth="3dp"
        app:startAngle="0"
        app:textStyle="jump"
        app:titleCenterColor="#000000"
        app:titleCenterSize="40dp"
        app:titleCenterText="" />

```

```kotlin
    fun setProgressBar() {
        with(countTimeProgressView) {
            startAngle = 0f
            countTime = 6000L
            borderWidth = 7f
            borderBottomColor = Color.GRAY
            borderDrawColor = Color.BLACK
            backgroundColorCenter = Color.WHITE
            markBallFlag = true
            markBallWidth = 9f
            markBallColor = Color.BLUE
            titleCenterText = "Time is Gold"
            titleCenterTextColor = Color.BLACK
            titleCenterTextSize = 50f
            addOnEndListener(object : CountTimeProgressView.OnEndListener {
                override fun onAnimationEnd() {
                    Toast.makeText(this@MainActivity, "Count Finished", Toast.LENGTH_SHORT).show()
                }

                override fun onClick(overageTime: Long) {
                    if (countTimeProgressView.isRunning) {
                        countTimeProgressView.cancelCountTimeAnimation()
                        Log.e("overageTime", "overageTime = " + overageTime)
                    } else {
                        countTimeProgressView.startCountTimeAnimation()
                    }
                }
            })
        }
        countTimeProgressView.startCountTimeAnimation()
    }
```
* xml์์ ๊ธฐ๋ณธ ์ธํ์ ํ์ง๋ง ์ฝํ๋ฆฐ์์ ์ฌ์ ์ ํ  ์ ์๋ค. 


