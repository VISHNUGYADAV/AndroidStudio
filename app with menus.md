12.	Develop an app with menus

Aim: Creating Option menu in android application
activity_main.xml

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#886FB5"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/tv"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="School of Academics"
        android:textSize="36sp"
        android:textColor="@color/black"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>

options.xml

<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/i1"
        android:title="Mathematics" />
    <item
        android:id="@+id/i2"
        android:title="Chemistry" />
    <item android:title="Information Technology" >
        <menu>
            <item
                android:id="@+id/i3"
                android:title="Computer Science" />
            <item
                android:id="@+id/i4"
                android:title="Big Data Analytics" />
        </menu>
    </item>
</menu>

MainActivity.java

package com.example.menu;

import androidx.annotation.NonNull;
import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {
    TextView tv;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        tv = findViewById(R.id.tv);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        MenuInflater m = getMenuInflater();
        m.inflate(R.menu.options, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(@NonNull MenuItem item) {
        int itemId = item.getItemId();

        if (itemId == R.id.i1) {
            tv.setText("Mathematics");
            return true;
        } else if (itemId == R.id.i2) {
            tv.setText("Chemistry");
            return true;
        } else if (itemId == R.id.i3) {
            tv.setText("Computer Science");
            return true;
        } else if (itemId == R.id.i4) {
            tv.setText("Big Data Analytics");
            return true;
        }

        return super.onOptionsItemSelected(item);
    }
}
