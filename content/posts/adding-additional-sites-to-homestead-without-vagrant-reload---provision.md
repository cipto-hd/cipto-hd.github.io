---
title: "Adding Additional Sites to homestead without vagrant reload --provision"
date: 2017-06-21T12:01:00Z
subtitle: ""
slug: ""
tags: ["laravel", "english", "homestead"]
aliases:
  [
    "/2017/06/adding-additional-sites-to-homestead-without-vagrant-reload---provision.html",
  ]
type: post
---

![Homestead nginx sites config files](/img/additional_sites_homestead.png)

Having used homestead for some time now, I have found that adding additional sites by following the guide at laravel doc quite cumbersome.

I think that it would be less cumbersome if additional site is added by adding additonal nginx configuration directly. I would recap my steps on adding local domain "melati.dev" below:

1. Add melati.dev record to file _/etc/hosts_ in the host machine, host OS. All the below commands were executed at virtual machine, guest OS (steps 2 up to 5)
2. Duplicate the default site configuration _homestead.app_ to _melati.dev_ (it's located at _/etc/nginx/sites-available_)
3. Create symbolic link from sites-vailable to sites-enabled:

```
ln -sf /etc/nginx/sites-available/melati.dev /etc/nginx/sites-enabled/melati.dev
```

4. Edit melati.dev file to reflect what the domain is wanted to be (items needed to be changed: **server_name, root, error_log, ssl_certificate, ssl_certificate_key**)
5. Reload nginx using `sudo invoke-rc.d nginx reload`

That's all what I did to add additional sites in homestead. Hope it would be helpful! Thanks for reading ^\_^ !
