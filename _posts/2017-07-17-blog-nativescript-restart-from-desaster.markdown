---
layout: post
title: "NativeScript: restart project from template after a total mess"
date:   2017-07-17 21:36:00 +0200
subtype: blog
tags:
- mobile
- nativescript
---

I don't know how it happened but my NativeScript project seems to be messed up totally.
I can not get it run on android anymore it always complains about
{% highlight bash %}
Exception: The NativeScript CLI requires Android runtime 1.5.0 or later to work properly.
{% endhighlight %}
all the time although the newest runtime is installed.

After a lot of investigation and no chance to get it running anymore I decided to
restart the project from a fresh template.
This is a checklist:

* update app id in ```package.json```
* Install dependencies (```tns plugin add ...```)
* copy ts-Sources
* update necessary Android permissions in Manifest
* copy platform specific resources
