Program 1
Creating “Hello world” Application.
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns: android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    >
    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        android:textSize="80dp"/>
</LinearLayout>
MainActivity.java
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity
 {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
}



Output
 

Program2
Creating an application that displays message based on the screen orientation
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto" >
<Button
android:id="@+id/button" 
android:layout_width="wrap_content"
 android:layout_height="wrap_content" 
android:onClick="onClick" 
android:text="Launch Next Activity"
/>
<TextView
android:id="@+id/textView2"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content" 
android:text="This activity is portrait orientation" 
/>
</androidx.constraintlayout.widget.ConstraintLayout>
activity_next.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android">
<TextView
android:id="@+id/textView" 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="This is landscape orientation" 
/>
</androidx.constraintlayout.widget.ConstraintLayout>
MainActivity.java
import android.content.Intent; 
import android.os.Bundle; 
import android.view.View;
import androidx.appcompat.app.AppCompatActivity; 
public class MainActivity extends AppCompatActivity {
 @Override
protected void onCreate(Bundle savedInstanceState) { 
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_main);
}

public void onClick(View v){
Intent intent = new Intent(MainActivity.this, NextActivity.class); startActivity(intent);
}
}
NextActivity.java
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity; 
{ 
@Override
protected void onCreate(Bundle savedInstanceState) { 
super.onCreate(savedInstanceState); 
setContentView(R.layout.activity_next);
}
}
AndroidManifest.xml
<?xml version="1.0" encoding="utf-8"?>
<manifest >
<application>
<activity
android:name=".NextActivity" 
android:exported="false" 
android:screenOrientation="landscape"
/>
<activity
android:name=".MainActivity" 
android:exported="true" 
android:screenOrientation="portrait"
>
<intent-filter>
<action android:name="android.intent.action.MAIN" />
<category android:name="android.intent.category.LAUNCHER" />
</intent-filter>
</activity>
</application>
</manifest>
Output




Program3
Create an application to develop login window using UI controls
MainActivity.java
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {

   EditText et_username, et_password;
   Button login_btn;
   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main);
       login();
   }
   void login(){
       et_username = (EditText) findViewById(R.id.et_username);
       et_password = (EditText) findViewById(R.id.et_password);
       login_btn = (Button) findViewById(R.id.btn_login);
       login_btn.setOnClickListener(new View.OnClickListener() 
{
           @Override
           public void onClick(View v)
 {
               if(et_username.getText().toString().equals("admin") && et_password.getText().toString().equals("admin")){
                   Toast.makeText(MainActivity.this, "Username and password is correct", Toast.LENGTH_SHORT).show();
                   Intent intent = new Intent(MainActivity.this, User.class);
                   startActivity(intent);
               }else{
                   Toast.makeText(MainActivity.this, "Username or password is incorrect", Toast.LENGTH_SHORT).show();
               }
           }
       });

   }
}
activity_main.xml
   <RelativeLayout
xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"

       android:layout_width="match_parent"
       android:layout_height="match_parent">

       <TextView
           android:id="@+id/login_text"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="Login"
           android:textSize="30dp" />

       <TextView
           android:id="@+id/username_text"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="Username"
           android:textSize="25sp" />
       <EditText
           android:id="@+id/et_username"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           />
       <TextView
           android:id="@+id/password_text"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:layout_below="@id/et_username"
           android:text="Password"/>
       <EditText
           android:id="@+id/et_password"	
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"/>
       <Button
           android:id="@+id/btn_login"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="Button" />
   </RelativeLayout>

User.java
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class User extends AppCompatActivity {
   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_user);
   }
}
activity_user.xml
<?xml version="1.0" encoding="utf-8"?>
   <RelativeLayout
xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
       android:layout_width="match_parent"
       android:layout_height="match_parent">

       <TextView
           android:id="@+id/textView"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:text="Welcome"
           android:textSize="30sp" />

       <TextView
           android:id="@+id/textView2"
           android:layout_width="wrap_content"
           android:text="Administrator"
           android:textSize="25sp" />
   </RelativeLayout>

Output
   
Program4
Create an application to implement new activity using explicit intent, implicit intent.
MainActivity.java
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import androidx.appcompat.app.AppCompatActivity;
import java.net.URI;
public class MainActivity extends AppCompatActivity {
   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main);
   }

   public void onImplicitButtonClicked(View view){
       Uri uri = Uri.parse("https://www.google.com");
       Intent intent = new Intent(Intent.ACTION_VIEW, uri);
       startActivity(intent);
   }

   public void onExplicitButtonClicked(View view){
       Intent intent = new Intent(MainActivity.this, Second.class);
       startActivity(intent);
   }
}
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
   <LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:gravity="center"
       android:orientation="vertical">

       <Button
           android:id="@+id/button2"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:onClick="onExplicitButtonClicked"
           android:text="Explicit Button" />

       <Button
           android:id="@+id/button3"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:onClick="onImplicitButtonClicked"
           android:text="Implicit Button" />
   </LinearLayout>

SecondActivity.java
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
public class Second extends AppCompatActivity {

   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_second);
   }
}

activity_second.xml
<?xml version="1.0" encoding="utf-8"?>
   <LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:gravity="center"
       android:orientation="horizontal">
       <TextView
           android:id="@+id/textView"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:gravity="center"
           android:text="Second Activity"
           android:textSize="20dp" />
   </LinearLayout>
Output:
    

Program5
Create an application that displays custom designed opening screen
MainActivity.java
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {

   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main);
}
}
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
   <RelativeLayout
xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
       android:layout_width="match_parent"
       android:layout_height="match_parent"
       android:gravity="center">
       <TextView
           android:id="@+id/textView"
           android:layout_width="wrap_content"
           android:layout_height="wrap_content"
           android:gravity="center"
           android:text="Hello Android Developer"
           android:textSize="20sp" />
   </RelativeLayout>

Splash.java
import android.content.Intent;
import android.os.Bundle;
import android.os.Handler;
import androidx.appcompat.app.AppCompatActivity;

public class Splash extends AppCompatActivity {
   Handler handler;
   @Override
   protected void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_splash);
       handler = new Handler();

       handler.postDelayed(new Runnable() {
@Override
           public void run() {
               Intent intent = new Intent(Splash.this, MainActivity.class);
               startActivity(intent);
               finish();
           }
       }, 3000);
   }
}
AndroidManifest.xml
<?xml version="1.0" encoding="utf-8"?>
<manifest >

   <application>
       <activity
           android:name=".MainActivity"
           android:exported="false" />
       <activity
           android:name=".Splash"
           android:exported="true">
           <intent-filter>
               <action android:name="android.intent.action.MAIN" />

               <category android:name="android.intent.category.LAUNCHER" />
           </intent-filter>
       </activity>
   </application>

</manifest>

Output
      

Program6
Create an UI with all views
MainActivity.java
import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.ImageButton;
import android.widget.RadioButton;
import android.widget.RadioGroup;
import android.widget.RadioGroup.OnCheckedChangeListener;
import android.widget.Toast;
import android.widget.ToggleButton;

public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Button btn = (Button) findViewById(R.id.button);
        CheckBox chkbox = (CheckBox) findViewById(R.id.checkBox);
        RadioGroup rgrp = (RadioGroup) findViewById(R.id.radiogroup);
        ToggleButton togbtn = (ToggleButton) findViewById(R.id.toggleButton);
        ImageButton imgbtn = (ImageButton) findViewById(R.id.imagebutton);
        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View arg0) {
                ToastToDisplay("Hey Button is pressed");
            }
        });
        chkbox.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (((CheckBox) v).isChecked()) {
                    ToastToDisplay("CheckBox is checked!!");
                } else {
                    ToastToDisplay("CheckBox is unchecked!");

                }
            }
        });
        rgrp.setOnCheckedChangeListener(new OnCheckedChangeListener() {
            @Override
            public void onCheckedChanged(RadioGroup group, int checkedId) {
                RadioButton rb1 = (RadioButton) findViewById(R.id.radiobutton1);
                RadioButton rb2 = (RadioButton) findViewById(R.id.radiobutton2);
                RadioButton rb3 = (RadioButton) findViewById(R.id.radiobutton3);
                if (rb1.isChecked()) {
                    ToastToDisplay("Radio Button 1 is checked!");
                } else if (rb2.isChecked()) {
                    ToastToDisplay("Radio Button 2 is checked!");} else {
                    ToastToDisplay("RadioButton 3 is checked");
                }
            }
        });
        togbtn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (((ToggleButton) v).isChecked()) {
                    ToastToDisplay("Toggle Button is On");
                } else {
                    ToastToDisplay("Toggle Buttton is Off");
                }
            }
        });
        imgbtn.setOnClickListener(new View.OnClickListener() {
                                      @Override
                                      public void onClick(View v) {
                                          ToastToDisplay("Image Button id pressed");
                                      }
                                  }
        );
    }
private void ToastToDisplay(String args) {
    Toast.makeText(getBaseContext(), args, Toast.LENGTH_SHORT).show();

}
}

activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">
    <TextView
        android:id="@+id/textview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello readers!!" />
    <Button
        android:id="@+id/button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Click!!"/>
    <CheckBox
        android:id="@+id/checkBox"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Checkbox!!" />
    <ToggleButton
        android:id="@+id/toggleButton"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="ToggleButton!!" />

    <RadioGroup
        android:id="@+id/radiogroup"
        android:layout_width="match_parent"
        android:layout_height="match_parent" >
            <RadioButton
                android:id="@+id/radiobutton1"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="RadioButton1" />
            <RadioButton
                android:id="@+id/radiobutton2"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="RadioButton2" />

            <RadioButton
                android:id="@+id/radiobutton3"
                android:layout_width="match_parent"
                android:layout_height="wrap_content"
                android:text="RadioButton3" />

        <ImageButton
            android:id="@+id/imagebutton"
            android:layout_width="232dp"
            android:layout_height="202dp"
            android:src="@drawable/ic_launcher_foreground"
            tools:srcCompat="@tools:sample/avatars" />

    </RadioGroup>

</LinearLayout>

Output
        

           

Program7
Create menu in application
MainActivity.java
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu){
        getMenuInflater().inflate(R.menu.my_menu, menu);
        return super.onCreateOptionsMenu(menu);
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item){
        switch(item.getItemId()){
            case R.id.search:
                Toast.makeText(
                        getApplicationContext(),
                        "Selected item search",
                        Toast.LENGTH_LONG
                ).show();
                break;
            case R.id.upload:
                Toast.makeText(
                        getApplicationContext(),
                        "Selected item upload",
                        Toast.LENGTH_LONG
                ).show();
                break;
                case R.id.copy:
                Toast.makeText(
                        getApplicationContext(),
                        "Selected item copy",
                        Toast.LENGTH_LONG
                ).show();
                break;
                case R.id.paste:
                Toast.makeText(
                        getApplicationContext(),
                        "Selected item paste",
                        Toast.LENGTH_LONG
                ).show();
                break;
            case R.id.bookmark:
                Toast.makeText(
                        getApplicationContext(),
                        "Selected item bookmark",
                        Toast.LENGTH_LONG
                ).show();
                break;
            default:
                Toast.makeText(
                        getApplicationContext(),
                        "Selected item is default",
                        Toast.LENGTH_SHORT
                ).show();
                break;
        }
        return super.onOptionsItemSelected(item);
    }
}
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Choose menu options"
     android:textSize="50dp"
    android:gravity="center_vertical"/>

</LinearLayout>

my_menu.xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:id="@+id/search"
        android:title="Search" />
    <item
        android:id="@+id/upload"
        android:title="Upload" />
    <item
        android:id="@+id/copy"
        android:title="Copy" />
    <item
        android:id="@+id/paste"
        android:title="Paste" />
    <item
        android:id="@+id/bookmark"
        android:title="Bookmark" >
        <menu >
            <item android:title="Item" />
        </menu>
    </item>
</menu>
gradle.properties
android.nonTransitiveRClass=true
android.nonFinalResIds=false

Output
     

Program8
Read/Write local data
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
    xmlns:app="http://schemas.android.com/apk/res-auto"	
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">	
    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="username"
/>
    <EditText
        android:id="@+id/username"
        android:layout_width="match_parent"
        android:layout_height="wrap_content”
/>
    <TextView
        android:id="@+id/password"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="password"
    />
    <EditText
        android:id="@+id/etpassword"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"/>

    <Button
        android:id="@+id/btn_save"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="save"
/>

    <Button
        android:id="@+id/btn_next"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Next"
/>
</LinearLayout>

MainActivity.java
import android.content.Context;
import android.content.Intent;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    Button btnsave,btnnext;
    EditText etusername,etpassword;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        btnsave = (Button) findViewById(R.id.btn_save);
        btnnext = (Button) findViewById(R.id.btn_next);
        etusername = (EditText) findViewById(R.id.username);
        etpassword = (EditText) findViewById(R.id.etpassword);
        btnsave.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                SharedPreferences sharedPreferences = getSharedPreferences("My prefs", Context.MODE_PRIVATE);
                SharedPreferences.Editor editor = sharedPreferences.edit();
                editor.putString("username", etusername.getText().toString());
                editor.putString("password", etpassword.getText().toString());
                editor.apply();
                Toast.makeText(getApplicationContext(), "saved successfully", Toast.LENGTH_LONG).show();
            }
        });
        btnnext.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Intent intent=new Intent(getApplicationContext(), MainActivity2.class);
                startActivity(intent);

    }
        });
    }
}
activity_main2.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">
    <Button
        android:id="@+id/fetch"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text=”fetch”/>

    <TextView
        android:id="@+id/username2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="username"/>

    <EditText
        android:id="@+id/et_username2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="username"/>

    <TextView
        android:id="@+id/password2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="password" />

    <EditText
        android:id="@+id/et_password2"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:ems="10"
        android:inputType="text"
/>
</LinearLayout>

MainActivity2.java
import android.content.Context;
import android.content.SharedPreferences;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;
    Button btnfetch;
    EditText etusername,etpassword;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
       setContentView(R.layout.activity_main2);
       btnfetch=(Button) findViewById(R.id.fetch);
       etusername=(EditText) findViewById(R.id.et_username2);
       etpassword=(EditText) findViewById(R.id.et_password2);
       btnfetch.setOnClickListener(new View.OnClickListener() {
           @Override
           public void onClick(View v) {
               SharedPreferences sharedPreferences=getSharedPreferences("My prefs", Context.MODE_PRIVATE);
               etusername.setText(sharedPreferences.getString("username",""));
               etpassword.setText(sharedPreferences.getString("password",""));
           }
       });
    }
}






Output
        

Program9
Create an application to send an email.
activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout 
xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto">

    <EditText
        android:id="@+id/test_email"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="150dp"
        android:hint="Test Email"
        android:textSize="20sp" />

    <EditText
        android:id="@+id/test_content"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/test_email"
        android:hint="Test Subject"
        android:textSize="20sp"/>

    <EditText
        android:id="@+id/test_body"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@+id/test_content"
        android:hint="Test Body"
        android:textSize="20sp"/>

    <Button
        android:id="@+id/send_email_btn"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@+id/test_body"
        android:text="Send Email"
/>
</RelativeLayout>
MainActivity.java
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
Button sendEmailButton =findViewById(R.id.send_email_btn);
        sendEmailButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                composeEmail();
            }
        });
    }

    private void composeEmail() {
        Intent intent=new Intent(Intent.ACTION_SENDTO);
        intent.setData(Uri.parse("mailto:"));
        intent.putExtra(Intent.EXTRA_EMAIL,new String[]{"recipient@example.com"});
        intent.putExtra(Intent.EXTRA_SUBJECT,"Subject of the email");
        intent.putExtra(Intent.EXTRA_TEXT,"Body of the email");

        if (intent.resolveActivity(getPackageManager())!=null){
            startActivity(intent);
        }
    }
}
AndroidManifest.xml
<?xml version="1.0" encoding="utf-8"?>
<manifest >
    <uses-permission android:name="android.permission.INTERNET"/>

    <application>
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
        

Program10

Steps to deploy Android Application
1.Prepare App
2.Generate Signed APK(Android Package Kit)
    -> In Android studio navigate to build->Generate signed Bundle/APK
    ->Follow the prompts to create the new keystore or use an existing one.A keystore is a binary file that contains a set of private keys.
->Configure the build type(release) and signing configuration.
->Generate the signed APK file.
3.Test your Signed APK:
Before distributing your app, test the signed APK to ensure that the signing process does not have any issues.
Install the APK on various devices and perform through testing.
Release on Google play console:
Sign in to Google play console
Create a new app entry if this is the first release or select an existing app.
Complete all the required information for the app listing, including the title,description, screenshots and categorization.
Upload the signed APK file.
Set pricing and distribution options.
Optimize the store listing for search and conversion.
Once everything is set click on Publish button to release the app to the Google Play store.


