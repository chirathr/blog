---
layout: post
title: Creating notification in Android
categories: Android
tags: Android, Creating, Notification, Builder, Manager, Service
comments: true
---

<div class="message">
    Notifications are an important way to display information when your app is not being used.  
</div>

A notification is a message that is shown outside an application window by the android system to inform the user about 
information like communication from other people, reminders and other timely information. 

### Notification layout

<img src="/public/images/android-notifications/notification-callouts_2x.png" alt="natification layout" style="padding: 20px 0;" width="500px"/>


The most common parts of a notification are indicated in figure above as follows:

- **Small icon:** This is required and set with `setSmallIcon()`.
- **App name:** This is provided by the system.
- **Time stamp:** This is provided by the system but you can override with `setWhen()` or hide it with `setShowWhen(false)`.
- **Large icon:** This is optional (usually used only for contact photos; do not use it for your app icon) and set with `setLargeIcon()`.
- **Title:** This is optional and set with `setContentTitle()`.
- **Text:** This is optional and set with `setContentText()`.


### Creating a notification

Creating a basic notification in Android is pretty simple. The first step is to get the notification manger service 
which is the system service that handles notifications.

{% highlight java %}
// Get the notification manager
NotificationManager notificationManager =
        (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
{% endhighlight %}

To show a notification in Android Oreo and above we need to create a notification channel. A user can disable notification
channels instead of all notifications for an app.

{% highlight java %}

// Create the NotificationChannel, but only on API 26+ because
// the NotificationChannel class is new and not in the support library
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
    CharSequence name = getString(R.string.channel_name);
    String description = getString(R.string.channel_description);
    int importance = NotificationManager.IMPORTANCE_DEFAULT;
    NotificationChannel channel = new NotificationChannel(CHANNEL_ID, name, importance);
    channel.setDescription(description);
    // Register the channel with the system; you can't change the importance
    // or other notification behaviors after this
    NotificationManager notificationManager = getSystemService(NotificationManager.class);
    notificationManager.createNotificationChannel(channel);
}

{% endhighlight %}

Next we will create the notification using the NotificationCompat.Builder and set the notification's content and channel.
    
{% highlight java %}
NotificationCompat.Builder mBuilder = new NotificationCompat.Builder(this, CHANNEL_ID)
        .setSmallIcon(R.drawable.notification_icon)
        .setContentTitle(textTitle)
        .setContentText(textContent)
        .setPriority(NotificationCompat.PRIORITY_DEFAULT);
{% endhighlight %}




More info about notifications can be found at [developer.android.com](https://developer.android.com/guide/topics/ui/notifiers/notifications).