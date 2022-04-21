---
title: 'Bootstrap v3: What Has Changed in the New Version'
date: Wed, 09 Oct 2013 12:29:25 +0000
draft: false
url: /2013/10/09/bootstrap-v3-what-has-changed-in-the-new-version/
author: 'Atanas Ruzhin'
summary: ''
tags: ['bootstrap 3', 'bootstrap css framework', 'bootstrap v3', 'Bootstrap.css', 'zArchive']
---

## IntroductionIn one of my previous articles I talked about [using the Bootstrap CSS framework in web projects](https://blog.groupdocs.com/using-bootstrap-css-framework-in-your-project). Exactly 2 years after the very first release of Bootstrap to the open world by the ex-Twitter developers we have now Bootstrap v3 - the new version of the most popular CSS framework. I’m calling it the most popular because of the recently announced results from the [meanpath](https://web.archive.org/web/20210516182340/http://meanpath.com/) source-code search engine which shows that 1% of websites nowadays are using Bootstrap. Which is a quite big number considering the fact there are more than 150 million active websites across the world wide web. But enough with rhetorical facts and let’s move on to the important part of this article. \[caption id="attachment\_4039" align="alignnone" width="622" caption="What Has Changed in Bootstrap v3"\]![What Has Changed in Bootstrap v3](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/GD_Blog_Bootstrap_02_2.png "Bootstrap v3: What Has Changed in the New Version")\[/caption\]

## What Has Changed in Bootstrap v3?On a first sight it doesn’t seem to have changed much, because Bootstrap v3 is still a CSS framework at the end of the day. Of course a lot of people are used to its features by now. But if you’re familiar with the code of the previous versions (mainly the [LESS ](https://blog.groupdocs.com/using-bootstrap-with-less-css-tutorial)part of it) it has actually changed a lot. Both the CSS and JavaScript parts were rewritten to provide better optimization for the end product, because the Bootstrap developers and community are pushing it to be more relevant to current front-end trends and best practices.

#### No more fallback Support for IE7The first major thing is that the framework doesn’t provide fallback styles for IE7 anymore. And that is to be expected, because even jQuery dropped them with their last major version. Dropping support for older browsers is an important transition for web evolution, because not that far into the feature, progressive enhancement will be aimed mainly at improving the mobile experience, rather than making websites behave the same way under different browser vendors. And that’s what I’m looking forward too as a web developer.

#### Fluid by defaultThe other big change is that Bootstrap v3 is responsive and fluid by default. This is because responsiveness isn’t a new concept in web development anymore and it’s such a common and widely used technique that it just doesn’t make sense to having a site that's optimized for mobile users. Because of all that, the **.row-fluid** and **.container-fluid**classes are now gone. They’re replaced with a lot of new classes for this, which give users a lot more freedom over and options for how they want their app’s layout to look on different screens. I won’t go into too much detail, or share code snippets, because you can find plenty of examples and instructions in the [official documentation](http://getbootstrap.com/css/#grid). The next major change in Bootstrap v3 is that it is built around the idea of the **“Mobile First”** approach. If you aren’t familiar with this practice, it’s basically a way of developing a web app. You start developing it for the smallest phones, then tablets and so on until you reach the large desktop look and features. So this change comes hand in hand with the default fluid nature of the framework. If you're disappointed about these changes and think that you’re obligated to make your site responsive and can’t use Bootstrap v3 because of this, don’t worry: you can still make static sites, just with some extra classes in the HTML. You have now a standalone class for responsive images - **.img-responsive** - instead of having all of your images that way when using the responsive version of the framework.

#### Glyphicons use font filesThe next important change I really want to point out goes hand in hand with one of my previous articles, [Using Web Icon Fonts – Best Practices](https://blog.groupdocs.com/using-web-icon-fonts-best-practices). That’s right, Glyphicons now use a font file instead of a PNG sprite, which I find awesome. It has 180 icons inside it, so be sure to check them out if you plan on using them in your project.

#### New lookAlso another big change is the default look of the whole framework. Like the other changes, this shows that Bootstrap aims to stay relevant to the current state of web. The design has “gone flat” as they call it, meaning that a lot of box shadows and gradients have been removed from most of the elements.  The bright colors have been changed to more neutral ones. Soft, darker colors and more simplicity is what web 2.0 stands for, so this change was kind of expected, at least from me.

#### Modules added, modules removedThe last changes I want to mention are what modules are removed and what’s added. Accordion, submenus and typeahead were removed. They are replaced by new modules: Panels and List Groups.

*   Panels are basically boxes that have an optional header, footer and, of course, content part. This could come in handy for any custom notification boxes (something like alerts in that sense) or containers for articles and so on.
*   List groups can be used for a simple or really complex series of components that have some sort consistent hierarchy. Of course they don’t limit you in any way and you can use them for whatever type of structure you think fits them well. It’s a flexible and powerful component which could fit very well in responsive and more complex layouts.

There are thousands of other changes on the class names of pretty much the whole framework which you can find on the official Bootstrap website. For those of you who aren’t ready to transition yet, don’t worry: version 2.3.2 is still [null](http://getbootstrap.com/2.3.2/getting-started.html).

## To Sum It UpPersonally, I’m very pleased with the new version of the framework and I have already started using Bootstrap v3 in several new projects. I could say it’s not bad, but I’ll probably need a bit more time to adapt to it as with anything new. I like that they’ve gone for the icon font and the mobile first approach and that they keep looking to the future. **AR**




