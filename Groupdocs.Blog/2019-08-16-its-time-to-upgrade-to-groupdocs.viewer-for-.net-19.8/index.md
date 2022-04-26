---
title: 'It''s Time to Upgrade to GroupDocs.Viewer for .NET v19.8'
date: Fri, 16 Aug 2019 18:07:14 +0000
draft: false
url: /2019/08/16/its-time-to-upgrade-to-groupdocs.viewer-for-.net-19.8/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', 'CAD viewer', 'document viewer', 'Document viewer API', 'document viewer API for asp.net', 'Office Viewer', 'online document viewer', 'PDF viewer', 'render as PDF', 'word to pdf']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) has been serving the developers in creating the document viewer applications for many years. With the efforts of our hard-working team and the support of our valuable customers, we are able to make the API stand among the top-ranked document viewer APIs. Since the Sky is the only limit, we always keep on enriching the API with more features, improving its performance, and making its usage easier for the developers. And today, I am excited to announce that we have introduced a new public API for GroupDocs.Viewer for .NET with major improvements.

In the latest version of the API (v19.8), we've improved the architecture of the API to simplify its usage and make it even easier to build applications. With the major product optimization, the API now consumes fewer resources as compared to the previous versions. Whereas, the document rendering speed has been improved significantly.

Let me give you a few reasons why you should switch to the v19.8 of GroupDocs.Viewer for .NET.

*   **Memory usage** - Significantly improved and optimized API's memory usage (from 10% to 400% approx. depending on the document type ).
*   **Improved rendering speed** - The overall rendering speed has been improvedremarkably. 
*   **Code optimization** - Optimized public API to make it even more intuitive and simple (with only a few lines of code you will be able to perform any action which required 20+ lines of code in the previous version).
*   **Single entry point** - A single class to manage the document rendering process for any supported file format.
*   **Easy to use** - API now gives more options to the developer in terms of usage and creativity.

With the major updates, the public API of GroupDocs.Viewer for .NET has undergone significant changes. As a result, the usage of the classes and their properties and functions has also been changed. Let's now check the difference between the coding styles of the new and old version of the API.

This is how we used to get the HTML representation of the document with embedded resources using the old version:

{{< gist GroupDocsGists f45159cf559053d41252a2069ec74425 "Viewer_OldStyle.cs" >}}

Now, have a look at how we can perform the same operation using the new API.

{{< gist GroupDocsGists f45159cf559053d41252a2069ec74425 "Viewer_NewStyle.cs" >}}

Have you noticed that the code has been shrunk significantly to fewer lines of code in the coding style of the new API? Also, you don't have to create separate handlers for HTML and image representation. Instead, just create a _[Viewer](https://apireference.groupdocs.com/net/viewer/groupdocs.viewer/viewer)_ class and control its behavior using the classes that extend _ViewOptions_ i.e. _[HtmlViewOptions](https://apireference.groupdocs.com/net/viewer/groupdocs.viewer.options/htmlviewoptions)_, _[PngViewOptions](https://apireference.groupdocs.com/net/viewer/groupdocs.viewer.options/pngviewoptions)_ and so on.

Now, as a developer, it is obvious that you would think about how would you deal with breaking changes in code after upgrading to the version which contains the major updates. So let me make it easier for you. In the latest version, the legacy API has been moved into the **Legacy** namespace. Therefore, after you upgrade to version 19.8, it is required to make project-wide replacement of namespaces only. This means that the namespaces will be changed from **GroupDocs.Viewer.\*** to **GroupDocs.Viewer.Legacy.\*** to resolve build issues. And that's it!

Alright! So now, its time to switch to the latest version. I would recommend you to first explore the [documentation](https://docs.groupdocs.com/viewer/net/) of the new API with the help of the source code [examples](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET/tree/master/Examples). Once you try it yourself, you will get a better idea of how useful it'll be for you to switch to the latest version. You can also consult the [release notes](https://docs.groupdocs.com/display/viewernet/GroupDocs.Viewer+for+.NET+19.8+Release+Notes) as well as the [migration notes](https://docs.groupdocs.com/viewer/net).

In case you would find the migration process difficult for you, feel free to post on our [forum](https://forum.groupdocs.com/categories).




