<table>
  <tr>
    <th colspan="2">DATA MAHASISWA</th>
  </tr>
  <tr>
    <td>Nama</td>
    <td>Roswanda Nuraini</td>
  </tr>
  <tr>
    <td>NIM</td>
    <td>312210328</td>
  </tr>
  <tr>
    <td>Kelas</td>
    <td>TI.22.A3</td>
  </tr>
  <tr>
    <td>Mata Kuliah</td>
    <td>Pemrograman Mobile</td>
  </tr>
</table>

# <p align="center">Implicit Intents</p>

![tugaspmimplisit](https://github.com/roswanda11/Implicit-Intent/assets/115516632/71c62739-52cd-4a84-aa67-284bb4694c4b)

# Langkah-langkah

Untuk membuat aplikasi Android dengan fitur splash screen dan tujuh project yang dapat diakses melalui metode eksplicit dan implisit intent, kita dapat mengikuti langkah-langkah sebagai berikut:

# 1. Membuat Splash Screen Layout ```(activity_splash_screen.xml)```:

Buat file layout untuk splash screen, misalnya ```activity_splash_screen.xml```. Dalam contoh ini, kita akan menampilkan logo masing-masing individu.

      <?xml version="1.0" encoding="utf-8"?>
      <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:background="@color/black"
          tools:content=".SplashScreen">
      
          <LinearLayout
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_centerInParent="true"
              android:gravity="center"
              android:orientation="vertical">
      
              <ImageView
                  android:id="@+id/logo"
                  android:layout_width="350dp"
                  android:layout_height="wrap_content"
                  android:adjustViewBounds="true"
                  android:src="@drawable/logowanda" />
      
          </LinearLayout>
      
      </RelativeLayout>

![Screenshot (513)](https://github.com/roswanda11/Implicit-Intent/assets/115516632/49f5ef7f-8472-47fb-ae32-71c200f11fdb)

Ini logo yang telah saya siapkan :

![logowanda](https://github.com/roswanda11/Implicit-Intent/assets/115516632/a59cdac0-6ec7-46e3-ac8a-5b68580f4b0e)

# 2. Membuat SplashScreen ```(SplashScreen.java)```:

Buat kelas untuk menangani splash screen dan pindah ke MainActivity setelah beberapa detik.

      package com.hellotoast;
      
      import android.content.Intent;
      import android.os.Bundle;
      import android.os.Handler;
      import android.view.View;
      
      import androidx.appcompat.app.AppCompatActivity;
      
      public class SplashScreen extends AppCompatActivity {
      
          @Override
          protected void onCreate(Bundle savedInstanceState) {
              super.onCreate(savedInstanceState);
              setContentView(R.layout.activity_splash_screen);
      
              View decorView = getWindow().getDecorView();
              // Hide the status bar.
              int uiOptions = View.SYSTEM_UI_FLAG_FULLSCREEN;
              decorView.setSystemUiVisibility(uiOptions);
              // Hide ActionBar
              if (getSupportActionBar() != null) {
                  getSupportActionBar().hide();
              }
              new Handler().postDelayed(new Runnable() {
                  @Override
                  public void run() {
                      startActivity(new Intent(SplashScreen.this, MainHomePage.class));
                      finish();
                  }
              }, 2000); // Ubah delayMillis menjadi 2000
          }
      }

# 3. Menambahkan button pada ```activity_home.xml``` yang sudah disiapkan

Di sini namanya ```activity_home.xml```, anda bisa menyesuaikan dengan nama xm anda

      <?xml version="1.0" encoding="utf-8"?>
      <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
          xmlns:tools="http://schemas.android.com/tools"
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:layout_marginStart="0dp"
          android:layout_marginEnd="0dp"
          android:background="@color/pink"
          android:gravity="center_vertical"
          android:orientation="vertical"
          tools:context=".SplashScreen">
      
          <Button
              android:id="@+id/btnHello"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Hello Toast"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnCount"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Count"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnSianida"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Kasus Sianida"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnTwoActivity"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:text="Project Two Activity"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      
          <Button
              android:id="@+id/btnAlarm"
              android:layout_width="match_parent"
              android:layout_height="wrap_content"
              android:layout_marginStart="50dp"
              android:layout_marginEnd="50dp"
              android:onClick="createAlarm"
              android:text="Project Set Alarm"
              android:textStyle="bold"
              android:textColor="@color/white"/>
      </LinearLayout>

![Screenshot (514)](https://github.com/roswanda11/Implicit-Intent/assets/115516632/ae123f5c-ce7c-4fa5-a198-1d3a6885794a)

# 4. Lalu atur MainActivity (MainActivity.java)

Karena saya sudah membuat activity sebelumnya untuk masing-masing project maka tinggal edit mainactivitynya tidak usah bikin activity satu-satu lagi: Di sini, kita akan menampilkan daftar project dan menangani eksplicit intent. nama saya MainHomePage.java, kalian bisa menyesuaikan dengan nama kalian.

      package com.hellotoast;
      
      import android.content.Intent;
      import android.os.Bundle;
      import android.provider.AlarmClock;
      import android.view.View;
      import android.widget.Button;
      
      import androidx.appcompat.app.AppCompatActivity;
      
      import java.util.ArrayList;
      
      public class MainHomePage extends AppCompatActivity {
      
          Button btnHello;
          Button btnCount;
          Button btnSianida;
          Button btnTwoActivity;
      
          @Override
          protected void onCreate(Bundle savedInstanceState) {
              super.onCreate(savedInstanceState);
              setContentView(R.layout.activity_home);
      
              setLayout();
              setKlik();
          }
      
          void setLayout() {
              btnHello = findViewById(R.id.btnHello);
              btnCount = findViewById(R.id.btnCount);
              btnSianida = findViewById(R.id.btnSianida);
              btnTwoActivity = findViewById(R.id.btnTwoActivity);
          }
      
          void setKlik() {
              btnHello.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intenthello = new Intent(MainHomePage.this, MainActivity.class);
                      startActivity(intenthello);
                  }
              });
      
              btnCount.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intentcount = new Intent(MainHomePage.this, MainToast.class);
                      startActivity(intentcount);
                  }
              });
      
              btnSianida.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intentsianida = new Intent(MainHomePage.this, MainScrollice.class);
                      startActivity(intentsianida);
                  }
              });
      
              btnTwoActivity.setOnClickListener(new View.OnClickListener() {
                  @Override
                  public void onClick(View view) {
                      Intent intenttwoactivity = new Intent(MainHomePage.this, MainFirstActivity.class);
                      startActivity(intenttwoactivity);
                  }
              });
          }
      
          public void createAlarm(View view) {
              ArrayList<Integer> alarmDays = new ArrayList<>();
              alarmDays.add(2);
              alarmDays.add(3);
              alarmDays.add(4);
              Intent intent = new Intent(AlarmClock.ACTION_SET_ALARM)
                      .putExtra(AlarmClock.EXTRA_DAYS, alarmDays)
                      .putExtra(AlarmClock.EXTRA_MESSAGE, "Testing")
                      .putExtra(AlarmClock.EXTRA_HOUR, 7)
                      .putExtra(AlarmClock.EXTRA_MINUTES, 30)
                      .putExtra(AlarmClock.EXTRA_VIBRATE, false)
                      .putExtra(AlarmClock.EXTRA_RINGTONE, "VALUE_RINGTONE_SILENT");
              if (intent.resolveActivity(getPackageManager()) != null) {
                  startActivity(intent);
              }
          }
      }

# 5. berikutnya adalah untuk mengedit file AndroidManifest.xml untuk aplikasi Android dengan SplashScreenActivity dan MainActivity yang akan memulai tujuh project menggunakan eksplicit dan implisit intent:

Di sini saya sudah menyiapkan kodingannya:

      <?xml version="1.0" encoding="utf-8"?>
      <manifest xmlns:android="http://schemas.android.com/apk/res/android">
      
          <uses-permission android:name="com.android.alarm.permission.SET_ALARM" />
      
          <application
              android:allowBackup="true"
              android:icon="@drawable/logowanda"
              android:label="Rosé"
              android:roundIcon="@drawable/logowanda"
              android:supportsRtl="true"
              android:theme="@style/Theme.HelloToast">
      
      
              <activity
                  android:name=".SplashScreen"
                  android:exported="true">
                  <intent-filter>
                      <action android:name="android.intent.action.MAIN" />
                      <category android:name="android.intent.category.LAUNCHER" />
                  </intent-filter>
              </activity>
      
              <activity android:name=".MainHomePage"></activity>
              <activity android:name=".MainActivity"></activity>
              <activity android:name=".MainScrollice"></activity>
              <activity android:name=".MainToast"></activity>
              <activity android:name=".MainFirstActivity"></activity>
      
          </application>
      </manifest>

# Output

# ic launcer
