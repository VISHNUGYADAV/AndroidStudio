7.	Develop movie rating app with ratings bar, image view, and other inputs

Aim: To demonstrate Movie Rating application.

a.	Activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"


    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#ADD8E6"
        android:fontFamily="sans-serif-black"
        android:textAlignment="center"
        android:paddingVertical="12dp"
        android:text="Popcorn and Pretzels"
        android:textSize="34dp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.444"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.001" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="We hope you enjoyed watching"
        android:textSize="24dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.127" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="128dp"
        android:layout_height="244dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.209"
        app:srcCompat="@drawable/poster" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Please rate our services"
        android:textSize="22dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.193"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.493" />

    <RatingBar
        android:id="@+id/ratingBar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:rating="4"
        android:theme="@style/RatingBar"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.572" />

    <TextView
        android:id="@+id/textView4"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Select the type of seats"
        android:textSize="22dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.186"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.666" />

    <RadioGroup
        android:layout_width="378dp"
        android:layout_height="40dp"
        android:id="@+id/seattypegroup"
        android:orientation="horizontal"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.752">

        <RadioButton
            android:id="@+id/gold"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginHorizontal="12sp"
            android:text="Gold"
            android:onClick="onRadioButtonClicked"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.194"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="0.749" />

        <RadioButton
            android:id="@+id/silver"
            android:onClick="onRadioButtonClicked"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginHorizontal="12sp"
            android:text="Silver"

            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.784"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="0.749" />

        <RadioButton
            android:id="@+id/platinum"
            android:layout_width="102dp"
            android:layout_height="wrap_content"
            android:onClick="onRadioButtonClicked"
            android:layout_marginHorizontal="12sp"
            android:text="Platinum"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintHorizontal_bias="0.784"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="0.749" />

    </RadioGroup>

    <CheckBox
        android:id="@+id/vipcheck"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Are you a VIP member?"
        android:textSize="22dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.241"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.855" />

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Submit"
        android:onClick="onSubmit"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.95"/>

</androidx.constraintlayout.widget.ConstraintLayout>

b.	MainActivity.xml
package com.example.moviereview;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.CheckBox;
import android.widget.RadioButton;
import android.widget.RatingBar;

public class MainActivity extends AppCompatActivity {

    RatingBar ratings;
    CheckBox isVip;
    float rating_points;
    int seat_flag = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    public void onSubmit(View view){
        ratings = findViewById(R.id.ratingBar);
        rating_points=ratings.getRating();
        isVip = findViewById(R.id.vipcheck);
        boolean is_vip = isVip.isChecked();
        Log.d("OUTPUT","Movie ratings: "+rating_points);
        Log.d("OUTPUT","Seat type: "+this.seat_flag);
        Log.d("OUTPUT","Are they VIP : "+is_vip);


    }

    public void onRadioButtonClicked(View view) {
        // Is the button now checked?
        boolean checked = ((RadioButton) view).isChecked();

        // Check which radio button was clicked
        int id = view.getId();
        if (id == R.id.gold) {
            if (checked) {
                seat_flag = 0;
                return;
            }


        } else if (id == R.id.platinum) {
            if (checked) {
                seat_flag = 1;
                return;
            }

        } else if (id == R.id.silver) {
            if (checked)
            // Ninjas rule
            {
                seat_flag=2;
                return;
            }
            }
        }
    }

c.	Output
