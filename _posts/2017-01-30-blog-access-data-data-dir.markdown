---
layout: post
title:  "Accessing /data/data - directory on android phone"
date:   2017-01-30 20:38:00 +0200
subtype: blog
tags:
- mobile
- android
---

While developing an android app it is useful to access the app directory which is
stored in /data/data.
Without rooting the phone you can access the files with adb:
{% highlight bash %}
adb shell
run-as com.your.packagename
cd com.your.packagename
{% endhighlight %}
