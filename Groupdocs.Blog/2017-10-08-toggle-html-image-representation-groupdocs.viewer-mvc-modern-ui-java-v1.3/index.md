---
title: 'Toggle between Html and Image Representation in GroupDocs.Viewer MVC Modern UI for Java v1.3'
date: Sun, 08 Oct 2017 18:54:08 +0000
draft: false
url: /2017/10/08/toggle-html-image-representation-groupdocs.viewer-mvc-modern-ui-java-v1.3/
author: 'Zeeshan Shafqat'
summary: ''
tags: []
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for Java](http://joomla-groupdocs.dynabic.com/templates/groupdocs/images/product-logos/90x90/groupdocs-viewer-java.png?v2g)](https://www.groupdocs.com/products/viewer/java)

GroupDocs team keeps on adding new features in **ASP.NET MVC Front End** for [**GroupDocs.Viewer for Java**](https://downloads.groupdocs.com/viewer/java/new-releases/groupdocs.viewer-for-java-17.2.0/), so that users can enjoy user-friendly interface, easily manageable code, pixel perfect rendering with features supported in our old front ends. In this new release **v1.3** user can now load document in both **HTML** and **Image **in the document. User can toggle between image and html through the Toggle image button. We recommend you to [download](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java/releases) and explore this new version. Let's have a look at it.

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/10/GDViewerJava-1024x649.png) Let's explore new features in detail.

## Toggle to Image RepresentationUser can now toggle between HTML and Image providing user a variety of features of ViewerImageHandler. Let's take a look at the code, `ViewerImageHandler handler = Utils.createViewerImageHandler(); ImageOptions o = new ImageOptions(); int pageNumber = Integer.valueOf(request.getParameter("page")); o.setPageNumbersToRender(Arrays.asList(pageNumber)); o.setPageNumber(pageNumber); o.setCountPagesToRender(1);`

## Open SourceThe best part is that full source code of the app is available to [download from GitHub](https://github.com/groupdocs-viewer/). You can also contribute to the app by sending a pull-request.

## API FeaturesThe app covers most APIs of GroupDocs.Viewer for Java, which allows anyone to see how to use same API in their own apps.

## Easy IntegrationThe app can be easily embedded or integrated with another app of your choice. You can either use IFRAME or embed it as AngularJS Module.

## Additional ResourcesFollowing resources will help you to download, learn, try and get technical support.

*   [Product Home](http://www.groupdocs.com/products/viewer/java) – GroupDocs.Viewer for Java.
*   [Documentation](http://www.groupdocs.com/docs/display/viewerjava/Home) – Product Documentations.
*   [Product Support Forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx) – Technical Support Forum for GroupDocs.Viewer.
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java) – Github source code examples.

## FeedbackAs always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx) and our dedicated support team will be there to respond.

* * *




