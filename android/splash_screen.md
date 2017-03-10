# Splash Screen In Android
> 10/03/2017, during my work on ScutOps App

Android splash screen are normally used to show user some kind of progress before the app loads completely. Some people uses splash screen just to show case their app / company logo for a couple of second.

**To create properly sized splash screens, you will need background images of different sizes/densities, viz., xxhdpi, xhdpi, hdpi, mdpi and ldpi.**

An android studio plugin called `Android Drawable Importer` lets you create these easily.
See [this](http://stackoverflow.com/questions/19196616/is-there-a-way-to-create-xxhdpi-xhdpi-hdpi-mdpi-and-ldpi-drawables-from-a-lar).

**Create mutiple images of `landing_page.png` each corresponding to a particular pixel density using Android Drawable Importer and save it in `res/drawable/`**

> *While searching about splash screens, I came across a term `9-patch-image`. It seems that it solves the problem of different screen densities, but I couldn't get it working :(.*

**Now let's get into splash screen code!**
- Create an Activity, say `SplashScreenActivity`

    ```java
    public class SplashScreenActivity extends AppCompatActivity {

    	/** Duration of wait **/
    	private final int SPLASH_DISPLAY_LENGTH = 2000;
    
    	@Override
    	protected void onCreate(Bundle savedInstanceState) {
    		super.onCreate(savedInstanceState);
    
    		 /* New Handler to start the Menu-Activity
             * and close this Splash-Screen after some seconds.*/
    		new Handler().postDelayed(new Runnable(){
    			@Override
    			public void run() {
                    /* Create an Intent that will start the Menu-Activity. */
    				Intent mainIntent = new Intent(SplashScreenActivity.this, MainActivity.class);
    				SplashScreenActivity.this.startActivity(mainIntent);
    				SplashScreenActivity.this.finish();
    			}
		    }, SPLASH_DISPLAY_LENGTH);
	    }
    }
    ```
    
- In res/drawables, create a resource file `background_splash.xml`
    *(replace `@drawable/landing_page` with `@drawable/<splash_screen_image_name>`)*
    
    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <layer-list xmlns:android="http://schemas.android.com/apk/res/android">
        <item
            android:drawable="@color/colorScutOpsPrimary"/>
        <item>
            <bitmap
                android:gravity="fill"
                android:src="@drawable/landing_page"/>
        </item>
    </layer-list>
    ```
- Create a new theme in res/values/styles.xml, say `SplashTheme`.

    ```xml
	<!-- Splash screen theme -->
	<style name="SplashTheme" parent="Theme.AppCompat.NoActionBar">
	    <item name="android:windowBackground">@drawable/background_splash</item>
	</style>
    ```
- Finally, add this theme to SplashScreenActivity in `AndroidManifest.xml` file.

    ```xml
	<activity
	    android:name=".SplashScreenActivity"
	    android:screenOrientation="portrait"
	    android:theme="@style/SplashTheme">
	    <intent-filter>
			<action android:name="android.intent.action.MAIN"/>
			<category android:name="android.intent.category.LAUNCHER"/>
	    </intent-filter>
	</activity>
    ```
