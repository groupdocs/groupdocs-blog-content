---
title: 'Remove Empty Paragraphs in GroupDocs.Assembly for .NET 18.10'
date: Tue, 20 Nov 2018 09:57:16 +0000
draft: false
url: /2018/11/20/remove-empty-paragraphs-in-groupdocs.assembly-for-.net-18.10/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for .NET', 'GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly Product Family']
---

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-assembly-net.png)We are delighted to announce a new feature in the monthly release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) **18.10**. Using the latest version, you can now remove empty paragraphs in word processing, presentation, and email documents. We recommend you to [install](https://www.nuget.org/packages/GroupDocs.Assembly/) and use the latest version of the API.

# Features Introduced

While assembling a document, if syntax tags are removed or replaced with empty values, the output document will have empty paragraphs. In version 18.10, we have introduced a new member **RemoveEmptyParagraphs **in **DocumentAssemblyOptions**. When this option is applied using **DocumentAssembler.Options**, the engine additionally removes empty paragraphs. You can use this option for the following document types:

*   Word Processing Document
*   Presentation Document
*   Email Document

## Use CaseTemplate document.```
Prefix
<<[""]>>
Suffix
```Result document without the new option applied.```
Prefix
  
Suffix
```Result document when the new option, **RemoveEmptyParagraphs** is applied.```
Prefix
Suffix
```For more details on this feature, please visit this documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Assembly for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Assembly/ "GroupDocs.Assembly Nuget Package") - Install GroupDocs.Assembly using NuGet
*   [Documentation](https://docs.groupdocs.com/display/assemblynet/Getting+Started "Assembly API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET/tree/master/Examples "How to use Assembly API") - Source Code Examples, Plugins, and Showcase Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vOzsaE9Rwjwd4-OwvdaWmJ8 "Assembly API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) - Technical Support Forum for GroupDocs.Assembly Product Family

# Feedback

As always, if you have some questions, queries or suggestions about [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) API,  just share with us by creating a [forum thread](https://forum.groupdocs.com/c/assembly).




