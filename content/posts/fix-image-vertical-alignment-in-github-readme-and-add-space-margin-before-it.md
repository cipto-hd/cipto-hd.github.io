+++
title = 'Fix Image Vertical Alignment in Github Readme and Add Space Margin Before It'
date = 2024-01-23T10:17:44+07:00
type = "post"
draft = false
+++

![fix image vertical alignment](/images/fix-image-vertical-alignment-and-add-space-before-it.jpg)

It took me some time to know that github overwrite image style attribute value, this value `style="margin-left:15px; vertical-align: middle"` was overwritten by this `style="max-width:100%". See below code snippets:
`

```html
Made with &#10084;&#65039; using wonderful
<a target="_blank" href="http://gohugo.io/"
  ><img
    src="https://github.com/cipto-hd/github-assets/raw/main/assets/hugo.svg"
    height="20px"
    alt="hugo logo"
    style="margin-left:15px; vertical-align: middle"
/></a>
```

```html
Made with &#10084;&#65039; using wonderful
<a target="_blank" href="http://gohugo.io/"
  ><img
    src="https://github.com/cipto-hd/github-assets/raw/main/assets/hugo.svg"
    height="20px"
    alt="hugo logo"
    style="max-width:100%"
/></a>
```

It turns out that we must use `align` attribute to center image vertically to fix image vertical alignment and use `&nbsp;` html entity to add some space before it. And tada below is the code for this fix:

```html
Made with &#10084;&#65039; using wonderful &nbsp;
<a target="_blank" href="http://gohugo.io/"
  ><img
    src="https://github.com/cipto-hd/github-assets/raw/main/assets/hugo.svg"
    height="20px"
    alt="hugo logo"
    align="center"
/></a>
```

Hopefully this info would be helpful for others. Thanks.
