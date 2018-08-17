---
layout: post
title: Understanding Android Activities and LifeCycles
categories: Android
tags: 'Android, Lifecycle, activities, onCreate, onStart, onResume, onPause, onStop, onDestroy'
comments: true
---

<div class="message">
  An activity is similar to a webpage in a sense that it has both a layout(UI) and logic.
</div>

Activities are an integral part of any Android application and just like web pages they have a layout and logic 
associated with them. But unlike desktop apps the mobile experience doesn't always start from the same screen. 
For example, if you open an online chat application you might see a list of friends. By contrast if you click on 
a notification it will directly take you to that chat.

Most android apps will have multiple activities and each activity provides a window where the app draws the UI.
Usually one of these activities will be the main activity(launcher activity) and will open by default. 
User interactions and other logic are also handled by an Activity. An important concept of an Activity is it's lifecycle.

### Activity Life Cycle

Every activity goes through a set of states during it's life called life cycles states. The android system calls 
corresponding callback methods in your activity class when the app goes through it's lifecycles. 
These callbacks are provided by the `Activity` class.

![Activity life cycle](/public/images/2018-08-15-understanding-activities-lifecycles/acitivy-lifecycle.png)

When an application starts the `onCreate()` method is called, followed by the `onStart()` and `onResume()` methods.
The app becomes visible now and when you minimize the app, methods `onPause()` and `onStop()` are called. 
From the stopped state, the activity either comes back to interact with the user, or the activity is finished 
running and goes away after calling `onDestroy()` method. If the activity comes back, the system invokes the 
`onRestart()` method. The `onDestroy()` method is called when the app is force closed by the user or the when 
the system kills the app to reclaim memory.

To listen to these events you must override these methods in your activity class.

##### MainActivity.java

{% highlight java %}
public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

}
{% endhighlight %}

The `onCreate()` callback will be triggered when the system first creates the activity. In this call back you perform
the application startup logic that need to be done only once(Like setting the correct layout file for the 
activity to draw). In the example above the setContentView() method sets the layout as `R.layout.activity_main`. 
Layout files are xml files that specify how the UI should be drawn. We use various tags to represent elements(views) 
and attributes to specific properties like height, width or color.

##### activity_main.xml

{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout 
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintLeft_toLeftOf="parent"
        app:layout_constraintRight_toRightOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
{% endhighlight %}

<img src="/public/images/2018-08-15-understanding-activities-lifecycles/1.png" alt="drawing" style="margin:auto; padding: 20px" width="350px"/>

In the `activity_main.xml` the outer view is a `ConstrainLayout` which is a container(view group) that can hold other 
views. Inside the constrain layout there is a `TextView` and as the name suggests it shows the text "Hello World!". 
Various attributes specify properties for a view. 
You can more about it from the [developer docs](https://developer.android.com/guide/topics/ui/).

To see the life cycle callbacks in action we can make a simple application that logs the states.

##### MainActivity.java

{% highlight java %}
public class MainActivity extends AppCompatActivity {

    public static final String TAG = "lifecycle_callback: ";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Log.v(TAG, "onCreate");
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.v(TAG, "onStart");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.v(TAG, "onResume");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.v(TAG, "onPause");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.v(TAG, "onStop");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.v(TAG, "onDestroy");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.v(TAG, "onRestart");
    }
}
{% endhighlight %}

Then checkout the `Logcat` tab in Android Studio with the keyword: `Lifecycle callback` to see the life cycle methods 
being called. Try minimizing or force stopping the app to see which methods are called.

![life cylce callback logcat](/public/images/2018-08-15-understanding-activities-lifecycles/2.png)

Read more about activities and lifecycles at [developer.android.com](https://developer.android.com/guide/components/activities/intro-activities).