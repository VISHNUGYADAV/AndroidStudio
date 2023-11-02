4.	Write a program to demonstrate explicit and implicit intents

Aim: To Build an Android intent-based app that allows users to seamlessly share content between different apps and enhance cross-app functionality

a.	Activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/counter_disp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="#4587EC"
        android:padding="8dp"
        android:paddingHorizontal="12dp"
        android:text="0"
        android:textColor="@color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.526" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="#4587EC"
        android:padding="4dp"
        android:id="@+id/varcolortext"
        android:text="Click the buttons below to count"
        style="@style/constrain"
        android:textColor="@color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.446" />


    <Button
        android:id="@+id/btn_prev"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="countPrev"
        style="@style/constrain"
        android:text="Previous"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.24"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.635" />

    <Button
        android:id="@+id/btn_next"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="countNext"
        style="@style/constrain"
        android:text="Next"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.765"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.635" />

    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:background="#000080"
        android:onClick="changeTextColor"
        android:text="Change Color"
        style="@style/constrain"
        android:fontFamily="sans-serif-black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.329" />

    <Button
        android:id="@+id/switchsecond"
        style="@style/constrain"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:onClick="countPrev"
        android:text="switch activity"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.778"
        android:textColor="@color/black"
        android:backgroundTint="#9ddef1"/>

</androidx.constraintlayout.widget.ConstraintLayout>

b.	Second_activity.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout android:layout_width="match_parent"
    android:layout_height="match_parent"
    xmlns:tools="http://schemas.android.com/tools"
    tools:context=".SecondActivity"
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:gravity="center">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Demonstration of intents and activity switching"
        android:paddingVertical="18dp"
        android:textSize="18sp"

        >

    </TextView>
    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginVertical="18sp"
        android:text="switch back to main"
        android:id="@+id/switchbtn"

        >

    </Button>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginVertical="18sp"
        android:text="implicit intent"
        android:onClick="implicitBtnCall"
        android:id="@+id/impButton"

        >

    </Button>



</LinearLayout>

c.	MainActivity.java
package com.example.counterapp;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.content.res.ColorStateList;
import android.graphics.Color;
import android.util.Log;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;


public class MainActivity extends AppCompatActivity {

    TextView counter;
    TextView colorful_text;
    private int count_var = 0;
    private int[] colors = {Color.BLACK, Color.BLUE, Color.GREEN, Color.RED};
    private int initial_color = 0;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        counter = findViewById(R.id.counter_disp);
        Button switch_second = findViewById(R.id.switchsecond);
        switch_second.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), SecondActivity.class);
                startActivity(intent);

            }
        });

    }
    public void countNext(View view){
        count_var++;
        counter.setText(Integer.toString(count_var));
        //counter.setText(Integer.parseInt(counter.getText().toString())+1);
    }
    public void countPrev(View view){
        //counter.setText(Integer.parseInt(counter.getText().toString())-1);
        count_var--;
        counter.setText(Integer.toString(count_var));
    }

    public void changeTextColor(View view){
        colorful_text = findViewById(R.id.varcolortext);
        colorful_text.setTextColor(colors[initial_color]);
        initial_color = (initial_color+1) % colors.length;
    }
}

d. SecondActivity.java
package com.example.counterapp;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;

import androidx.appcompat.app.AppCompatActivity;

import java.net.URI;

public class SecondActivity extends AppCompatActivity {
    Button switchMain;
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.second_activity);
        switchMain = findViewById(R.id.switchbtn);

        switchMain.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(getApplicationContext(), MainActivity.class);
                startActivity(intent);
            }
        });
    }

    public void implicitBtnCall(View view){
        Intent intent = new Intent(Intent.ACTION_VIEW);
        intent.setData(Uri.parse("https://loyola-website.vercel.app/"));
        startActivity(intent);
    }
}
d.	Manifest.xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.CounterApp"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:launchMode="singleInstance">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name=".SecondActivity"
            android:exported="true"
            android:launchMode="singleInstance">

        </activity>
    </application>

</manifest>

e.	Output
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.CounterApp"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true"
            android:launchMode="singleInstance">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name=".SecondActivity"
            android:exported="true"
            android:launchMode="singleInstance">

        </activity>
    </application>

</manifest>
