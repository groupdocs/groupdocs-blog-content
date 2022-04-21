---
title: 'Change Page Orientation using GroupDocs.Merger for Java 18.12'
date: Thu, 27 Dec 2018 14:06:43 +0000
draft: false
url: /2018/12/27/groupdocs.merger-for-java-18.12/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Merger for Java', 'GroupDocs.Merger Product Family']
---

[![GroupDocs Editor for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/08/groupdocs-merger.png)](https://www.groupdocs.com/products/merger/java)

We are pleased to announce **GroupDocs.Merger for Java 18.12** with many new features. This latest release provides the ability to change page orientation along with a feature to rotate pages in the document. Furthermore, you can also get a list of all the formats supported by the API. Please check GroupDocs.Merger for Java 18.12 [release notes](https://docs.groupdocs.com/display/mergerjava/GroupDocs.Merger+for+Java+18.12+Release+Notes) for further reference.

# Features

## Change Page OrientationNew method **changeOrientation** let you change page orientation (portrait, landscape) for pages in the document.```
DocumentResult result = new DocumentHandler().changeOrientation(documentExample, OrientationMode.Landscape, new int[]{1,6});
```

## Get Supported FormatsMethod **getSupportedFormats()** is added to get all formats supported by the API.```
Map documentFormatsContainer = new DocumentHandler().getSupportedFormats();
```

## Rotate Pages**rotatePages** method allows you to rotate pages in document.```
DocumentResult result = new DocumentHandler().rotatePages(documentExample, RotateMode.Rotate270);
```

## Supports Diagram and Note FormatsDiagram and Note formats are supported by following methods:

*   Join
*   MovePage
*   RemovePage
*   Split document
*   SwapPages
*   Trim

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Merger:

*   [API Home](https://products.groupdocs.com/merger/java "Product Home") - GroupDocs.Merger for Java
*   [Download](https://downloads.groupdocs.com/merger/java "Download API") - GroupDocs.Merger for Java Download
*   [Documentation](https://docs.groupdocs.com/display/mergerjava/Home "Documentation") - Product Documentation
*   [Examples](https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java "Example projects") - GitHub source code examples
*   [Product Support Forum](https://forum.groupdocs.com/c/merger "Support forum") \- Technical Support Forum for GroupDocs.Merger




