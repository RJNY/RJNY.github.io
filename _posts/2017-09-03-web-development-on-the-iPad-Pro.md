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
experiences with iOS and Android terminals. Surprisingly enough, one stood out with exceptional reviews,
[Blink](https://itunes.apple.com/us/app/blink-shell-mosh-ssh-terminal/id1156707581?mt=8).

Basically, this is a terminal app that allows you to SSH or Mosh into another machine, and it
totally works!

## What do I need?

- an iPad (any iPad _should_ do)
- a bluetooth or iPad keyboard
- [Blink](https://itunes.apple.com/us/app/blink-shell-mosh-ssh-terminal/id1156707581?mt=8).
- A PC, Mac or a [VPS](https://www.digitalocean.com/pricing/) (requires additional setup)
- Bash & Vim know-how. I believe there are pretty good text editors that'll work, but I didn't need
  them so I wouldn't be the person to ask)
- (optional) [install mosh](https://mosh.org/#getting) on the machine you're SSH-ing into

## Setup

### SSH using host configuration

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

### SSH manually

you can simply SSH into your machine by typing `ssh obiwan@192.168.x.x`
or Mosh into it with `mosh obiwan@192.168.x.x --server=/usr/local/bin/mosh-server`

If your mosh-server isn't in your PATH, you're gonna have to pass the server path as an argument.
If you installed it via homebrew like I did, the path will be something like `/usr/local/bin/mosh-server`

ex: `mosh obiwan@192.168.x.x --server=/usr/local/bin/mosh-server`

## SSH into your machine

Assuming you followed the above setup, you should not be able to `ssh [host]` or `mosh [host]`.

Earlier I entered 'pit' as my _Host_ alias, so I would need to type `ssh pit` or `mosh pit`
(seewhatididthere?)


## TMUX and Vim

If you made it this far and you're comfortable with Bash and Vim, you should feel right at home.
Navigate to your project and start programming like you normally would.

I have to say, TMUX and Vim run exceptionally on Mosh. I was thouroughly impressed by the
performance. I could honestly see myself developing using an iPad, comfortably.

![image]({{site.url}}/assets/img/ipad-setup.png)

## Running the web server

If you simply try running `rails server`, you're gonna have a bad time. This is because your iPad
cannot connect to your VPS's localhost. you're gonna have to tell rails, node, etc. what ip to serve
to explicitly.

Rails ex:
``` bash
rails server -b 192.168.x.x -p 3000
```

Node ex:
``` bash
HOST=192.168.x.x PORT=3000 webpack-dev-server
```

Once the server is spinning, you just need to visit `http://192.168.x.x:3000` instead of localhost


## Drawbacks

The biggest drawback, and the deal breaker, is that there are no good browser developer tools
available natively on iOS or Android at this time. There is a
[firebug-lite bookmarklet](http://martinkool.com/post/13629963755/firebug-on-ipad-and-iphone) tool
that gives you a javascript DOM inspector, but I found this to be quite buggy. The JavaScript
console rarely works and this is where my journey ended.

## Conclusion

**So is it good for web development?** _Not yet._

The lack of a native web inspector is a critical missing component. Your only options are the buggy
firebug bookmarklet or connect to a laptop via usb for the web inspector, which defeats the entire
purpose of development on an iPad in the first place.

There is also the need to always be connected to the internet for a SSH connection. If you lose
internet connection, you're stranded with very limited options of resolution.

Another surprising thing that bugged me is the lack of mouse or trackpad support on the iPad. While it
is a joy to touch the screen for many of my tasks, the need to touch the screen for web development
sucks all the joy out of this magical experience.

**Is it for me?** _Not yet_

Simply put, the only thing the iPad has going for it over the macbook is it's form-factor, touch
screen and LTE option. There is nothing I can't already do on a macbook that I can't do on an iPad
(except touch the screen apparently).

I will be returning my iPad Pro 10.5". The iPad has definitely become a contender in the realm of
professional tools. I believe that this could be the machine that most professionals use for their
day-to-day tasks. You'll find many YouTube videos of how the iPad helps business professionals,
music producers and artists alike, so I'll spare you the details of how amazing the iPad is for the
day-to-day, mundane.

That aside, I love the idea of carrying an iPad instead of my 15" MacBook Pro. I even thought about
trading it in for the LTE version so I could have access to my VPS from anywhere and not be reliant
of slow public WiFi connections.

I am looking forward to the day where the iPad is a full laptop replacement, but today is not that
day. Happy hacking!
