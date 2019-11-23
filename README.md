# Android Handout (Java)

## Summary

 - #### [Intents](#intents)
 - #### [Splash Screen](#splash-screen)
 - #### [Dialogs](#dialogs)

## Intents
- Go from FirstActivity to SecondActivity

**FirstActivity.java**
````java
Intent i = new Intent(FirstActivity.this, SecondActivity.class);
startActivity(i);
````
---
- Send data between FirstActivity and SecondActivity

**FirstActivity.java**
````java
Intent i = new Intent(FirstActivity.this, SecondActivity.class);
i.putExtra("key", "value");
startActivity(i);
````
**SecondActivity.java**
````java
String data = getIntent().getExtras().getString("key");
````
String `data` is equal to `"value"` now.

## Splash Screen

1. Create an activity called `SplashActivity`

2. Create a drawable resource file

 **splash_background.xml**
````xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">
    <item android:drawable="@android:color/black" />
    <item>
        <bitmap
            android:gravity="center"
            android:src="@mipmap/ic_launcher" />
    </item>
</layer-list>
````

3. Create a style

**styles.xml**
````xml
<style name="SplashTheme" parent="Theme.AppCompat.NoActionBar">
	<item name="android:windowBackground"> 
		@drawable/splash_background
	</item>
</style>
````

4. Create an intent in SplashActivity to go to the activity that should appear after splash

**SplashActivity.java**
````java
Intent i = new Intent(SplashActivity.this, MainActivity.class);
startActivity(i);
finish();
````

## Dialogs
Basic dialogs contain:
- Title
- Description
- Positive Button (Action)
- Negative Button (Cancel)

````java
new AlertDialog.Builder(this)
       .setTitle("Title")
       .setMessage("This is the description")
       .setPositiveButton("Exit", new DialogInterface.OnClickListener() {
           public void onClick(DialogInterface dialog, int which) {
               // Code
           }
       })
       .setNegativeButton("Cancel", null)
       .show();
````
