1.	Design and develop a login screen 


Aim: To develop a secure Android login Page application that enables users to authenticate and access personalized content with ease.

a.	Activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:background="#A18EC5">

    <TextView
        android:id="@+id/enterUN"
        android:layout_width="250dp"
        android:layout_height="41dp"
        android:text="Enter your username"
        android:textSize="25dp"
        android:textColor="@color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.51"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.243" />

    <TextView
        android:id="@+id/enterPW"
        android:layout_width="250dp"
        android:layout_height="41dp"
        android:text="Enter your password"
        android:textSize="25dp"
        android:textColor="@color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.523"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.515" />

    <EditText
        android:id="@+id/pw"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="12"
        android:inputType="textPassword"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.554"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.612" />

    <EditText
        android:id="@+id/un"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:ems="12"
        android:inputType="text"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.348" />

    <Button
        android:id="@+id/Login"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="20dp"
        android:text="Login"
        android:layout_marginTop="80dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.718" />

    <TextView
        android:id="@+id/heading"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Login Page"
        android:background="@color/black"
        android:textAlignment="center"
        android:textColor="@color/white"
        android:textSize="35dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.001" />

</androidx.constraintlayout.widget.ConstraintLayout>




b.	MainActivity.xml

package com.example.login;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    private EditText usernameEditText;
    private EditText passwordEditText;
    private Button loginButton;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        usernameEditText = findViewById(R.id.un);
        passwordEditText = findViewById(R.id.pw);
        loginButton = findViewById(R.id.Login);

        loginButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // Get the entered username and password
                String username = usernameEditText.getText().toString().trim();
                String password = passwordEditText.getText().toString().trim();

                // Check if the password meets the validation criteria
                if (isValidPassword(password)) {
                    // Display a success message
                    String message = "Login successful! Welcome, " + username + "!";
                    Toast.makeText(MainActivity.this, message, Toast.LENGTH_SHORT).show();
                } else {
                    // Display a more user-friendly message for an invalid password
                    Toast.makeText(MainActivity.this, "Password should be at least 6 characters long.", Toast.LENGTH_SHORT).show();
                }
            }
        });
    }

    // Simple password validation: At least 6 characters
    private boolean isValidPassword(String password) {
        return password.length() >= 6;
    }
}
