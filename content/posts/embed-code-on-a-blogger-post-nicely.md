---
title: "Embed code on a blogger post nicely"
date: 2014-04-22T17:17:00Z
subtitle: ""
slug: ""
tags: ["featured", "embed code", "english", "prettify", "web"]
aliases: ["/2014/04/embed-code-on-blogger-post-nicely.html"]
type: post
---

![prettify](/img/prettify.jpg)

You want to display source code or text command on a blogger post nicely? Don’t worry! You can use Prettify script to highlight code in your web pages. Some tutorials would suggest to directly embed Presttify into template file. But it would clutter your template code. There is a more elegant way, ie using blogger widget.

Here are the steps:

1. At the Blogger.com Blog Administration, click “Layout” in the left navigation bar.
2. Click “Add Gadget” somewhere in your layout, preferably somewhere at the bottom of the page.
3. Choose “HTML/JavaScript” from the “Basics” tab.
4. Give your gadget a name (i.e. “PrettyPrint”) and paste the code from below into the “Content” text area.

```
<script src="https://cdn.rawgit.com/google/code-prettify/master/loader/run_prettify.js"></script>
```

5. To display code snippet on your post, encode your code snippet into html entities. You can use online tool, for example htmlentities.net.
6. On post editing/creating screen, make sure you are on HTML mode, not Compose mode , then just place the code inside of a `<pre class=“prettyprint”>…</pre>` tag.

For more info, check this link:
[Google Code Prettify](https://github.com/google/code-prettify)
