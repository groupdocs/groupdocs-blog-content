---
title: 'Support for Dynamic Insertion of External Documents in GroupDocs.Assembly for .NET 18.12'
date: Mon, 24 Dec 2018 22:20:48 +0000
draft: false
url: /2018/12/24/support-for-dynamic-insertion-of-external-documents-in-groupdocs.assembly-for-.net-18.12/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for .NET', 'GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly Product Family']
---

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-assembly-net.png)We are delighted to announce a new feature in the monthly release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) **18.12**. Using the latest version, you can now assemble external documents dynamically for Word Processing and Email file formats. Previously, an evaluation mark was added to a nested document being inserted dynamically, which is now fixed. We recommend you to [install](https://www.nuget.org/packages/GroupDocs.Assembly/) and use the latest version of the API.

# Features Introduced

You can insert contents of outer documents to your reports dynamically using doc tags. A doc tag denotes a placeholder within a template for a document to be inserted during runtime. The syntax of a doc tag is defined as follows:```
<<doc ["document_expression"]>> 
```An expression declared within a doc tag is used by the engine to load a document to be inserted during runtime. The expression must return a value of one of the following types:

*   A byte array containing document data
*   A [Stream](http://msdn.microsoft.com/en-us/library/system.io.stream(v=vs.110).aspx) instance able to read document data
*   A string containing a document URI

While building a report, an expression declared within a doc tag is evaluated and its result is used to load a document which content replaces the doc tag then. By default, a document being inserted is not checked against template syntax and is not populated with data as well. However, you can enable this by using a build switch as follows:```
<<doc ["document_expression"] -build>> 
```When a build switch is used, the engine treats a document being inserted as a template that can access the following data available at the scope of a corresponding doc tag:

*   Data sources
*   Variables
*   A contextual object
*   Known external types

For more details on this feature, please visit [this](https://docs.groupdocs.com/display/assemblynet/Working+with+Outer+Document+Insertion) documentation article.

# Fixes

The following bug is fixed in the latest version of the API.

*   An evaluation mark is added to a nested document being inserted dynamically

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Assembly for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Assembly/ "GroupDocs.Assembly Nuget Package") - Install GroupDocs.Assembly using NuGet
*   [Documentation](https://docs.groupdocs.com/display/assemblynet/Getting+Started "Assembly API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET/tree/master/Examples "How to use Assembly API") - Source Code Examples, Plugins, and Showcase Applications
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vOzsaE9Rwjwd4-OwvdaWmJ8 "Assembly API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) - Technical Support Forum for GroupDocs.Assembly Product Family

# Feedback

As always, if you have some questions, queries or suggestions about [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) API,  just share with us by creating a [forum thread](https://forum.groupdocs.com/c/assembly).




