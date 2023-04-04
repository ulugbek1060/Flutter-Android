# Flutter-Android
Open flutter android application from other app

Another way to open a Flutter Android application from another app is to use a custom scheme URL. Here's an example of how to do this:

1. In your Flutter Android app, add an intent filter to the `AndroidManifest.xml` file for the activity you want to launch. For example, if you want to launch the main activity, add the following intent filter to your `MainActivity` declaration:

```xml
<activity>
  
    ...
    
          <intent-filter>
               <action android:name="android.intent.action.VIEW" />
               <category android:name="android.intent.category.DEFAULT" />
               <category android:name="android.intent.category.BROWSABLE" />
               <!--TODO:  Add this filter, if you want support opening urls into your app-->
               <data
                   android:scheme="example_scheme"
                   android:host="example_host.com"/>
           </intent-filter>
<activity/>
```

In this example, we add an intent filter that listens for URLs with the `myapp://open_flutter_app` scheme and launches our `MainActivity`.

2. In the other app that wants to launch your Flutter Android app, create a new `Intent` with a custom scheme URL that matches your Flutter Android app's intent filter:

```kotlin
     try {
            val intent = Intent(Intent.ACTION_VIEW)
            intent.data = Uri.parse("example_scheme://example_host.com")
            startActivity(intent)
         } catch (e: ActivityNotFoundException) {
            Toast.makeText(this, "${e.message}", Toast.LENGTH_SHORT).show()
         }
```

In this example, we create a new `Intent`, set its action to `ACTION_VIEW`, and set its data URI to match our Flutter Android app's custom scheme URL.

We then call `startActivity()` with our intent to launch our Flutter Android app's main activity.

I hope this helps! Let me know if you have any further questions.
