# Flutter-Android
Open flutter android application from other app

# first way

To open a Flutter Android application from another app, you can use an `Intent` to launch the app's main activity. Here's an example of how to do this:

1. In your Flutter Android app, add an intent filter to the `AndroidManifest.xml` file for the activity you want to launch. For example, if you want to launch the main activity, add the following intent filter to your `MainActivity` declaration:

```xml
<activity
    android:name=".MainActivity"
    android:launchMode="singleTop">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />
        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

2. In the other app that wants to launch your Flutter Android app, create a new `Intent` and set its action and package name to match your Flutter Android app's main activity:

```java
Intent intent = new Intent();
intent.setAction(Intent.ACTION_MAIN);
intent.addCategory(Intent.CATEGORY_LAUNCHER);
intent.setPackage("com.example.flutter_app");
startActivity(intent);
```

In this example, we create a new `Intent`, set its action to `ACTION_MAIN`, its category to `CATEGORY_LAUNCHER`, and its package name to match our Flutter Android app's package name.

We then call `startActivity()` with our intent to launch our Flutter Android app's main activity.

I hope this helps! Let me know if you have any further questions.

# second way

Another way to open a Flutter Android application from another app is to use a custom scheme URL. Here's an example of how to do this:

1. In your Flutter Android app, add an intent filter to the `AndroidManifest.xml` file for the activity you want to launch. For example, if you want to launch the main activity, add the following intent filter to your `MainActivity` declaration:

```xml
<activity
    android:name=".MainActivity"
    android:launchMode="singleTop">
    <intent-filter>
        <action android:name="android.intent.action.VIEW" />
        <category android:name="android.intent.category.DEFAULT" />
        <category android:name="android.intent.category.BROWSABLE" />
        <data
            android:scheme="myapp"
            android:host="open_flutter_app" />
    </intent-filter>
</activity>
```

In this example, we add an intent filter that listens for URLs with the `myapp://open_flutter_app` scheme and launches our `MainActivity`.

2. In the other app that wants to launch your Flutter Android app, create a new `Intent` with a custom scheme URL that matches your Flutter Android app's intent filter:

```java
Intent intent = new Intent(Intent.ACTION_VIEW);
intent.setData(Uri.parse("myapp://open_flutter_app"));
startActivity(intent);
```

In this example, we create a new `Intent`, set its action to `ACTION_VIEW`, and set its data URI to match our Flutter Android app's custom scheme URL.

We then call `startActivity()` with our intent to launch our Flutter Android app's main activity.

I hope this helps! Let me know if you have any further questions.
