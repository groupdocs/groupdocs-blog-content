---
title: 'Using Web Icon Fonts - Best Practices'
date: Fri, 02 Aug 2013 15:51:23 +0000
draft: false
url: /2013/08/02/using-web-icon-fonts-best-practices/
author: 'Derek Hyland'
summary: ''
tags: ['CSS3 property', 'icon fonts', 'using icon fonts', 'web icon fonts', 'zArchive']
---

Here at [GroupDocs](http://groupdocs.com/) we take front end and web development in general very seriously. We constantly strive to improve our products and because of that, we try to keep up with the latest trends and best practices, not always an easy thing. But that doesn’t apply only to our front end department of course. Each and every one of us is trying to improve his skills and is eager to try different techniques that could result in better and more optimal outcomes. One of [GroupDocs](http://groupdocs.com/) designers recently told me he had been experimenting with web icon fonts and he asked me to help him with web implementation and testing to see if his efforts would bear fruit. I thought it was a good opportunity to share things with others on that matter since we had pretty good results.

## Ways to implement web icon fonts in your markupBefore I talk about browser support I feel I should explain how the web implementation goes here. Since we're using an actual font file, we implement it in the same way as any other custom web font. The created font is exported into a few different font formats and then we import those files using CSS. This is necessary because browser vendors support different formats, so we need our custom font in the following formats: EOT, TTF, WOFF, SVG. There are plenty of online tools that can do this for us so simply search on the web for that kind of tool. Something like [fontsquirrel.com/](http://www.fontsquirrel.com/), for example.

### How to implement it in our markupI've researched how other developers are doing this and two ways stood out from the rest. Selecting the icon we want to use on an element either by using its own CSS class, or by inserting its corresponding font character into the data attribute.

```
<span aria-hidden="true"></span>

.test-icon:before {
   content: "\\61";
}
```

```
<div class="icon-large-blue" aria-hidden="true" data-icon="a"></div>

\\\[data-icon\\\]:before {
   content: attr(data-icon);
```

### Which approach is best?Well, each is better then the other depending on the situation. The only thing I can say for sure is that the first approach is slightly faster because it doesn't rely on a data attribute, but only on the **content** CSS3 property. Let's assume that we don't need additional styling on the icon we want to use. In this case I feel that the first example is the most efficient way to do it. First of all we use only one attribute, second we use the class as a selector which is faster then using the **\[data\]** selector. Also, we use a direct value in the content property of the selector **content: "\\61";** which is again faster then the **content: attr(data-icon);** approach. Now let’s say we want to use the same icon, but we want to change its color and size so it sits better with the current look of our design. Well, from my standpoint, using dedicated classes for styling changes like these is the best approach, but that increases the number the class names used on the element. In cases like these I personally prefer to use the second example. Doing so we still avoid using actual characters inside the DOM element **<div class=”icon”> a</div>** and we achieve the desired result. There are plenty of other good ways to implement web icon fonts in your markup and CSS, so don't be afraid to experiment until you feel satisfied with the results. Also keep in mind that it really comes down to the project needs and what the design will look like.

## Browser supportThis method is supported in almost all browsers you should care about, the only problem is if you're supporting IE7 and below. But a few lines of JavaScript can fix this for us, so you don't need to be bothered by this. In [GroupDocs](http://groupdocs.com/), we plan to use this feature by creating at least two versions of the font: one for smaller icon sizes, like 20x20 pixels, and one for larger version of the icons, something around 50x50. Why? Because we have several places on the site where we use the same icons, but with different sizes, depending on the page design and content structure. For example, you'll see big icons for each of GroupDocs app on the home page: [http://groupdocs.com/](http://groupdocs.com/) And then you'll see the same icons, but in smaller size, on other page of the site. They're located in the right vertical navigation on the right side of the banner here: [http://groupdocs.com/developer/dot-net](http://groupdocs.com/dot-net)

## Examples of using web icon fontsRendering results with Google Chrome. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/08/image-1.png) Rendering results with Internet Explorer 8 ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/08/image-2.png) From what I've seen in my tests on different browsers, vector graphics with average sizes don't render well when they're shrunk down. Modern browsers such as Chrome, Safari and Firefox handles this well, but that's due to the more advanced antialiasing algorithms they use for text rendering. You can really see a notable difference in older browsers such as IE7 and IE8. Things are getting messy in there. So we either go with multiple fonts for dealing with this issue or we just make a font with small icons and keep increasing the size of the font until necessary, or until things start to look odd. Again it really comes down to the needs of the project so you should set your priorities first and try to find the most optimal solution which fits your needs the best. What will we gain by switching to this method of creating icons on the GroupDocs site?

*   First, we won't stop using sprites completely, but we'll discard some of our sprites and combine the icons used there in one, maybe two, font files.
*   Also, we'll optimize the space in our main sprite and decrease its initial file size.
*   This will give us the freedom to change icons color, size or adding other CSS styling (like text shadow) to them on the fly. That's due the potential that vector graphics offer.
*   We reduce development time since we don't have to update sprites constantly and we won't lose time on graphic optimizations anymore.

But keep in mind that like everything else in our life there are good and bad parts. This is a font, so all the graphics in it are monochromatic and your icons will be too. There is info on the web that this could result in worse user experience, even more for screen readers. You can try avoiding such complications by using the **:before** pseudo class, setting the speak property to none, or setting the **aria-hidden="true"** element. The best way is to use all of these tricks. Place the **aria-hidden** attribute on the HTML element, put the value of the content property in a selector with a **:before** pseudo class like in my earlier examples, and then set **speak: none;** in the main selector CSS styles. Something like this:```
<span aria-hidden="true"></span>

.test-icon {
   speak: none;
}
.test-icon:before {
   content: "\\61";
}
```Again there is no guarantee that this won't hurt the experience when using screen reader, but it's something. And of course, like any other font, you cannot expect it to look exactly the same across all browsers like an image would, but this effect can be reduced to a minimum with some extra CSS for font rendering.

## How to make custom fontsIt is best to consult with a professional graphical designer on that matter. I personally played a bit with [icomoon.io](https://icomoon.io/) and I'm pleased with the results it gave me. It gives you auto generation of all necessary font file formats, the icons CSS styles and also a good way for IE7 support. But there might be a lot more and different ways out there that may fit your needs better, so you should do your own research.

## ConclusionI personally like the idea of using web icon fonts in projects where possible and when the project's designer is hyped for the idea as much as me. It offers great flexibility and performance gains for the project and of course it's more fun to use new techniques. **AR**




