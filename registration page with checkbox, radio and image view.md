5.	Develop a registration page with checkbox, radio and image view.

Aim: To demonstrate the usage of Registration page with checkbox, radio and image view.

a.	Activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#D1B352"
    android:padding="16dp"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/registrationImage"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_centerHorizontal="true"
        android:contentDescription="Registration Image"
        android:src="@drawable/ic_launcher_foreground" />

    <EditText
        android:id="@+id/editTextName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/registrationImage"
        android:layout_marginTop="16dp"
        android:hint="Name" />

    <CheckBox
        android:id="@+id/checkBoxAgree"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/editTextName"
        android:layout_marginTop="16dp"
        android:text="I am not a robot" />

    <RadioGroup
        android:id="@+id/radioGroupGender"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/checkBoxAgree"
        android:layout_marginTop="16dp">

        <RadioButton
            android:id="@+id/radioButtonMale"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Male" />

        <RadioButton
            android:id="@+id/radioButtonFemale"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Female" />

        <RadioButton
            android:id="@+id/radioButtonOther"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Other" />
    </RadioGroup>

    <Button
        android:id="@+id/buttonRegister"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/radioGroupGender"
        android:layout_marginTop="16dp"
        android:text="Register" />

</RelativeLayout>

b.	MainActivity.xml

package com.example.registration_page;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.EditText;
import android.widget.ImageView;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    private ImageView registrationImage;
    private EditText editTextName;
    private CheckBox checkBoxAgree;
    private RadioGroup radioGroupGender;
    private Button buttonRegister;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        registrationImage = findViewById(R.id.registrationImage);
        editTextName = findViewById(R.id.editTextName);
        checkBoxAgree = findViewById(R.id.checkBoxAgree);
        radioGroupGender = findViewById(R.id.radioGroupGender);
        buttonRegister = findViewById(R.id.buttonRegister);
        buttonRegister.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String name = editTextName.getText().toString();
                boolean agreedToTerms = checkBoxAgree.isChecked();
                int selectedRadioButtonId = radioGroupGender.getCheckedRadioButtonId();
                RadioButton selectedRadioButton = findViewById(selectedRadioButtonId);
                String gender = selectedRadioButton != null ? selectedRadioButton.getText().toString() : "";
                String message = "Name: " + name + "\nI am not a robot: " + agreedToTerms + "\nGender: " + gender;
                Toast.makeText(getApplicationContext(), message, Toast.LENGTH_LONG).show();
            }
        });
    }
}
