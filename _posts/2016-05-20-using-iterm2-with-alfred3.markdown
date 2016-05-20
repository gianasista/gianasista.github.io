---
layout: post
title:  "Integrating iTerm2 into Alfred"
date:   2016-05-20 19:19:18 +0200
tags:
- iterm
- alfred
---

I have installed iTerm with Homebrew (brew cask) and wanted to integrate it with Alfred.
On GitHub I found [this](https://github.com/stuartcryan/custom-iterm-applescripts-for-alfred/) awesome little project which helped me out
and here is my custom script I am using in Alfred (needed to change the iTerm path)

{% highlight applescript %}
-- This is v0.4 of the custom script for AlfredApp for iTerm 2.1.1
-- Please see https://github.com/stuartcryan/custom-iterm-applescripts-for-alfred/
-- for the latest changes.

-- Please note, if you store the iTerm binary in any other location than the Applications Folder
-- please ensure you update the two locations below (in the format of : rather than / for folder dividers)
-- this gets around issues with AppleScript not handling things well if you have two iTerm binaries on your system... which can happen :D

on alfred_script(q)
	if application "iTerm" is running then
		run script "
			on run {q}
				tell application \":opt:homebrew-cask:Caskroom:iterm2:2.0.0:iTerm.app\"
					activate
					try
						set myterm to the first terminal
					on error
						set myterm to (make new terminal)
					end try
					tell myterm
						set mysession to (launch session \"Default Session\")
						tell mysession to write text q
					end tell
				end tell
			end run
		" with parameters {q}
	else
		run script "
			on run {q}
				tell application \":opt:homebrew-cask:Caskroom:iterm2:2.0.0:iTerm.app\"
					activate
					tell the first terminal
						tell the last session to write text q
					end tell
				end tell
			end run
		" with parameters {q}
	end if
end alfred_script
{% endhighlight %}