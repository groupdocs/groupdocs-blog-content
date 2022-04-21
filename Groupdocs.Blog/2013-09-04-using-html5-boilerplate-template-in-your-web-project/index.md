---
title: 'Using HTML5 Boilerplate Template in Your Web Project'
date: Wed, 04 Sep 2013 09:55:12 +0000
draft: false
url: /2013/09/04/using-html5-boilerplate-template-in-your-web-project/
author: 'Atanas Ruzhin'
summary: ''
tags: ['html5 boilerplate templates', 'using html5 boilerplate', 'web templates', 'zArchive']
---

## IntroductionA few years ago, HTML 5 still wasn’t very well supported by most popular browsers so web sites were created mostly with XHTML or HTML4. I still have a folder on my machine filled with HTML templates for both XTML and HTML 4. Inside of it there are also templates for newsletters, micro-sites, responsive templates and whatnot. All of them were built by taking code from 2 or 3 different templates and look like Frankenstein's code monster. Which is understandable, because there are several doctypes in HTML4 and XHTML which developers had to take into account. Setting up a template for a new project wasn’t the fastest thing to do. But now, with HTML5, things are different. \[caption id="attachment\_3806" align="alignnone" width="600" caption="HTML5 Boilerplate Template"\]![HTML5 Boilerplate Template](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/GD_Blog_Boilerplate_banner_01.png "HTML5 Boilerplate Template")\[/caption\] **HTML5 Boilerplate** is a basic template for starting a new web project. It is used by some of the largest and most popular websites and companies for their websites and services, like Google, Microsoft and Nike. Boilerplate template is used in every [GroupDocs](http://groupdocs.com/html5-document-viewer) related project as well, even for this blog.

## Where to Get It?You can download the full version of Boilerplate template from the official website: [http://html5boilerplate.com/](http://html5boilerplate.com/). You can also can build your own optimized version of the template, choosing only the files you really need for your project here [http://www.initializr.com/](http://www.initializr.com/) For this tutorial I’ll use Initializr's custom builder. I’ll go with the **“Classic H5BP"** settings for this one.

## What’s Inside It?

### HTMLBoilerplate template has really simple structure built from few folders for your project’s CSS, images and scripts. It alos includes the most popular CSS and JS frameworks, like jQuery, modernizr and Normalize. The full version has a lot of other useful things, but I’ll stick to the core files of the template and leave the rest to your own investigations. Let’s look what’s in the **index.html** file. Right after the HTML5 doctype, you'll see a few **<!--\[if lt IE …\]>** statements. This is very useful feature and I've used it in almost every project I've worked on in the last 3 years or so. Those statements basically put specific classes on the _<html>_ element depending on which IE version the client is using: _.ie7, .ie8_ etc. Those classes are very helpful when you need to override a CSS rule to fix a bug in IE7 for example. The content in the _<head>_ of the document should be pretty self-explanatory. There a few _<meta>_ tags for the document’s charset type, viewport and description. Heads up: Don’t forget to edit the documents _<title></title>_. Of course we have the CSS files included and after them we have another IE specific statement which runs _HTML5shiv_ for legacy browsers which don’t have support for the new tags in HTML5 _(header, footer, nav,_ etc._)_. Keep in mind that you might want to get rid of

```
meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1
```

before pushing the project to live, because it’s an option created by Microsoft mainly for development and testing purposes.

### JavaScriptAt the start of the _<body>_ you can see one more statement for enabling Chrome Frame in legacy browsers. I usually keep this since it might improve the user experience for someone out there. At the end of the _<body>_, several scripts are loaded, make sure they stay there! The first two scripts load jQuery. The first one tries to load the library from Google’s servers and if it fails to do so the next script loads a local copy of jQuery to prevent potential problems with the site’s functionality. After those 2,  **plugins.js** and **main.js** swhould be included. **Main.js** is an empty file ready for your own JavaScript, and **plugins.js** is a file used to initialize plugins. And at the end of the file, you'll find a Google Analytics script template where you can insert your GA ID to enable tracking. That’s all of the index.html file. Create your wrapper element inside the body of the document and start writing markup.

### CSSLet’s talk about the CSS templates located in the css folder. There should be 3 files in total in this folder: **main.css, normalize.css, normalize.min.css** **Main.css** contains a few very basic styles for text, images and other popular HTML elements. There are a few helpful service classes you can use too, like **.clearfix** and**.invisible**. Also some media query statements for print media and responsive layouts. You can of course do whatever you want with the file: extend, delete or rename it. As for **Normalize.css**, this is your CSS reset file. You should always have one of these in your project. Normalize is probably the most popular CSS reset out there and it's built to bring a more consistent look to sites across modern browsers. If you decide to use your own reset file that’s OK, but you’re strongly encouraged to keep the first 5 or 6 CSS selectors which helps desktop legacy and mobile browsers with the rendering of HTML5 elements. If you have other files in the template you don’t know what do to with, feel free to remove them.

## ConclusionBoilerplate is the perfect solution if you don’t have your own HTML template. You can extent it and edit it as much as you want to fit your project's needs. You can use Initializr anytime you want to set up a different template output, or you can simply create a few versions of the template which are working for you and use them later on. It’s all up to you to decide. **AR**




