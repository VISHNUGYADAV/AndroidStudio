9.	Develop custom splash screens for your app

Aim: Displaying custom designed Opening Screen.

a.	activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/idRLContainer"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#635324"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/idIVLogo"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        android:layout_margin="25dp"
        app:tint="@color/white" />

    <!--on below line we are creating progress bar-->
    <ProgressBar
        android:id="@+id/idPBLoading"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/idIVLogo"
        android:layout_centerInParent="true"
        android:indeterminateTint="@color/white" />

    <ImageView
        android:id="@+id/imageView"
        android:layout_width="168dp"
        android:layout_height="175dp"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_marginStart="125dp"
        android:layout_marginTop="122dp"
        android:layout_marginEnd="118dp"
        android:layout_marginBottom="433dp"
        app:srcCompat="@drawable/logo" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="147dp"
        android:layout_height="36dp"
        android:layout_alignParentStart="true"
        android:layout_alignParentTop="true"
        android:layout_alignParentEnd="true"
        android:layout_alignParentBottom="true"
        android:layout_marginStart="154dp"
        android:layout_marginTop="320dp"
        android:layout_marginEnd="110dp"
        android:layout_marginBottom="374dp"
        android:text="Welcome"
        android:textColor="@color/white"
        android:textSize="25sp" />
</RelativeLayout>

b.	activity_main2.xml

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#000000"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/textView4"
        android:layout_width="411dp"
        android:layout_height="49dp"
        android:background="#000000"
        android:text="Till the Last Bite"
        android:textAlignment="center"
        android:textSize="34sp"
        android:textColor="#EFB813"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.023" />

    <ImageView
        android:id="@+id/imageView2"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:srcCompat="@drawable/bg" />


</RelativeLayout>

MainActivity.java

package com.example.opening_screen;
import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import android.view.WindowManager;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // on below line we are configuring our window to full screen
        getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN,
                WindowManager.LayoutParams.FLAG_FULLSCREEN);

        setContentView(R.layout.activity_main);

        new Handler().postDelayed(new Runnable() {
            @Override
            public void run() {
                Intent i = new Intent(MainActivity.this, MainActivity2.class);

                // on below line we are
                // starting a new activity.
                startActivity(i);
                finish();
            }
        }, 2000);
    }
}

MainActivity2.java

package com.example.opening_screen;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
public class MainActivity2 extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
    }
}
AndroidManifest.xml

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="Opening_Screen"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Opening_Screen"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity2"
            android:exported="false"/>
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
</manifest>
