---
layout: post
title: "NativeScript unit test problems"
date:   2017-07-13 09:55:00 +0200
subtype: blog
tags:
- mobile
- nativescript
---

While my first NativeScript app is having some progress I wanted to have some tests for it.
So I started to read the [tutorial](https://docs.nativescript.org/tooling/testing) and followed
its steps:

* ```tns test init```
* ```npm i @types/jasmine --save-dev```
* ```tns test ios --emulator```

But the only result was a lot a lot of errors on cli complaining about a file missing (node_pre-gyp).
After some investigation I realized that even in a simple template app I had the same issues.
That's why I suspected that it is NativeScripts fault and wanted to open a bug report.
While collecting the logs for it I saw that already while initializing the projects for tests
there showed up some errors with node-pre-gyp.
The following steps helped me out:

* I deleted my .npm in my home but had some other problems like ```cwd = process.cwd(); Error:
  ENOENT: no such file or directory, uv_cwd``` after that so I did
* ```sudo npm cache clean -f``` and ```sudo npm install -g n```
* ```tns test init``` still showed some problems with ```node-pre-gyp``` and ```abbrev``` so I
  copied these dependencies from my .npm to app/node_modules/fsevents

and viola my tests are running now.  
