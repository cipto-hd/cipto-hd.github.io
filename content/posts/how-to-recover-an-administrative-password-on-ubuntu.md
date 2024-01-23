---
title: "How to recover an administrative password on Ubuntu"
date: 2015-10-06T04:40:00Z
subtitle: ""
slug: ""
tags: ["ubuntu", "recover", "english", "password"]
aliases: ["/2015/10/how-to-recover-administrative-password.html"]
type: post
---

{{< figure src="/img/passwd recover success.jpg" title="administrative password is successfully recovered" >}}

Have you ever lost your Ubuntu administrative password, the password of first user on Ubuntu? Don't worry! It can be recovered. Frankly speaking, I've just recovered my lost password before posting this blog article.

Here the steps are:

First, boot up your Ubuntu machine. You will be greeted with Grub menu. Select advanced option menu entry.
![](/img/grub-menu.jpg)

Secondly, You will see the sub menu with many items. Just select the second entry with recovery mode at the end.
![](/img/grub advanced submenu.jpg)

Then, a recovery menu will appear. Select root menu entry, this way you will get root shell prompt access.
![](/img/recovery-menu.jpg)

Remount the root path with this command:

```
 mount -rw -o remount
```

Issue this command and then set the new password:

```
 passwd your-user-name
```

Hopefully you can recover you password successfully.
