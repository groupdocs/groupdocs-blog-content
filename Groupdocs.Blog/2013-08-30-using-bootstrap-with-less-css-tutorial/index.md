---
title: 'Using Bootstrap With LESS CSS - Tutorial'
date: Fri, 30 Aug 2013 12:20:19 +0000
draft: false
url: /2013/08/30/using-bootstrap-with-less-css-tutorial/
author: 'Atanas Ruzhin'
summary: ''
tags: ['Bootstrap.LESS', 'less css', 'using bootstrap with less css', 'zArchive']
---

As I mentioned in my article on [how to optimize Bootstrap](https://blog.groupdocs.com/using-bootstrap-css-framework-in-your-project) this post will explain the basic syntax and features that the LESS language has to offer which you’ll need to extend, edit or minify Bootstrap. Hopefully this tutorial will help you understand the basics of using Bootstrap with LESS.

## What Is LESS?LESS is a dynamic stylesheet language which gives you more options and freedom when writing CSS. It helps you keep styles better organized, cascade styles more naturally and correct, and it speeds up CSS development in general. Also it’s a simple language which can be learned in a matter of hours by anyone with some programming experience. Even if you don’t have programming skills, it won't take you long to learn at least its basic features. \[caption id="attachment\_3791" align="alignnone" width="600" caption="LESS Dynamic Stylesheet Language"\]![LESS Dynamic Stylesheet Language](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/08/GD_Blog_LESS2.png "LESS Dynamic Stylesheet Language")\[/caption\]

## LESS syntaxThe idea with LESS is to help you develop faster, not to put an additional burden on your shoulders. It can be a lifesaver in large projects such [GroupDocs](http://groupdocs.com/). Described as simply as possible, you write CSS pretty much the same way you’ve always done using the CSS syntax, but with a different mindset when you’re writing in LESS. Which means that you now have options which allow you to write less code. LESS' slogan is **“LESS is more”**. Let’s write a few CSS styles and see how we can improve them with less syntax:

```
.blog-article {
    height: 300px;
}
.blog-article .image {
    display: block;
    float: left;
    border: 3px dashed black;
}
.blog-article h2 {
    font-size: 24px;
    color: #ccc;
    text-shadow: 1px 1px #000;
}
```

In LESS, it looks like this:

```
.blog-article {
    height: 300px;

    .image {
        display: block;
        float: left;
        border: 3px dashed black;
    }
    h2 {
        font-size: 24px;
        color: #ccc;
        text-shadow: 1px 1px #000;
    }
}
```

What if we want to extend some of the parent classes by adding a new class? In CSS, this is done by concatenating the two classes without leaving space between them:**.class1.class2**. In LESS, we do it by writing the new class inside the block of the main class with the **&** operator in front of it:

```
.blog-article {
    height: 300px;

    &.longer {
        height: 500px;
    }
}
```

This compiles into:

```
.blog-article {
    height: 300px;
}
.blog-article.longer {
    height: 500px;
}
```

After you compile the LESS code, it looks exactly the same as the CSS example above. So what have we gained here? Well, we don’t have to write the parents over and over before each new selector, but only inside the .blog-article block brackets (**{ }**). It might not seem like a big improvement, but as you write more and more code for your website, this way of writing becomes beneficial because styles look a lot more organized and are easier to read. But let's now discover some really neat benefits that we get when using LESS CSS.

## VariablesAs in classical programming languages, variables are used as containers where you store information as number values or text, depending on your needs. You can find a whole file in Bootstrap filled only with variables so developers can easily change different styles for their projects such as text colors or font types:

```
@gray: #555;
@sansFontFamily: "PT Sans", Helvetica, Arial, sans-serif;
```

The whole idea behind variables is that you can use them later in any of your rulesets without having to remember the exact hexadecimal code of a color, or a specific font family:

```
.blog-article {
    h2 {
        font-family: @sansFontFamily;
        font-size: @fontLarge;
        color: @gray;
    }
}
```

Of course you can also do arithmetical expressions with variables which store number values:

```
h4 {
    font-size: @fontLarge / 2;
}
```

## MixinsMixins are great for reusing code, something which is a big issue in CSS development. For example, imagine that you have multiple elements with blue background and some image pattern. You can make a simple ruleset that has these background styles inside it and reuse it where you need it later on:

```
// This is a simple CSS ruleset which can be added as a mixin inside other rulesets to inherit its properties
.blue-background {
    background: @blue url(path/img.png) 0 0 repeat-x;
}
.blog-article {
    .blue-background;
}
.widget-box {
    color: @white;
    border: 2px solid @lime;
    .blue-background;
}

// The code above compiles into:
.blog-article {
    background: #049cdb url(path/img.png) 0 0 repeat-x;
}
.widget-box {
    color: #fff;
    border: 2px solid #83ff46;
    background: #049cdb url(path/img.png) 0 0 repeat-x;
}
```

The parametric mixins spring from the same idea as the simple ones, but can accept parameters much like functions do in other programming languages. You can see a lot of them inside the **mixins.less** file in Bootstrap. Here is one that's very frequently used:

```
.border-radius (@radius) {
  border-radius: @radius;
  -moz-border-radius: @radius;
  -webkit-border-radius: @radius;
}
```

When we use this mixin inside a ruleset we just have to pass it the desirable value for the border radius we need on this element:

```
.button {
    .border-radius(5px);
}
// This outputs to the following CSS
.button {
    border-radius: 5px;
    -moz-border-radius: 5px;
    -webkit-border-radius: 5px;
}
```

No more worries over browser support! If you're writing a lot of repeatable code, just think of a way to create a mixin from it and start calling it in other parts of LESS when you need it. There is much, much more that LESS CSS can offer to boost your development process and productivity, but those features should be enough for you to extend and modify your Bootstrap as much as you want. If you're interested in learning more about using Bootstrap with LESS CSS or using LESS CSS even without Bootstrap, you can find anything necessary on [LESS' official website](http://lesscss.org/). **AR**




