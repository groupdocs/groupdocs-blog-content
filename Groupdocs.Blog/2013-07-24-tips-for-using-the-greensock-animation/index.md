---
title: 'Tips for using the GreenSock Animation Platform'
date: Wed, 24 Jul 2013 13:03:32 +0000
draft: false
url: /2013/07/24/tips-for-using-the-greensock-animation/
author: 'Derek Hyland'
summary: ''
tags: ['framework', 'greensock', 'greensock animation platform', 'GroupDocs', 'GroupDocs Document Management', 'gsap', 'zArchive']
---

## GreenSock Animation Platform (GSAP) for JavaScriptI have always had a sort of passion for the special effects presented in today's multi-media. I've experience with a lot of different types of effects. From the credits at the end of a TV show, subtitles, and karaoke effects. The last type, that I still work with, are the CSS3 animations which are now one of the most used trend to achieve effects and interactivity on the modern web. About half an year ago I was assigned to a project with a lot of complex and long animations. And of course, the client wanted everything to be created with CSS3 animations. This is when I discovered the GreenSock Animation Platform. I was pleasantly surprised by the potential of this framework.

## GSAP JS IntroductionIn short, this framework is focused on giving an easy, effective and powerful way for creating rich animations, as well as dynamic and creative web interfaces. The framework was developed for Action Script 2 (AS2), but later on it was extended for AS3 and - last but not least - a little over a year ago, Front End developers received the pleasant news that GSAP now has a version for JavaScript as well. The magic wand that Flash developers were wielding with passion and confidence can now be used by Front End developers. It's a great assistant in modern web development where CSS3 animations have become an inseparable part from interactive web applications and even more necessary in marketing websites where a lot of "flashiness" and rich animations are required. That's enough introduction: lets move to the real part.

## Why this is the best framework in its field of expertise? What are the good points of it?

1.  The syntax is pretty straight forward and really easy to learn and use.
2.  It saves you a lot of development time.
3.  It offers cross-browser support for all major browsers, even IE8 (at least most of it).
4.  Incredibly fast performance and small file size for what you can achieve with it.
5.  Framework independent, it's written in clean and classic JavaScript.
6.  No jQuery or mootools are necesesary.
7.  It's free for non-commercial projects.
8.  There is plenty of documentation and tutorials on the official website - [https://greensock.com/docs](http://greensock.com/docs#/HTML5/).

I can point out other big pluses of the framework, but we'll stick to the major ones which should be enough to show how amazing this piece of software is. Let me break down the points above in a more detailed and augmented way. Before I start with some GroupDocs related code examples, it is very important to explain the main concept behind the framework idea. Described as simply as possible, what the framework does is **change an object's property from one value to another**.

### GroupDocs Code examplesLive example: https://codepen.io/dwigga/pen/EmKro For these examples we're going to use some of the images from the [official GroupDocs website](http://groupdocs.com):

```
TweenLite.to( 'logo', 1.5, {width: 286} );
```

This line of code animates the width of a image from 0 to 286 pixels. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/07/note1.png "note") A quick description of the code:

*   TweenLite - the tween object.
*   .to()\- the object method which receives the 3 required parameters:
    *   Param 1 - The object we're going to animate, in our case "logo". (String.)
    *   Param 2: The duration of the tween (in seconds). In our case, the tween will last for second and a half. (Number.)
    *   Param 3: The properties of the object (the element) we want to animate. We wrap up the properties in object brackets and separate them with commas (Object):
        
        ```
        {property1: value, property2: value}
        ```
        

#### Heads up for this code exampleNotice exactly how I wrote the object: **'logo'** Now in a normal JS context, writing the selector name this way would be invalid, because the object should be either assigned to a variable before that point, or simply using **document.getElementById('logo')** does the job. Or in case we want to use jQuery, we should wrap it in a jQuery selector block like: **$('#logo')**. Now the reason that I'm listing all of those variants is because all of them actually work in the same way, regardless of which one we decide to use. So all of the lines below **work exactly the same**.

```
TweenLite.to( 'logo', 1.5, {width: 236} );
TweenLite.to( '#logo', 1.5, {width: 236} );
TweenLite.to( document.getElementById('logo'), 1.5, {width: 236} );
TweenLite.to( $('#logo'), 1.5, {width: 236} );
```

Here is a breakdown of what actually happens when the GreenSock Animation Platform executes the very first line of code from the four above:

*   If the object's type isn't defined in the code, GSAP automatically checks if any of the popular JS frameworks are already loaded, such as **window.$** or **window.jQuery**. If neither is found it falls back to the default JS ID selector - document.getElementById(). This means you're free to use any engine selector you want or are already using. The only drawback of not declaring the exact object type is a very small performance cost. But that should be raising concerns only when you're animating a HUGE number of objects at the same time and of the same name.

*   The other thing I want to point out in this example is that we're animating the default width property of the IMG element in HTML, not its CSS property. The main reason I'm doing this is because I want to highlight that you can tween any property of any DOM element, custom or default object you have. Even Canvas! That's as awesome as it gets!

#### But lets take a look at more advanced tweens involving CSS changes by extending the last example.Live example: https://codepen.io/dwigga/pen/wcBhl

```
TweenLite.to( logo, 1.5, {width: 236} );
TweenMax.to( logo, 1, {x: 500, rotation: 360, delay: 1.5, ease: Expo.easeIn} );
TweenMax.to( logo, 1, {transformOrigin: '0 50%', rotation: 335, delay: 3, ease: Back.easeIn} );
TweenMax.to( logo, 1, {rotation: 440, delay: 4, ease: Back.easeInOut} );
TweenMax.to( logo, 1, {rotation: 450, delay: 5, ease: Power3.easeIn, yoyo: true, repeat: -1} );
```

The first thing you'll probably ask is: "Why is TweenMax used here?" The GreenSock Animation Platform has 2 versions. **TweenLite** is the slim one. It has the tools necessary for dealing with simple animations. If our main focus is performance and file size we should use this version. The other, more advanced version of the framework, is **TweenMax**, TweenLite's big beefy brother. It's the same thing, but it gives us many more options to play with and it loads the most used and popular plugins for GSAP automatically. If we want to tween CSS properties we need the **CSSPlugin** plugin to be loaded. Using TweenMax will do that for us. In this example I'm using five tweens in total. I'll describe what they're doing:

*   The first tween does the same as in the first example, increasing the image's width.
*   The second tween moves the image to the right and rotates it in a full 360 degree motion with some extra easing for better visual effect.
*   The third one its rotating the image's right end only thanks to the transformOrigin: '0 50%' property.
*   The Fourth one is doing the same thing as the previous but in the opposite direction and it leaves the image in a vertical position.
*   And the last one simply loops the animation, rotating the image by 10 pixels in both directions endlessly. I won't go in further details with this example, but you can see what those properties are about and much, much more on the [GreenSock Docs](https://greensock.com/docs/).

#### Why does this save development time?I want to explain why this framework reduces development time so much. We have to keep in mind that CSS3 is still not fully supported across all major browser vendors and most of them still use their own vendor prefixes for most CSS3 properties (for example **webkit**, **moz**, **o**, or **ms**). If we write CSS3 animations in the standard way, by writing CSS3 directly, we need to copy this code many times as necessary and use the browser vendor prefixes so that the code works on all major browsers. Just a quick example of what I'm talking about:

```
transform: translate(700px, 0);
```

Without using prefixes this works only in the latest versions of webkit based browsers and Firefox. But we can make this work on older versions as well, if we use the vendor prefixes. For example, for Webkit based browsers:

```
transform: translate(700px, 0);
-webkit-transform: translate(700px, 0);
```

Now if we want to enable support for older Firefox versions, we need to duplicate the code once more:

```
transform: translate(700px, 0);
-webkit-transform: translate(700px, 0);
-moz-transform: translate(700px, 0);
```

And we need to continue doing this until we have included the prefixes for all popular browsers on the market. That's why the GreenSock Animation Platform saves a lot of development time: you write the tween and GSAP does the rest. It checks what the current browser and version is, and adds all of the necessary prefixes.

#### So it's fast, huh?I've mentioned that its fast. But how fast is it? Well, super fast. In fact, **20 times** faster then jQuery and mootools. You can see the difference yourself here: [https://www.greensock.com/js/speed.html](http://www.greensock.com/js/speed.html) Again this is the official website of the framework: [GreenSock](https://greensock.com/) And the full official documentation for it: [https://greensock.com/docs](http://greensock.com/docs#/HTML5/)

#### ConclusionAs my final thoughts for GSAP I can honestly say that the guys involved in the creation of GreenSock have done a wonderful job. That's a life time achievement. The framework is fast, effective, small, OOP friendly and gives developers everything they can wish for when doing web animations. The best part is that the JavaScript version of it is updated very frequently and a lot of new cools things will be coming up in the future. **AR**




