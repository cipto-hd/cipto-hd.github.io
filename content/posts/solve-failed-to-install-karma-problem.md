---
title: 'Solve "failed to install karma" problem'
date: 2014-04-26T16:39:00Z
subtitle: ""
slug: ""
tags: ["unit test", "karma", "english", "angularjs", "web"]
aliases: ["/2014/04/solve-failed-to-install-karma-problem.html"]
type: post
---

Actually I feel embarrassed that I write about programming but having a blog not completely and correctly managed (there are some typos and their faulty friends).
Ok, now I would like to focus on solving "failed to install karma" problem. I faced this problem when I ran karma unit test while following along angularjs tutorial.
I was confused to find out that I could not run unit test using this command "npm test". Karma npm package had been installed (globally) using "sudo npm -g install karma". So what's the problem?

After hours of googling for answer, I finally managed to tackle that problem, initially after looking this link `http://stackoverflow.com/a/23044629/3451126`. In my understanding, in order to accomplish unit test, "npm test" was trying to call "karma", but the command was not found. It turned out that "karma cli command" is not installed by default, despite of the fact that karma package has been already installed. To successfully run unit test on angularjs, we also have to install karma-cli using this command: "sudo npm -g install karma-cli". There are also several other steps that need to be accomplished. I will include them on my recap below.

To recap the steps needed to run unit test on angularjs, I will outline them below:

1. First install karma main npm package using this command "sudo npm -g install karma"
2. Install karma cli command by executing "sudo npm install -g karma-cli"
3. Install karma jasmine using "sudo npm install -g karma-jasmine --save-dev"
4. Install browser launcher package, in my case I use chrome, so i used "sudo npm install karma-chrome-launcher --save-dev". If you use firefox, just replace chrome with firefox.
   Hopefully, this post help you! ^\_^.

By the way, this is my screenshot on karma unit test:

![](/img/karma_unit-test.png)
