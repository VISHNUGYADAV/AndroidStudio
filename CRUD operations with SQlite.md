11.	Demonstrate CRUD operations with SQlite

Aim:To demonstrate the Sqlite Database in android Application
a.	Activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Please enter the details below"
        android:textSize="24dp"
        android:layout_marginHorizontal="20sp"
        android:id="@+id/parent"
        />
    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/name"
        android:hint="Name"
        android:textSize="22dp"
        android:layout_below="@+id/parent"
        android:inputType="textPersonName"/>
    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/phone"
        android:hint="Phone number"
        android:textSize="22dp"
        android:layout_below="@+id/name"
        android:inputType="textPhonetic"/>
    <EditText
        android:id="@+id/email"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="email@gamil.com"
        android:textSize="22dp"
        android:layout_below="@+id/phone"
        android:inputType="textEmailAddress"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/insert_btn"
        android:textSize="24dp"
        android:text="Insert data"

        android:layout_below="@+id/email"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/update_btn"
        android:textSize="24dp"

        android:text="Update data"
        android:layout_below="@+id/insert_btn"

        />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/delete_btn"
        android:textSize="24dp"
        android:text="delete data"

        android:layout_below="@+id/update_btn"
/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/view_btn"
        android:textSize="24dp"
        android:text="View data"

        android:layout_below="@+id/delete_btn"
/>

</RelativeLayout>

b.	MainActivity.xml
package com.example.myapplication;

import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;

import android.database.Cursor;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    EditText name, email, phone;
    Button insert, update, delete, view;
    DBHelper DB;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        name = findViewById(R.id.name);
        email = findViewById(R.id.email);
        phone = findViewById(R.id.phone);
        insert = findViewById(R.id.insert_btn);
        update = findViewById(R.id.update_btn);
        delete = findViewById(R.id.delete_btn);
        view = findViewById(R.id.view_btn);
        DB = new DBHelper(this);

        insert.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String nameTxt = name.getText().toString();
                String emailTxt = email.getText().toString();
                String phoneTxt = phone.getText().toString();

                if (phoneTxt.length()!=10){
                    Toast.makeText(MainActivity.this, "invalid phone number", Toast.LENGTH_SHORT);
                    return;
                }
                if (emailTxt.indexOf("@")<0){
                    Toast.makeText(MainActivity.this, "invalid email", Toast.LENGTH_SHORT);

                    return;
                }
                Boolean checkinsertdata = DB.insertuserdata(nameTxt,phoneTxt, emailTxt );
                if(checkinsertdata){
                    Toast.makeText(MainActivity.this, "New entry made", Toast.LENGTH_LONG).show();
                }
                Toast.makeText(MainActivity.this, "Entry failed", Toast.LENGTH_LONG).show();

            }
        });

        update.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String nameTxt = name.getText().toString();
                String emailTxt = email.getText().toString();
                String phoneTxt = phone.getText().toString();

                Boolean checkupdatedata = DB.updateuserdata(nameTxt,phoneTxt, emailTxt);
                if(checkupdatedata){
                    Toast.makeText(MainActivity.this, "New Update made", Toast.LENGTH_LONG).show();
                }else
                Toast.makeText(MainActivity.this, "update failed", Toast.LENGTH_LONG).show();
            }
        });

        delete.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String nameTxt = name.getText().toString();
                Boolean checkdeletedata = DB.deletedata(nameTxt);
                if(checkdeletedata){
                    Toast.makeText(MainActivity.this, "delete made", Toast.LENGTH_LONG).show();
                }else
                Toast.makeText(MainActivity.this, "delete failed", Toast.LENGTH_LONG).show();
            }
        });

        view.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                Cursor res = DB.getdata();
                if(res.getCount() == 0){
                    Toast.makeText(MainActivity.this, "No entries present", Toast.LENGTH_LONG).show();
                    return;
                }
                StringBuffer buffer = new StringBuffer();
                while(res.moveToNext()){
                    buffer.append("name : "+ res.getString(0)+"\n");
                    buffer.append("phone : "+ res.getString(1)+"\n");
                    buffer.append("email : "+ res.getString(2)+"\n\n");

                }
                AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
                builder.setCancelable(true);
                builder.setTitle("User entries");
                builder.setMessage(buffer.toString());
                builder.show();
                Toast.makeText(MainActivity.this, "update failed", Toast.LENGTH_LONG).show();
            }
        });
    }
}
c.	Dbhelper.java
package com.example.myapplication;

import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

import androidx.annotation.NonNull;
import androidx.annotation.Nullable;

public class DBHelper extends SQLiteOpenHelper {
    public DBHelper(Context context) {
        super(context, "Userdata.db", null, 1);
    }

    @Override
    public void onCreate(SQLiteDatabase DB) {
        DB.execSQL("create Table Userdetails(name Text  PRIMARY KEY, phone Text, email Text)  ");
    }

    @Override
    public void onUpgrade(SQLiteDatabase DB, int i, int i1) {
        DB.execSQL("drop table if exists Userdetails");
    }

    public boolean insertuserdata(String name, String phone, String email){
        SQLiteDatabase DB = this.getWritableDatabase();
        ContentValues cv = new ContentValues();
        cv.put("name", name);
        cv.put("phone", phone);
        cv.put("email",email);

        long result = DB.insert("Userdetails", null, cv);
        return result!=-1;
    }

    public boolean updateuserdata(String name, String phone, String email){
        SQLiteDatabase DB = this.getWritableDatabase();
        ContentValues cv = new ContentValues();
        cv.put("name", name);
        cv.put("phone", phone);
        Cursor cursor = DB.rawQuery("select * from Userdetails where name = ?", new String[] {name});
        if (cursor.getCount()>0){
            long result = DB.update("Userdetails", cv, "name=?", new String[]{name});
            return (result!=-1);
        }
        return false;
    }

    public boolean deletedata(String name){
        SQLiteDatabase DB = this.getWritableDatabase();
        Cursor cursor = DB.rawQuery("select * from Userdetails where name = ?", new String[] {name});
        if (cursor.getCount()>0){
            long result = DB.delete("Userdetails", "name=?", new String[]{name});
            return (result!=-1);
        }
        return false;
    }

    public Cursor getdata(){
        SQLiteDatabase DB = this.getWritableDatabase();
        Cursor cursor = DB.rawQuery("select * from Userdetails", null);
        return cursor;
    }
}
