---
layout: post
title:  "Nice android libs"
date:   2016-07-27 11:30:00 +0200
subtype: blog
tags:
- android
- coding
---

While working on my new android app I found two nice libraries which I started to use.

The first one is [Timber](https://github.com/JakeWharton/timber). It is just a class which is very helpful and will be part
of every new android project I will write.
I am using it to log to a file in debug mode with [logback-android](https://github.com/tony19/logback-android).
After adding my FileLoggingTree in my Application class
{% highlight java %}
Timber.plant(new FileLoggingTree());
{% endhighlight %}
logging is a easy as this
{% highlight java %}
Timber.i("MyLogText");
{% endhighlight %}

The second one is [Butterknife](http://jakewharton.github.io/butterknife/). I have been using RoboGuice until then but was always
bothered because it uses reflection. [Butterknife](http://jakewharton.github.io/butterknife/) is exactly what I need.
Code is generated for the bindings like
{% highlight java %}
@BindView(R.id.tagList) ListView tagList;
{% endhighlight %}
