---
layout: post
title: "Web Development on the iPad Pro"
comments: true
date: 2017-09-03
youtubeId: 2XUpbvkMB-k
---

I recently decided to pick up an iPad Pro (10.5 inch) with the apple pencil. I tend to play a lot of
video games and I was hoped the iPad would spark some latent creative abilities. I downloaded a few
applications for drawing, note taking and fiddled with garageband, but seeing that I have garageband
on my mac, type way faster than I could ever hand write and sketch with a lead pencil and paper, I
was beginning to think about returning it. While I do value the super slim form factor, I could
never replace my macbook since I can't do any web development on my iPad, right?

## Blink

I checked out the app store for some terminal apps. They were all pretty lack-luster from my past
experiences with iOS/Android terminals. Surprisingly enough, one stood out with exceptional reviews,
[Blink](https://itunes.apple.com/us/app/blink-shell-mosh-ssh-terminal/id1156707581?mt=8).

Basically, this is a terminal app that allows you to SSH or Mosh into another machine, and it
totally works!

## What do I need?

- an iPad (any iPad _should_ do)
- a bluetooth or iPad keyboard
- [Blink](https://itunes.apple.com/us/app/blink-shell-mosh-ssh-terminal/id1156707581?mt=8).
- A PC, Mac or a [VPN](https://www.digitalocean.com/pricing/) (requires additional setup)
- Bash & Vim know-how. I believe there are pretty good text editors that'll work, but I didn't need
  them so I wouldn't be the person to ask)
- (optional) [install mosh](https://mosh.org/#getting) on the machine you're SSH-ing into

## Setup

### SSH/Mosh using host configuration

Open up Blink, type config to enter the settings.

Select Hosts and click the '+' on the top right to add a new host. This will be your remote machine
you want to SSH into.

SSH
- Host: Alias for your host (I used "pit", you'll understand why in a bit.)
- HostName: your IP (ex: 192.168.x.x)
- port: I left this blank
- user: your machines user (ex: obiwan)

Mosh
- Server: If your mosh-server isn't in your PATH, you're gonna have to fill the path out yourself.
  If you installed it via homebrew like I did, it'll be something like `/usr/local/bin/mosh-server`

![image]({{site.url}}/assets/img/blink-settings.png)

### SSH/Mosh manually

you can simply SSH into your machine by typing `ssh obiwan@192.168.x.x`
or Mosh into it with `mosh obiwan@192.168.x.x --server=/usr/local/bin/mosh-server`

If your mosh-server isn't in your PATH, you're gonna have to pass the server path as an argument.
If you installed it via homebrew like I did, the path will be something like `/usr/local/bin/mosh-server`

ex: `mosh obiwan@192.168.x.x --server=/usr/local/bin/mosh-server`

## SSH/Mosh into your machine

Assuming you followed the above setup, you should not be able to `ssh [host]` or `mosh [host]`.

Earlier I entered 'pit' as my _Host_ alias, so I would need to type `ssh pit` or `mosh pit`
(seewhatididthere?)


## TMUX and Vim

If you made it this far and you're comfortable with Bash and Vim, you should feel right at home.
Navigate to your project and start programming like you normally would.

I have to say, TMUX and Vim run exceptionally on Mosh. I was thouroughly impressed by the
performance. I could honestly see myself developing using an iPad, comfortably.

![image]({{site.url}}/assets/img/ipad-setup.png)

## Drawbacks

The biggest drawback, and the deal breaker, is that there are no good browser developer tools
available natively on iOS or Android at this time. There is a
[firebug-lite bookmarklet](http://martinkool.com/post/13629963755/firebug-on-ipad-and-iphone) tool
that gives you a javascript DOM inspector, but I found this to be quite buggy. The JavaScript
console rarely works and this is where my journey ended.

## Conclusion

The iPad has definitely become a contender in the realm of professional tools. I believe that this
could be the machine that most professionals use for their day-to-day tasks. You'll find many
YouTube videos of how the iPad helps business professionals, music producers and artists alike, so
I'll spare you the details of how amazing the iPad is for the day-to-day, mundane.

So is it good for web development? _Not yet._

The lack of a native web inspector is a critical missing component. There is also the need to always
be connected to the internet for a SSH/Mosh connection.

That aside, I love the idea of carrying an iPad instead of my 15" MacBook Pro. I even thought about
trading it in for the LTE version so I could have access to my VPN from anywhere and not be reliant
of slow public WiFi connections. I am looking forward to the day where the iPad is a full laptop
replacement, but today is not that day. Happy hacking!
