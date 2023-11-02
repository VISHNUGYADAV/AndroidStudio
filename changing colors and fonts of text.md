13.	Demonstrate dynamically changing colors and fonts of text on button clicks.

Aim: To design an android app that utilizes GUI components,fonts and colors effectively to create an intuitive and visually appealing user interface for enhanced user engagement
a.	activity_main.xml
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

</androidx.constraintlayout.widget.ConstraintLayout>

b.	MainActivity.java
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
