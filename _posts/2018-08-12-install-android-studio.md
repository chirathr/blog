---
layout: post
title: Installing Android Studio in Ubuntu 18.04
categories: Android Ubuntu
tags: Android, Studio, Ubuntu, 18.04
comments: true
---

Learning Android app development was one of the things I always wanted to do. So after graduation I was determined to 
learn Android app development, build an app and publish it in the Google Play Store. The first step in learning 
Android app development is to setup the Android Studio IDE. Installing Android Studio on Ubuntu 18.04 is pretty 
straight forward and the best thing is you don't need to bother with installation of any adb driver.

![Download Android Studio](/public/images/2018-08-14-install-android-studio/android-studio-1.jpg "Download Android Studio")
Download Android Studio from [developer.android.com](https://developer.android.com/studio/).

![Unzip](/public/images/2018-08-14-install-android-studio/android-studio-2.png)
Right click and unzip the file or use the unzip command.

![Unzip](/public/images/2018-08-14-install-android-studio/android-studio-3.png)
{% highlight bash %}
    $ unzip android-studio-ide-181.4886486-linux.zip
{% endhighlight %}

![Execute](/public/images/2018-08-14-install-android-studio/android-studio-4.png)
Change directory into `android-studio/bin` and execute `studio.sh`.

{% highlight bash %}
    $ cd android-studio/bin
    $ ./studio.sh
{% endhighlight %}

![Android studio](/public/images/2018-08-14-install-android-studio/android-studio-5.png)
Android studio should start successfully and you can click `next` download the latest `Android SDK`.

![Android studio](/public/images/2018-08-14-install-android-studio/android-studio-6.png)