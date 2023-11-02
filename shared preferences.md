14.	Demonstrate the use of shared preferences

Aim:To demonstrate the Shared Preferences.

activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#85A59E"
    android:orientation="vertical"
    tools:context="com.example.sharedpreferences_studentdetails.MainActivity">

    <TextView
        android:id="@+id/textview"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#000000"
        android:gravity="center_horizontal"
        android:textColor="@color/white"
        android:textSize="30sp"
        tools:text="Your text" />

    <!-- New EditText fields for student details -->
    <EditText
        android:id="@+id/edittextName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20sp"
        android:hint="Enter Name" />

    <EditText
        android:id="@+id/edittextRollNo"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20sp"
        android:hint="Enter Reg No" />

    <EditText
        android:id="@+id/edittextContactNo"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20sp"
        android:hint="Enter Contact Number" />

    <Button
        android:id="@+id/apply_text_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:text="apply text" />

    <Switch
        android:id="@+id/switch1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal" />

    <Button
        android:id="@+id/save_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="center_horizontal"
        android:text="save data" />

</LinearLayout>

MainActivity.java

package com.example.sharedpreferences_studentdetails;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Switch;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private TextView textView;
    private EditText editText, editTextName, editTextRollNo, editTextContactNo;
    private Button applyTextButton, saveButton;
    private Switch switch1;

    public static final String SHARED_PREFS = "sharedPrefs";
    public static final String TEXT = "text";
    public static final String SWITCH1 = "switch1";

    private String text, studentName, studentRollNo, studentContactNo;
    private boolean switchOnOff;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        textView = findViewById(R.id.textview);
        editText = findViewById(R.id.edittextName);
        applyTextButton = findViewById(R.id.apply_text_button);
        saveButton = findViewById(R.id.save_button);
        switch1 = findViewById(R.id.switch1);

        editTextName = findViewById(R.id.edittextName);
        editTextRollNo = findViewById(R.id.edittextRollNo);
        editTextContactNo = findViewById(R.id.edittextContactNo);

        applyTextButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                textView.setText(editTextName.getText().toString());
            }
        });

        saveButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                                saveData();
            }
        });

        loadData();
        updateViews();
    }

    public void saveData() {
        SharedPreferences sharedPreferences = getSharedPreferences(SHARED_PREFS, MODE_PRIVATE);
        SharedPreferences.Editor editor = sharedPreferences.edit();

        editor.putString(TEXT, textView.getText().toString());
        editor.putBoolean(SWITCH1, switch1.isChecked());

        // Save additional student details
        editor.putString("NAME", editTextName.getText().toString());
        editor.putString("ROLL_NO", editTextRollNo.getText().toString());
        editor.putString("CONTACT_NO", editTextContactNo.getText().toString());
        editor.apply();

        Toast.makeText(this, "Data saved", Toast.LENGTH_SHORT).show();
    }

    public void loadData() {
        SharedPreferences sharedPreferences = getSharedPreferences(SHARED_PREFS, MODE_PRIVATE);
        text = sharedPreferences.getString(TEXT, "");
        switchOnOff = sharedPreferences.getBoolean(SWITCH1, false);
        studentName = sharedPreferences.getString("NAME", "");
        studentRollNo = sharedPreferences.getString("ROLL_NO", "");
        studentContactNo = sharedPreferences.getString("CONTACT_NO", "");     }

    public void updateViews() {
        textView.setText(text);
        switch1.setChecked(switchOnOff);

        editTextName.setText(studentName);
        editTextRollNo.setText(studentRollNo);
        editTextContactNo.setText(studentContactNo); // Updated to set contact number
    }
}
