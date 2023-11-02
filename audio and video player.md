6.	Demonstrate usage of audio and video player based on user activity.

Aim: To demonstrate the Audio and video player Application.

a.	Activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/btnstart"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Start"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.125"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.525" />

    <Button
        android:id="@+id/btnstop"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Stop"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.871"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.525" />

    <Button
        android:id="@+id/btnpause"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Pause"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.525" />

    <TextView
        android:id="@+id/title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif-medium"
        android:text="Audio Player"
        android:textSize="28dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.075" />

    <TextView
        android:id="@+id/audioname"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="sans-serif-medium"
        android:text="Get rick rolled"
        android:textSize="24dp"
        android:textStyle="italic"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.536"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.349" />

    <Button
        android:id="@+id/btnchange"
        android:layout_width="151dp"
        android:layout_height="40dp"
        android:text="Change track"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.71" />
</androidx.constraintlayout.widget.ConstraintLayout>

b.	MainActivity.xml
package com.example.audioplayer;

import androidx.appcompat.app.AppCompatActivity;

import android.media.AudioAttributes;
import android.media.MediaPlayer;
import android.net.Uri;
import android.os.Bundle;
import android.provider.MediaStore;
import android.renderscript.RenderScript;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import java.io.IOException;

public class MainActivity extends AppCompatActivity {

    Button pause_button, stop_button, start_button, change_track;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        pause_button = findViewById(R.id.btnpause);
        start_button = findViewById(R.id.btnstart);
        stop_button = findViewById(R.id.btnstop);
        change_track = findViewById(R.id.btnchange);
        final int[] flag = {1};
        final int[] trackNo = {0};
        final MediaPlayer mp = new MediaPlayer();
        Uri my_uri = Uri.parse("https://cdn.pixabay.com/audio/2023/01/16/audio_091569a832.mp3");
        mp.setAudioAttributes(
                new AudioAttributes.Builder()
                        .setContentType(AudioAttributes.CONTENT_TYPE_MUSIC)
                        .setUsage(AudioAttributes.USAGE_MEDIA)
                        .build()
        );

        try{
            if(trackNo[0]==0) {

                 mp.setDataSource(getApplicationContext(), my_uri);
            }
            else {
                mp.setDataSource(getApplicationContext(),Uri.parse("https://cdn.pixabay.com/audio/2023/07/30/audio_e0908e8569.mp3"));
            }
            mp.prepare();
        }

        catch(IOException e){
            e.printStackTrace();
            Log.d("Import failed","importing audio failed");
        }

        pause_button.setOnClickListener((View view )-> {
            if(flag[0] ==1){
                pause_button.setText("Resume");
            }
            else{
                pause_button.setText("Pause");
                mp.start();
            }
            flag[0] = flag[0] *-1;
            mp.pause();
        });

        start_button.setOnClickListener((View view)->{
            mp.start();
        });

        stop_button.setOnClickListener((View view)->{
            mp.stop();
        });

        change_track.setOnClickListener((View view)->{
            if(trackNo[0] == 0){
                trackNo[0] =1;
            }
            else{
                trackNo[0]= 0;
            }
        });


    }
}
