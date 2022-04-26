---
title: 'Manage User Permissions by Replacing HTTP Handlers in GroupDocs.Viewer for .NET Library'
date: Wed, 26 Mar 2014 13:05:12 +0000
draft: false
url: /2014/03/26/manage-user-permissions-replacing-http-handlers-groupdocs-viewer-net-library/
author: 'Denis Gvardionov'
summary: ''
tags: ['GroupDocs Viewer', 'http handlers', 'user permissions', 'viewer for .net library', 'zArchive']
---

![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/03/GD_VWR_NETIcon_114.png)Greetings everyone! As you may know, GroupDocs.Viewer allows you to open and browse different types of documents (PDF, Word, Excel, etc.) in a browser, without any third-party plugins or programs. The viewer simply converts documents to a set of images, HTML, CSS and SVG and combines them to render the documents in HTML pages. GroupDocs.Viewer has several implementations designed for different platforms and forms of distribution. One of them is a [.NET library](http://groupdocs.com/dot-net/document-viewer-library). It is in fact a single DLL file which is easy to use in ASP.NET projects, both WebForms and MVC. There are a lot of [examples and articles](https://docs.groupdocs.com/viewer/net) showing how to use the standard GroupDocs.Viewer's for .NET functionality already, but this time I want to show you something different. Sometimes you may want to change, extend or supplement Viewer's functionality. For example, you may want to restrict the download, copy or print options. You can disable these by simply configuring Viewer's options, sure. But what if you want a more advanced and intelligent solution? For example, you may need to allow only registered users to be able to download a document, and restrict this option for unregistered users. This article shows you how to achieve this. [Go to the article >>>](https://docs.groupdocs.com/viewer/net)




