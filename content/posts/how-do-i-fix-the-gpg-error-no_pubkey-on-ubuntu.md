---
title: 'How do I fix the GPG error "NO_PUBKEY" on Ubuntu'
date: 2015-09-25T07:04:00Z
subtitle: ""
slug: ""
tags: ["error", "ubuntu", "english", "gpg", "no_pubkey"]
aliases: ["/2015/09/how-do-i-fix-gpg-error-nopubkey-on.html"]
type: post
---

{{< figure src="/img/no pub key error.png" title="GPG error NO_PUBKEY" >}}

You have seen error like this below when adding a new repository on Ubuntu Software & Updates -> Other software?

```
 GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 409C8B51283EC8CD
```

Don't worry? I will share two solution how to tackle it. Here they are :

1. The quick way is by running command on terminal. Execute the following commands in terminal (replace key with the key on error message after NO_PUBKEY ):

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 409C8B51283EC8CD
```

and then update

```
sudo apt-get update
```

2.  Using grapical application i.e. Y-PPA-Manager
1.  To install it, first add the webupd8 repository for this program:
    ```
    sudo add-apt-repository ppa:webupd8team/y-ppa-manager
    ```
1.  Update your software list and install Y-PPA-Manager:
    ```
    sudo apt-get update
    sudo apt-get install y-ppa-manager
    ```
1.  Run `y-ppa-manager`.
    When the main y-ppa-manager window appears, click on "Advanced."
    From the list of advanced tasks, select "Try to import all missing GPG keys" and click OK.

I hope you enjoy your journey on Ubuntu. Cheers ^\_^
