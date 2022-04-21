---
title: 'Change Page Orientation using GroupDocs.Merger for .NET 18.11'
date: Sun, 25 Nov 2018 12:39:01 +0000
draft: false
url: /2018/11/25/change-page-orientation-using-groupdocs.merger-for-.net-18.11/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Merger for .NET', 'GroupDocs.Merger Product Family']
---

[![GroupDocs Editor for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/05/groupdocs-merger.png)](https://www.groupdocs.com/products/merger/net)

We are pleased to announce the release of GroupDocs.Merger for .NET 18.11. This latest version of the API comes with some new features. **GetSupportedFormats** and **RotatePage** methods are introduced. Furthermore, you can change page orientation. Please see release notes for further details.

# Features

## Change Page OrientationNew method ChangeOrientation is introduced.```
public DocumentResult ChangeOrientation(Stream documentStream, OrientationOptions orientationOptions);
```

## Get Supported FormatsMethod GetSupportedFormats is added.```
public Dictionary GetSupportedFormats();
```

## Rotate PagesRotatePages method is introduced in the API.```
public DocumentResult RotatePages(Stream documentStream, RotateOptions rotateOptions);
```

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on GroupDocs.Merger:

*   [NuGet](https://www.nuget.org/packages/GroupDocs.Merger/ "GroupDocs.Merger Nuget Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/display/mergernet/Getting+Started "Merger API documentation") - API Documentation
*   [API Reference](https://apireference.groupdocs.com/net/merger "GroupDocs.Merger API reference") - GroupDocs.Merger for .NET API Reference
*   [Examples](https://github.com/groupdocs-merger/GroupDocs.Merger-for-.NET "How to use Merger API")\- Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/merger) - Technical Support Forum for GroupDocs.Merger queries

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/merger "Technical Support Forum").




