---
layout: post
title: My First Android App - JioFiDash
categories: Android
tags: Android, Development, MaterialDesign, Volley, JioFi, JioFi6, Jio
comments: true
---

![JioFiDash Poster](/public/images/2018-08-24-first-android-app-jiofi-dash/JiofiDash-poster.jpg)

<div class="message">
    Almost ready with my first Android app - A dashboard for JioFi 6 (JMR815).
</div>

I always wanted to publish an app in the PlayStore. So, one month back I decided to learn enough of the Android 
framework to be able to develop a simple app. Initially all the ideas I had seemed to be already there in the PlayStore. 
One day, I was have having trouble with my JioFi modem, the network speeds were low and I needed check the status often. 
That's when I realized I could make an app for this device as no other app out there supports the latest 
`JioFi 6 (JMR815)` device.

![JioFi 6](/public/images/2018-08-24-first-android-app-jiofi-dash/jiofi6.jpeg)

<div class="message">
    <strong>Note: </strong>This app only supports JioFi 6(JMR815).
</div>

In all fairness, I did build few apps before, but all of them were frankensteined together with code I found on the internet. 
So this would be my first real experience building an app. Initially I just wanted something simple with the features I 
want like battery status, connection speed and an option to restart. But soon I came up a list of important 
features that would be useful.

#### Features

These features have been successfully implemented. Initially it was quite hard since I had to reverse engineer 
the api from the Javascript code of the admin panel provided by JioFi. With some patience and a bit of help from 
Chrome dev tools, I was able to get information about the api and the endpoints to send the actual post request 
to make all this possible.

- Battery status
- Battery full and low notification
- Realtime data speeds
- Data usage
- Network band and signal strength
- Devices connected to WiFi
- Block devices on WiFi
- Change WiFi ssid and password
- Restart JioFi
- Enable WPS button
- Open Admin web Ui

#### The UI

I wanted the app to have a simple UI that looked good. So I used `MaterialComponents` from the material design
library. Here are few screenshots:

<div style="display: inline-block;">
<img src="/public/images/2018-08-24-first-android-app-jiofi-dash/main_activity.png" alt="Card List Item" style="border: 1px solid #e8e8e8; display: inline; margin: 0 5px 20px 5px;" width="300px"/>
<img src="/public/images/2018-08-24-first-android-app-jiofi-dash/wifi-settings.png" alt="Card List Item" style="border: 1px solid #e8e8e8; display: inline; margin: 0 5px 20px 5px;" width="300px"/>
<img src="/public/images/2018-08-24-first-android-app-jiofi-dash/settings.png" alt="Card List Item" style="border: 1px solid #e8e8e8; display: inline; margin: 20px 5px 5px 5px;" width="300px"/>
<img src="/public/images/2018-08-24-first-android-app-jiofi-dash/on_boarding.png" alt="Card List Item" style="border: 1px solid #e8e8e8; display: inline; margin: 20px 5px 5px 5px;" width="300px"/>
</div>

The app is almost ready to to be published. If anyone want's to try it out, feel free to contact me.