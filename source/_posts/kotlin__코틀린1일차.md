---
emoji: ๐
categories: language
title: ์ฝํ๋ฆฐ 1 ์ผ์ฐจ
author: ๋ฒ์
date: '2022-03-10 18:00:00'
tags: ๋ธ๋ก๊ทธ
cover: 
description: Simple recoder
---

## ๊ฐ๋จํ Recoder ๋ง๋ค๊ธฐ

์ฑ๋ ์๊ณ  ์ ํ๋ธ๋ ์์ผ๋๊น ์ผ๋จ ๋ฐ์น๊ธฐ๋ก ๋ง๋ค์ด๋ณด๋ฉด์ ๊ฒช์ด ๋ณด๊ธฐ๋ก ํ๋ค. ๋ชธ์ผ๋ก ๊ฒช๋ ๊ฒ์ ์ ๊น๋จน์ง ์๊ธฐ ๋ง๋ จ์ด๋

### MaiActivity.kt

```kotlin

class MainActivity : AppCompatActivity() {

    private var output: String? = null
    private var mediaRecorder: MediaRecorder? = null
    private var state: Boolean = false

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        button_start.setOnClickListener {
            if (ContextCompat.checkSelfPermission(
                    this,
                    android.Manifest.permission.RECORD_AUDIO
                ) != PackageManager.PERMISSION_GRANTED && ContextCompat.checkSelfPermission(
                    this,
                    android.Manifest.permission.WRITE_EXTERNAL_STORAGE
                ) != PackageManager.PERMISSION_GRANTED
            ) {
                //Permission is not granted
                val permissions = arrayOf(
                    android.Manifest.permission.RECORD_AUDIO,
                    android.Manifest.permission.WRITE_EXTERNAL_STORAGE,
                    android.Manifest.permission.READ_EXTERNAL_STORAGE
                )
                ActivityCompat.requestPermissions(this, permissions, 0)
            } else {
                startRecording()
            }
        }
        button_stop.setOnClickListener {
            stopRecording()
        }


    }

    private fun startRecording() {
        //config and create MediaRecorder Object
        val fileName: String = java.util.Date().getTime().toString() + ".mp3"
        output =
            Environment.getExternalStorageDirectory().absolutePath + "/Download/" + fileName //๋ด์ฅ๋ฉ๋ชจ๋ฆฌ ๋ฐ์ ์์น
        mediaRecorder = MediaRecorder()
        mediaRecorder?.setAudioSource((MediaRecorder.AudioSource.MIC))
        mediaRecorder?.setOutputFormat((MediaRecorder.OutputFormat.MPEG_4))
        mediaRecorder?.setAudioEncoder(MediaRecorder.AudioEncoder.AAC)
        mediaRecorder?.setOutputFile(output)

        try {
            mediaRecorder?.prepare()
            mediaRecorder?.start()
            state = true
            Toast.makeText(this, "๋ ์ฝ๋ฉ ์์๋์์ต๋๋ค.", Toast.LENGTH_SHORT).show()
        } catch (e: IllegalStateException) {
            e.printStackTrace()
        } catch (e: IOException) {
            e.printStackTrace()
        }
    }

    private fun stopRecording() {
        if (state) {
            mediaRecorder?.stop()
            mediaRecorder?.reset()
            mediaRecorder?.release()
            state = false
            Toast.makeText(this, "์ค์ง ๋์์ต๋๋ค.", Toast.LENGTH_SHORT).show()
        } else {
            Toast.makeText(this, "๋ ์ฝ๋ฉ ์ํ๊ฐ ์๋๋๋ค.", Toast.LENGTH_SHORT).show()
        }
    }


}
```

- ์๋ฐ๋ ๊ตฌ์ฑ์ด ๋น์ทํ๋ค. ์กฐ๊ณฐ์ฉ ๋ค๋ฅธ ์ ๋

  - ์ฒ์์ด๋ผ ํด๋์ค ์์ ๋ค ๋ฐ์๋๊ณ  ํ๋๋ฐ ๊ธฐ๋ฅ์ด ๋จ์ํด์ ๊ทธ๋ด ํ์๊ฐ ์๊ธฐ๋ํ๊ณ  ๋ค์์ ๋๋ ์ํด๋ณด์

- ์ฝํ๋ฆฐ์ ์์์ ์ฝ๋ก  : ์ผ๋ก ํํํ๋ค
- ์ฝํ๋ฆฐ์ null์ ์๊ฒฉํ๋ฐ ?๋ฅผ ์ฌ์ฉํ๋ฉด null์ ์ธ ์ ์๋ค.
- ์ฝํ๋ฆฐ๊ณผ ์๋๋ก์ด๋ ์๋ช์ฃผ๊ธฐ๋ฅผ ๋ณด๋ฉด ํ๋ก๊ทธ๋จ์ด ์คํ๋๋ฉด onCreate()๋ถํฐ ์์ํ๋ค. ๊ทธ๋์ oncreate ์๋์์ฑ ๋๋ ๊ฑฐ์์
  - oncreate()๋ ์ต์ด 1ํ๋ง ์คํ๋๋ค
  - onstart()
    - ์กํฐ๋นํฐ๊ฐ ํ๋ฉด์ผ๋ก ๋ณด์ผ๋ ์คํ๋๋ ๋ฉ์๋
  - onpause()
    - ์กํฐ๋นํฐ๋ฅผ ๋ ๋๋ ๊ฒฝ์ฐ ์คํ๋๋ ๋ฉ์๋
  - onResume()
    - ์กํฐ๋นํฐ๊ฐ ์์๋๋ฉด ์คํ๋๋ ๋ฉ์๋, onstart ๋ค์์ผ๋ก ์คํ๋จ
  - onStop()
    - ์กํฐ๋นํฐ๊ฐ ํ๋ฉด์ ๋ณด์ด์ง ์์ ๋ ์คํ๋๋ ๋ฉ์๋
  - ondestroy()
    - ์กํฐ๋นํฐ๊ฐ ๋ฉ๋ชจ๋ฆฌ์์ ์ ๊ฑฐ๋  ๋ ์คํ๋๋๋ฉ์๋

![190527_Activity-LifeCycle](https://user-images.githubusercontent.com/37897508/87264079-0c923d00-c4fa-11ea-8065-90195f5db1ea.png)

* Toast๋ ๋ญ๊ณ  ํ๋ ์ ๊น์ฉ ํ์คํธ๋ผ๋๊ฐ ์๋ฆผ์ ๋์ฐ๋ ๊ธฐ๋ฅ์ด๋ค
* ์๋ฐ์ฒ๋ผ ๋ฆฌ์ค๋๋ฅผ ์ด์ฉํด ์์ง์ด๋ค
* ์ฝ๊ฐ ์ฒด๊ฐ์ mvc ๋ชจ๋ธ ๋๋์ด๋ค 
  * Kotlin์์ ์ง  ์ฝ๋๋ฅผ view(activity_main.xml)์ id์ ์ฐ๊ฒฐํ๋ค

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageView2"
        android:layout_width="285dp"
        android:layout_height="473dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:srcCompat="@drawable/record" />

    <Button
        android:id="@+id/button_start"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="100dp"
        android:layout_marginTop="28dp"
        android:text="Start"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView2"
        android:layout_marginLeft="100dp" />

    <Button
        android:id="@+id/button_stop"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="28dp"
        android:layout_marginEnd="100dp"
        android:text="Stop"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/imageView2"
        android:layout_marginRight="100dp" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="52dp"
        android:text="Voice Recorder"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>

```
* ๋ญ ๊ทธ๋ฅ ์๋๋ก์ด๋ ์คํ๋์ค๊ฐ guiํด์ ์ง์ํด์ค์ ์ฝ๊ฒํ๋ค 
* ์ฝํ๋ฆฐ๊ณผ๋ id๋ฅผ ํตํด์ ์ฐ๊ฒฐํ๋ค
* html css ์๊ฐ ๋๋๋ผ
### AndroidManifest.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.test">
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```
* ์ฐ๋ฆฌ๊ฐ ๋ง๋ค ์ฑ(์คํ ํ์ผ)์ ๊ถํ์ ์ง์ ํด์ค๋ค.
* DB ์ ์ ํ๋ ๋๋? ์์ด์ฝ์ ๋ญ ์ธ ๊ฒ์ธ๊ฐ ์ด๋ค ๊ถํ์ด ์๋๊ฐ ํํฐ๋ฅผ ์ ์ฉํ  ๊ฒ์ธ๊ฐ
* manifest์ ๋ฑ๋กํ์ง ์์ผ๋ฉด ํ์ผ๊ฐ ์ฐ๊ฒฐ์ด ์๋๋ค