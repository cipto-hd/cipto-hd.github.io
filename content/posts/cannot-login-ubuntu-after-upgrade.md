---
title: "Cannot login ubuntu after upgrade"
date: 2014-04-18T09:40:00Z
subtitle: ""
slug: ""
tags: ["computer", "ubuntu", "english", "upgrade", "login"]
aliases: ["/2014/04/cannot-login-ubuntu-after-upgrade.html"]
type: post
---

Sometime ago, I had a problem, ie cannot login to ubuntu 14.04, but now I have succeed to login ^\_^. This problem also have happened to older Ubuntu version, where I get to know the solution. In my case there was a mismatch on desktop config from the user I login and the available desktop config. Here what i did: ([username] just as a placeholder)

First I check the lightdm.log:

```
-----------------------------------
sudo nano /var/log/lightdm/lightdm.log
---------------------------------------
```

I had a suspicion on these lines:

```
..................
    [+27.41s] DEBUG: Session pid=1114: User [username] authorized
    [+27.42s] DEBUG: Session pid=1114: Greeter requests session ubuntu
    [+27.42s] DEBUG: Seat: Failed to find session configuration ubuntu
    [+27.42s] DEBUG: Seat: Can't find session 'ubuntu'
..................
```

why did lightdm look for "ubuntu" session? This was because of [username] which i use its xsession is ubuntu. It was on /var/lib/AccountsService/users/[username]:

```
---------------------------------------
[User]
Language=en_US
FormatsLocale=id_ID.UTF-8
XSession=ubuntu <=====================  THIS ONE
Background=/home/[username]/Pictures/Wallpapers/1781785_10201241375132193_1896210726_o.jpg
SystemAccount=false

[InputSource0]
xkb=us
---------------------------------------
```

Then I look at the xsession in folder /usr/share/xsessions. There was only gnome.desktop, no ubuntu.desktop.
So that I changed the content of /var/lib/AccountsService/users/[username]:

```
from XSession=ubuntu to XSession=gnome
```

Problem solved ^\_^
