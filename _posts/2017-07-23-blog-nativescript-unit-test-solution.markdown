---
layout: post
title: "NativeScript unit test problems solved"
date:   2017-07-23 20:57:00 +0200
subtype: blog
tags:
- mobile
- nativescript
---

After having a lot of problems making my unit tests run and not to break my project
(after fixing some npm-issues my tests did run but my app did not build for android
  anymore). I learned a lot of stuff: one reason for my building problems were
some added hooks ( it took me some time to figure that our because the hooks
  directory is in .gitignore and for that reason was out of my mind too ;-)).
After a lot of investigation for the reason of this log

```npm ERR! enoent ENOENT: no such file or directory, rename```

I found the dead simple solution: just update npm

```npm update npm -g```

After that ```tns test init``` worked like a charm and my test run fine (without
  breaking my builds).
