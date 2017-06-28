---
layout: post
title:  "New job for old MacMini"
date:   2016-12-10 20:38:00 +0200
tags:
- admin
---

My powerpc MacMini is retired for many years now. After trying to use it as media server
I realized that I did not use it a lot and working with the very old version of MacOS
did not make fun.
After a long time of being retired I wanted to give the old hardware a new chance.
What could this old hardware be useful for?

What about using it as my NAS? Yes sounds great and is much cheaper than a Synology
(ok that comparison is not fair, a Synology is much better and for more than two
years now I am thinking about buying one because it is an awesome product).

As my OS I chose Debian.
After installing the PowerPc version with Xfce I needed to activate ssh:
{% highlight bash %}
# let's do this as root
su
apt-get update

# install sudo and add your user to this group
apt-get install sudo
adduser USERNAME sudo

# install ssh server
apt-get install open-ssh-server
{% endhighlight %}

Now I need login without password. I like the tool ssh-copy-id (which is part of the openssh-client package):
{% highlight bash %}
ssh-copy-id USERNAME@HOST
{% endhighlight %}
(if you have more than one key you can choose the key with the -i option)

To make connecting a little bit more comfortable I added an alias to my .zshrc:
{% highlight bash %}
alias sshserver='USERNAME@HOST'
{% endhighlight %}
and reloaded with
{% highlight bash %}
source .zshrc
{% endhighlight %}

Now my ssh connection works fine with
{% highlight bash %}
sshserver
{% endhighlight %}

To test WakeOnLan I needed the MacAdress:
{% highlight bash %}
ifconfig -a
{% endhighlight %}
