---
layout: post
title: How to fix Android Virtual Device error on Ubuntu 18.04
categories: Android Ubuntu
tags: Android Studio KVM permission denied AVD manager ubuntu 18.04
comments: true
---

<div class="message">
  <strong>/dev/kvm device: permission denied</strong> is the error that I got while trying to run Android Virtual Device(AVD) 
  on a fresh install of Ubuntu 18.04.
</div>

![Error](/public/images/2018-08-13-fix-avd-error-ubuntu-18-04/1.png "Error")

The error message also shows a hint on what could be wrong: `Grant current user access to /dev/kvm.` A quick google search reveals that this is a common problem.

The easiest way to fix this would be to install qemu-kvm and then give appropriate permission to the current user.

Install `qemu-kvm`.

{% highlight bash %}
$ sudo apt install qemu-kvm
{% endhighlight %}

Use the adduser command to add your user to the kvm group.

{% highlight bash %}
$ sudo adduser <username> kvm
{% endhighlight %}


And then own the file /dev/kvm using chown.

{% highlight bash %}
$ sudo chown <username> /dev/kvm
{% endhighlight %}

![Fix error](/public/images/2018-08-13-fix-avd-error-ubuntu-18-04/2.png "Fix error")

After the above steps the AVD should work as expected.

![Android emulator boots](/public/images/2018-08-13-fix-avd-error-ubuntu-18-04/3.png "Android emulator boots")