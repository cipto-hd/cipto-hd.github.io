---
title: "How to install node on Ubuntu (latest stable node and older one/s)"
date: 2015-09-30T06:45:00Z
subtitle: ""
slug: ""
tags: ["npm", "ubuntu", "node", "english", "nvm"]
aliases: ["/2015/09/how-to-install-node-on-ubuntu-latest.html"]
type: post
---

![](/img/nodejs-green.png)

As quoted from https://nodejs.org/, Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient. Node.js' package ecosystem, npm, is the largest ecosystem of open source libraries in the world.

In its official site, there is a link for downloading node archive to install it in our Ubuntu machine. But I prefer the NVM way for installing node, because we can have more than one node version on our machine. Why do we have to bother our ourselves? With the current stable version of node, we can try the latest features, but sometimes there are node packages that need older version, so that by installing NVM we can cope with these two condition.

To install NVM you could use the install script using cURL:

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.27.1/install.sh | bash
```

or Wget:

```
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.27.1/install.sh | bash
```

Now to install latest stable node, run this:

```
nvm install stable
```

To install spesific version of node, for example 0.10 (at the of writing, i think this version is commonly used), run this:

```
nvm install 0.10
```

To use a certain version, run these:

```
nvm use stable
nvm use 0.10
```

To check node version which is currently active:

```
node --version
```

Upon completing node installation we also get npm (node package manager) installed. Check it with this:

```
npm --version
```

To set the default node version touse, in case of we have installed more than one version, run this:

```
nvm alias default 0.10
```

Replace 0.10 with your preferred node version.

I hope this post will be usefull for many beginner software developers. If you don't mind you can drop some comments. Success for you! And me for sure ^\_^
