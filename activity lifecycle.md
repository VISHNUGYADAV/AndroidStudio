2.	Write a program to demonstrate the activity lifecycle of android apps

Aim: To create an android application to understand and manage the activity life cycle,ensuring optimal performance and user experience throughout app interactions.

a.	Acitivity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="178dp"
        android:layout_height="40dp"
        android:layout_centerHorizontal="true"
        android:layout_centerVertical="true"
        android:text="Activity Life Cycle"
        android:textColor="#3cff00"
        android:textSize="20sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="next"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.798"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.717" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Previous"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.182"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.717" />


</androidx.constraintlayout.widget.ConstraintLayout>

b.	MainActivity.java
package com.codedost;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.TextView;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Log.d("Activity_Lifecycle","onCreate invoked");
        Toast.makeText(MainActivity.this,"Created",Toast.LENGTH_SHORT).show();

    }
    @Override
    protected void onStart() {
        super.onStart();
        Log.d("Activity_Lifecycle","onStart invoked");        Toast.makeText(MainActivity.this,"Start",Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onResume() {
        super.onResume();
        Log.d("Activity_Lifecycle","onResume invoked");   Toast.makeText(MainActivity.this,"Resume",Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onPause() {
        super.onPause();
        Log.d("Activity_Lifecycle","onPause invoked");        Toast.makeText(MainActivity.this,"Pause",Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onStop() {
        super.onStop();
        Log.d("Activity_Lifecycle","onStop invoked");        Toast.makeText(MainActivity.this,"Stop",Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d("Activity_Lifecycle","onRestart invoked");       Toast.makeText(MainActivity.this,"Restart",Toast.LENGTH_SHORT).show();
    }
    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d("Activity_Lifecycle","onDestroy invoked");
        Toast.makeText(MainActivity.this,"Destroy",Toast.LENGTH_SHORT).show();
    }

