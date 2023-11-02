8.	Develop a simple calculator in android

Aim: To develop a Simple Android Application for Native Calculator.

a.	Activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"

    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Simple calculator"
        android:textAllCaps="true"
        android:textFontWeight="900"
        android:fontFamily="sans-serif-black"
        android:textSize="24sp"
        android:textColor="#f00000"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.05" />

    <EditText
        android:id="@+id/num1"
        android:layout_width="129dp"
        android:layout_height="60dp"
        android:background="#4E86B2"
        android:ems="10"
        android:textAlignment="center"
        android:text="0"
        android:inputType="number"
        android:padding="3dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.812"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.291" />

    <EditText
        android:id="@+id/num2"
        android:layout_width="132dp"
        android:layout_height="65dp"
        android:background="#4E86B2"
        android:ems="10"
        android:text="0"
        android:textAlignment="center"
        android:inputType="number"
        android:padding="3dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.204"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.291" />

    <Button
        android:layout_width="55dp"
        android:layout_height="50dp"
        android:text="+"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.238"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.513"
        android:id="@+id/addbtn"/>

    <Button
        android:layout_width="55dp"
        android:layout_height="50dp"
        android:text="-"
        android:id="@+id/subbtn"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.441"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.513" />

    <Button
        android:layout_width="55dp"
        android:layout_height="50dp"
        android:text="*"
        android:id="@+id/mulbtn"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.643"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.513" />

    <Button
        android:layout_width="55dp"
        android:layout_height="50dp"
        android:text="/"
        android:id="@+id/divbtn"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.828"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.513" />



    <TextView
        android:id="@+id/num3"
        android:layout_width="54dp"
        android:layout_height="46dp"
        android:background="#7AA3C4"
        android:padding="8dp"
        android:text="0"
        android:textSize="20sp"
        android:textAlignment="center"
        android:gravity="center"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.792" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="The calculated answer is"
        android:textSize="18sp"
        android:fontFamily="sans-serif-black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.503"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.714" />


</androidx.constraintlayout.widget.ConstraintLayout>

b.	MainActivity.xml
package com.example.myapplication;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.text.TextUtils;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {

    EditText num1, num2;
    TextView num3;
    Button add,sub,mul,div;

    float a,b,c;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        num1= findViewById(R.id.num1);
        num2 = findViewById(R.id.num2);
        num3 = findViewById(R.id.num3);
        add = findViewById(R.id.addbtn);
        sub = findViewById(R.id.subbtn);
        mul = findViewById(R.id.mulbtn);
        div = findViewById(R.id.divbtn);
        add.setOnClickListener(this::onClick);
        sub.setOnClickListener(this::onClick);
        mul.setOnClickListener(this::onClick);
        div.setOnClickListener(this::onClick);

    }
    @Override
    public void onClick(View view){
        float a = 0;
        float b = 0;
        float result = 0;
        String oper = "";
        if (TextUtils.isEmpty(num1.getText().toString()) || TextUtils.isEmpty(num2.getText().toString()))
            return;
        a = Float.parseFloat(num1.getText().toString());
        b = Float.parseFloat(num2.getText().toString());
        int id = view.getId();
        if (id == R.id.addbtn) {
            oper = "+";
            result = a + b;
        } else if (id == R.id.subbtn) {
            oper = "-";
            result = a - b;
        } else if (id == R.id.mulbtn) {
            oper = "*";
            result = a * b;
        } else if (id == R.id.divbtn) {
            oper = "/";
            result = a / b;
        }
        // form the output line
        num3.setText(Float.toString(result));
    }
}
