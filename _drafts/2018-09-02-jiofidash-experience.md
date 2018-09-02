---
layout: post
title: Developing and releasing my first Android app
categories: Android
tags: Android, JioFi6, WiFi, Battery, Status, SSID, Password, Notifications, RecyclerView, Fragments, Dialogs, AsyncTasks
comments: true
---

![JioFiDash](/public/images/2018-08-28-jiofidash-experience/jiofi-dash-promotion.png)

<a href="https://play.google.com/store/apps/details?id=com.chirathr.jiofidash" target="_blank">
    <img src="/public/images/2018-08-28-jiofidash-experience/available-on-google-play.png" alt="Battery status" style="border: 1px solid #e8e8e8; display: inline; margin: 20px 5px 0 5px;" width="200px"/>
</a>

After a month of coding, bug fixing and testing, I have managed to release my app on the PlayStore.

The initial weeks were spend watching video tutorials and going through the developer docs. After week two 
I decided to build the JioFiDash app. There were lots of hurdles along the way like reverse 
engineering the API required to get data from the JioFi device. I had to learn lots of new concepts like RecyclerView, 
Fragments, Dialogs, AsyncTasks and various ways to do network calls(Using Volley and HttpURLConnection). 
I also had to parse HTML from the admin web UI using JSoup and get the CSRF tokens required to make POST requests.

In the end, It was a fun learning experience and I was able to learn many of the important concepts required to develop and
release an Android apps in the PlayStore.

For those who are interested in learning Android development, I would recommend this course from 
[Udacity](https://classroom.udacity.com/courses/ud851). You can also follow the developer guide available at 
[developer.android.com](https://developer.android.com/guide/).

#### Screenshots

<div style="display: inline-block;">
    <img src="/public/images/2018-08-28-jiofidash-experience/1.png" alt="Battery status" style="border: 1px solid #e8e8e8; display: inline; margin: 20px 5px 0 5px;" width="320px"/>
    <img src="/public/images/2018-08-28-jiofidash-experience/2.png" alt="Wifi ssid, password" style="border: 1px solid #e8e8e8; display: inline; margin: 20px 5px 0 5px;" width="320px"/>
    <img src="/public/images/2018-08-28-jiofidash-experience/3.png" alt="change ssid password" style="border: 1px solid #e8e8e8; display: inline; margin: 5px 5px 0 5px;" width="320px"/>
    <img src="/public/images/2018-08-28-jiofidash-experience/4.png" alt="Restart and WPS" style="border: 1px solid #e8e8e8; display: inline; margin: 5px 5px 0 5px;" width="320px"/>
    <img src="/public/images/2018-08-28-jiofidash-experience/5.png" alt="Notifications" style="border: 1px solid #e8e8e8; display: inline; margin: 5px 5px 5px 5px;" width="320px"/>
    <img src="/public/images/2018-08-28-jiofidash-experience/6.png" alt="Select device" style="border: 1px solid #e8e8e8; display: inline; margin: 5px 5px 5px 5px;" width="320px"/>
</div>
