---
layout: post
title: "NativeScript hickups"
date:   2017-07-07 21:37:00 +0200
subtype: blog
tags:
- mobile
- nativescript
---

Yesterday my NativeScript made me feel crazy. Suddenly my project did not build anymore.
Wired error occured like
{% highlight bash %}
error TS2304: Cannot find name 'Promise'.
{% endhighlight %}

I suspect a wired library dependency (incompatible versions).
After a lot of investigation I learned a lot:

* removing the ```node_modules-folder``` and using ```tns install```to reinstall all dependencies can help
* the app-folder contains a second ```package.json```which was messed up in my case
* after updated to the newest nativescript version I realized that ```livesync```is deprecated now (you can use ```tns run ios --watch```instead)
* using ```tns platform clean ios```is a good idea if something is messed up
* updating to angular 4 was very easy :-)
