---
layout: post
title: Creating notifications on Android
categories: Android
tags: Android, Creating, Notification, Builder, Manager, Service
comments: true
---

![Create notification](/public/images/android-notifications/notifcation_poster.png)

<div class="message">
    Notifications are an important way to display information when your app is not being used.  
</div>

A notification is a message that is shown outside of an application window by the android system to inform the user about 
information like communication from other people, reminders and other timely information. 

Code for the this tutorial is available on my [GitHub](https://github.com/chirathr/Android_Example_Repo).

### Notification layout

<img src="/public/images/android-notifications/notification-callouts_2x.png" alt="natification layout" style="padding: 20px 0;" width="500px"/>

The most common parts of a notification are indicated in figure above as follows:

1. **Small icon:** This is required and set with `setSmallIcon()`.
2. **App name:** This is provided by the system.
3. **Time stamp:** This is provided by the system but you can override with `setWhen()` or hide it with `setShowWhen(false)`.
4. **Large icon:** This is optional (usually used only for contact photos; do not use it for your app icon) and set with `setLargeIcon()`.
5. **Title:** This is optional and set with `setContentTitle()`.
6. **Text:** This is optional and set with `setContentText()`.

### Creating a notification

Creating a basic notification for Android is pretty simple. The first step is to get the notification manger service 
which is the system service that handles notifications.

##### Notification manager service

Get the notification manager system service.

{% highlight java %}
NotificationManager notificationManager =
        (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
{% endhighlight %}

##### Notification channels

To show a notification in Android Oreo and above we need to create a notification channel. A user can disable or
 fine tune the visual and auditory options for each channel separately.

<img src="/public/images/android-notifications/notification_channel.png" alt="Heads-up notification" width="400px"/>


{% highlight java %}

// Create the NotificationChannel, but only on API 26+ because the NotificationChannel class is new and not in the support library
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    CharSequence name = "My notification channel";
    String description = "Notification channel description";
    int importance = NotificationManager.IMPORTANCE_HIGH;
    NotificationChannel channel = new NotificationChannel(
                                    CHANNEL_ID, name, importance);
    channel.setDescription(description);
    // Register the channel with the system; you can't change the importance or other notification behaviors after this
    NotificationManager notificationManager = getSystemService(
                                                NotificationManager.class);
    notificationManager.createNotificationChannel(channel);
}
{% endhighlight %}

Setting the importance to `IMPORTANCE_HIGH` will make the notification pop up as a `Heads-up notification`.

##### Load Bitmap image for Large Icon

We can also include a large icon in the notification, but it needs to be of type Bitmap.

{% highlight java %}
Bitmap largeIcon = BitmapFactory.decodeResource(getResources(), R.drawable.profile_pic);
{% endhighlight %}

##### Create a pending Intent

Here we create a `PendingIntent` that is used by the notification manger to launch the app when the notification is clicked.

{% highlight java %}
Intent startActivityIntent = new Intent(this, MainActivity.class);

PendingIntent pendingIntent = PendingIntent.getActivity(
        this,
        PENDING_INTENT_ID,
        startActivityIntent,
        PendingIntent.FLAG_UPDATE_CURRENT
);
{% endhighlight %}

##### Build the notification

Next we will create the notification using the `NotificationCompat.Builder` and set the notification's content and channel.
    
{% highlight java %}

// Build the notification
NotificationCompat.Builder notificationBuilder =
    new NotificationCompat.Builder(this, CHANNEL_ID)
            .setSmallIcon(R.drawable.ic_launcher_foreground)
            .setLargeIcon(largeIcon)
            .setContentTitle("Hi there!")
            .setContentText("Message from Chirath")
            .setContentIntent(pendingIntent)
            .setAutoCancel(true);   // close the notification on click
{% endhighlight %}

`setAutoCancel(true)` will dismiss the notification when user clicks on it.

##### Set notification priority

We had already set the priority as high when we created the notification channel. But notification channels are not supported
by devices running Nougat and below. So for these devices we need to set the priority using the `setPriority()` method.

{% highlight java %}
if (Build.VERSION.SDK_INT < Build.VERSION_CODES.O) {
    notificationBuilder.setPriority(NotificationCompat.PRIORITY_HIGH);
}
{% endhighlight %}

##### Show the notification

The last step is to call the notify method and pass in unique id and the result of  
`NotificationCompat.Builder.build()`.

{% highlight java %}
notificationManager.notify(NOTIFICATION_ID, notificationBuilder.build());
{% endhighlight %}

<img src="/public/images/android-notifications/notification_frame.png" alt="Notification" width="400px"/>

Now when the app opens, a notification should popup like above.

More info about creating Android notifications can be found at [developer.android.com](https://developer.android.com/guide/topics/ui/notifiers/notifications).