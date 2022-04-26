---
title: 'Introducing Modernizr: a Feature Detection JavaScript Library'
date: Mon, 09 Sep 2013 11:13:23 +0000
draft: false
url: /2013/09/09/modernizr-feature-detection-javascript-library/
author: 'Atanas Ruzhin'
summary: ''
tags: ['browser detection javascript', 'html5 browser detection', 'html5 feature detection', 'javascript library', 'modernizr', 'modernizr javascript library', 'zArchive']
---

## Progressive EnhancementAs for a lot of other big companies, at [GroupDocs.com](http://groupdocs.com/) user experience is the most important thing taken into account when developing huge web products. The reasons are quite obvious. It really comes down to the design and user groups a web app targets when choosing cross-browser support and priorities. There is a web development practice called “Progressive Enhancement” which stands behind the idea that all users should have identical experience with websites. Unfortunately, nothing is ever ideal in this world and as much as a developer might try to accomplish results driven by this philosophy there are things that are just impossible to make look or act the same way. You have to take into consideration a lot of different things, like the device resolution, hardware, browser vendor and version, and many other factors. Progressive enhancement is a lot like democracy to me because it cannot be realized exactly as its original model, but you try to recreate it and apply its ideas as much as possible in your workflow. \[caption id="attachment\_3817" align="alignnone" width="584" caption="Modernizr JavaScript Library"\]![Modernizr JavaScript Library](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/modernizr.jpg "Modernizr JavaScript Library")\[/caption\]

## What Is Modernizr All About?[null](http://modernizr.com/download/)is a feature detection JavaScript library for HTML5 and CSS3. In other words, it checks if the client’s browser supports the new goodies that HTML5 and CSS3 have in their bags. One of the reasons I’ve decided to write about this library is the fact that some people misunderstand what exactly Modernizr does. The wrong assumption is that Modernizr is doing browser vendor detection or more specifically that it's sniffing the _navigator.userAgent_ string. Indeed, this was how browser detection was done by devs a few years ago, but it is actually a very unsafe and unreliable way of handling cross-browser issues. It has been considered very poor practice from a long time now. This is mainly due the fact that the _navigator.userAgent_ string contains horribly organized and sometimes wrong data. So that’s why doing straight feature detection in the browser is a much more convenient way to resolve cross-browser issues. It’s more efficient to make someone do a task, proving what he’s capable of, than asking him theoretically, right? This is probably the most core functionality of Modernizr, but there is actually a lot more in it, like enabling HTML5 tags support in legacy browsers such as IE6 - IE8. OK the credit for HTML5 tags support goes to html5shim/html5shiv, but that’s included in Modernizr (by default) so you don’t have to load those separately.

## What Is Modernizr's Workflow?At the start of every page load in the client’s browser, Modernizr tests all of the features you’ve asked it to and places corresponding classes on the <html> tag of your document. For features that aren’t supported by the current browser it adds a “no-” prefix to the corresponding class name for that feature. For example if the user is browsing with IE8, where box-shadow isn’t supported, Modernizr adds a “no-boxshadow” class to the document's <html> tag.

## How Can I Take Advantage of Modernizr?Modernizr JavaScript library is a tool intended to help developers handle progressively enhancing web pages. It really depends on how you want to approach the visual and functional differences in browsers. Let’s go with CSS first.

## CSS3

```
/\* CSS3 Gradient in modern browsers \*/
.gradient-box {
    background: linear-gradient(to bottom,
        rgba(226,226,226,1) 0%,
        rgba(219,219,219,1) 50%,
        rgba(209,209,209,1) 51%,
        rgba(254,254,254,1) 100%);
}
/\* fallback image for old browsers - IE7, IE8 \*/
.no-cssgradients .gradient-box {
    background: url(img/vertical-gradient.png) 0 0 repeat-x;
}
```

So if you want to have gradients in IE8 just as in modern browsers, you have to use images. This is what the example above is doing, by using only the class placed by Modenizr on the <html> tag (in this case **.no-cssgradients**) to override the original style. Pretty simple, isn’t it?

## HTML5Now let’s move onto doing actually something with the library instead of leaving it to do all the work for us. In the next example I’ll use the _“placeholder”_ form input in HTML5.

```
Modernizr.load({
  test: Modernizr.input.placeholder,
  yep : '', // I've left the "yep" node just in case you have to include something even when it's supported, otherwise just skip writing "yep" in there
  nope: 'placeholder-polyfill.js'
});
```

This is a very basic example of the _Modernizr.load()_ method. What it does is as simple as it looks. It checks if the browser supports this feature and if it doesn’t it loads a polyfill for it. Polyfill is a code written in JavaScript to enable (mirror) some HTML5 functionality in older browsers that doesn’t have native support for it. You can write one yourself, but you can also find plenty on the internet. Loading scripts via the _.load()_ method of the library is really fast, because it loads files asynchronously. Just keep in mind that you shouldn't include the whole library if you're going to test just for one or two features in the browsers. There are single solutions for most of what you're going to need on this matter, so just make a quick search.

## How to Install Modernizr?First of all, let’s download it. Go to the official download page at [null](http://modernizr.com/download/) As suggested in there, you should use the development version before you start developing since it won’t be easy for you to predict all of the features you’re going to use in the project. The best place to include the script is inside the **<head>** of the document, right after your stylesheet files. Be sure to include the script there if you’re going to use HTML5 Shiv which needs to be executed before the **<body>** of the document is loaded. After you do this be sure to place a **“class=”no-js”** on the _<html>_ tag of your document. This class will be replaced by Modernizr with **“class=”js”** if JavaScript is enabled in your browser. This is it, you can now start using the library. After you have the big picture of your site, you can write down all of the features you’ll be enhancing progressively and go to the download page again. In the wizard there, check only those features you’ll need so you can optimize your own version of the library before uploading it to the production environment.

## ConclusionModernizr JavaScript library a tool that you don’t usually have a good reason not to use. It really is. It’s a very useful, small and fast library and if you’re going to use HTML5 and CSS3 (which you should use) using it in your project can only be helpful to you. There are really good reasons for why the biggest companies in IT like _Twitter, Google and Microsoft_ are using it for their websites right? **AR**




