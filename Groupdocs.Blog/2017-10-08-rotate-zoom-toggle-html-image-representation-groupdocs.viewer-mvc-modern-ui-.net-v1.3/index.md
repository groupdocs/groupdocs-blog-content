---
title: 'Rotate Zoom and Toggle between Html and Image Representation in GroupDocs.Viewer MVC Modern UI for .NET v1.3'
date: Sun, 08 Oct 2017 18:55:39 +0000
draft: false
url: /2017/10/08/rotate-zoom-toggle-html-image-representation-groupdocs.viewer-mvc-modern-ui-.net-v1.3/
author: 'Zeeshan Shafqat'
summary: ''
tags: []
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](http://groupdocs.com/dot-net/document-viewer-library)

GroupDocs team keeps on adding new features in **ASP.NET MVC Front End** for [**GroupDocs.Viewer for .NET**](https://downloads.groupdocs.com/viewer/net/new-releases/groupdocs.viewer-for-.net-17.6.0/), so that users can enjoy user-friendly interface, easily manageable code, pixel perfect rendering with features supported in our old front ends. In this new release **v1.3** user can now load document in both **HTML** and **Image **in the document. User can toggle between image and html through the Toggle image button. Under Image Representation user can Rotate and Document and Zoom In/Out. We recommend you to [download](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET/releases/tag/Modern.UI.v1.2) and explore this new version. Let's have a look at it.

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/09/2017-09-12_15-08-59.png) Let's explore new features in detail.

## Toggle to Image RepresentationUser can now toggle between HTML and Image providing user a variety of features of ViewerImageHandler. Let's take a look at the code, `ViewerImageHandler handler = Utils.CreateViewerImageHandler(); ImageOptions o = new ImageOptions(); o.PageNumbersToRender = new List<int>() { page }; o.PageNumber = page; o.CountPagesToRender = 1; List<PageImage> list = Utils.LoadPageImageList(handler, file, o);`

## Zoom Image

*   Zoom in/Out buttons are visible only under Image Representation of file.
*   Zoom will increase/decrease the size of image to 10 pts.

## Rotate Image

*   User can rotate all the pages of the file when click this button.
*   Rotate Image will allow to rotate in one direction.

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/groupdocs-viewer-dotnet/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/channel/UCgO8dwgI5KAsQCVegviVXYA/playlists "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocsviewer/GroupDocs_Viewer_NET "download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx "Technical Support Forum").




