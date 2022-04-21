---
title: 'Insert Hyperlinks Dynamically in Documents using C#'
date: Sun, 19 Aug 2018 18:13:29 +0000
draft: false
url: /2018/08/19/insert-hyperlinks-dynamically-in-csharp-using-groupdocs-assembly/
aliases:
    - /2018/08/19/insert-hyperlinks-dynamically-using-groupdocs.assembly-for-.net-18.7/
author: 'Ali Ahmed'
summary: ''
tags: ['insert hyperlink in reports', 'insert hyperlinks in csharp']
categories: ['GroupDocs.Assembly Product Family']
---



{{< figure align=center src="images/groupdocs-assembly-net.png" alt="">}}


[GroupDocs](https://www.groupdocs.com/) team is releasing new features in the monthly release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) **18.7**. Using the latest version, you can now insert hyperlinks dynamically in Word Processing, Spreadsheet, Presentation, and Email documents. We recommend to [install](https://www.nuget.org/packages/GroupDocs.Assembly/) and use the latest version of the API.

## How to Insert Hyperlinks to Reports using Link Tag in C#

Using GroupDocs.Assembly for .NET 18.7, you can now insert hyperlinks to your reports dynamically using link tags. The syntax of a link tag is defined as follows:

```
 <<link \[uri\_expression\]\[display\_text\_expression\]>>
```

Here, **uri\_expression** defines URI for a hyperlink to be inserted dynamically. This expression is mandatory and must return a non-empty value. In turn, **display\_text\_expression** defines text to be displayed for the hyperlink. This expression is optional. If it is omitted or returns an empty value, then during runtime, the value of **uri\_expression** is used as display text as well.

For more details regarding this feature, please have a look at [Inserting Hyperlinks Dynamically](https://docs.groupdocs.com/assembly/net/inserting-hyperlinks-dynamically/).

## Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Assembly for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Assembly/ "GroupDocs.Assembly Nuget Package") - Install GroupDocs.Assembly using NuGet
*   [Documentation](https://docs.groupdocs.com/display/assemblynet/Getting+Started "Assembly API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET/tree/master/Examples "How to use Assembly API") - Source Code Examples, Plugins, and Assembly Editor Application
*   [Video Tutorials](https://www.youtube.com/watch?v=7FfYiii_PcM&t=0s&list=PL25CTxMCj5vOzsaE9Rwjwd4-OwvdaWmJ8&index=2 "Assembly API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) - Technical Support Forum for GroupDocs Assembly

## Feedback

As always, if you have some questions, queries or suggestions about [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) API,  just share with us by creating a [forum thread](https://forum.groupdocs.com/c/assembly).




