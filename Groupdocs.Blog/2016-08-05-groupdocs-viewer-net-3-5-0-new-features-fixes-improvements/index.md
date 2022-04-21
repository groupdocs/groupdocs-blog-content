---
title: 'Releasing GroupDocs.Viewer for .NET 3.5.0 - New Features and Fixes'
date: Fri, 05 Aug 2016 10:39:21 +0000
draft: false
url: /2016/08/05/groupdocs-viewer-net-3-5-0-new-features-fixes-improvements/
author: 'Usman Aziz'
summary: ''
tags: ['X GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/03/groupdocs-viewer.png)](http://groupdocs.com/dot-net/document-viewer-library)

We've always been listening to the feedback of our valuable customers and in response, we are announcing another monthly release of [GroupDocs.Viewer for .NET](http://www.groupdocs.com/dot-net/document-viewer-library "GroupDocs.Viewer for .NET") with fixes for over **15** issues. The latest version has also introduced some new features along with necessary improvements. Let's have a glance at what **v3.5.0** has come with.

## Document Viewer API - New FeaturesListed below are the new features introduced in **GroupDocs.Viewer for .NET 3.5.0**.

*   [Implement saving Cells document sheet to multiple pages in image mode](https://docs.groupdocs.com/viewer/net)
*   [Implement ability to specify font for watermark](https://docs.groupdocs.com/viewer/net)

## GroupDocs.Viewer for .NET 3.5.0 - FixesWe have provided fixes for following issues in the **GroupDocs.Viewer for .NET 3.5.0**.

*   Cannot add page to pdf document
*   OutOfMemoryException raised when total file size reached up to 250MB
*   The operation is not supported error raised when loading epub document
*   IOException is raised when try to move a loaded document(into the viewer) to any other directory
*   Cell shading is not applied uniformly while converting spreadsheet to HTML
*   Ott file stream detects as ods file format
*   GetDocumentInfo() throws "Parameter is not valid" exception
*   Excel file is not properly rendering into HTML
*   Header contents of Word document are not appearing in rendered html or images
*   Exception generated while calling handler.getDocumentInfo(uuid)
*   Exception when calling GetPdfFile/RotatePage/ReorderPage with guid without extension
*   Incorrect watermark position and text in PDF file
*   Out Of Memory exception while rendering excel file into HTML
*   Each page of a Word document is converted to HTML too long
*   Incorrect saving PDF to HTML
*   There is no text in tables of a PDF after conversion to HTML
*   Text selection is unstable in Firefox on the HTML engine

## Document Viewer API for .NET - ImprovementsFollowing are the improvements made in the latest version of the API.

*   Implement GetPdfFile from stream or remote file
*   Improve Words files to HTML rendering speed
*   Implement saving file data separately based on options
*   Implement releasing converters resources

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on **document viewer API**:

*   [Download](http://groupdocs.com/Community/getting-started/dot-net/document-viewer-library.aspx "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/groupdocs-viewer-dotnet/ "Install from NuGet Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/channel/UCgO8dwgI5KAsQCVegviVXYA/playlists "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocsviewer/GroupDocs_Viewer_NET "download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, you are welcome to share your feedback to improve this API. We will be happy to know your thoughts. Just create a [forum thread](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx "Technical Support Forum") and our dedicated support team will be there to respond.




