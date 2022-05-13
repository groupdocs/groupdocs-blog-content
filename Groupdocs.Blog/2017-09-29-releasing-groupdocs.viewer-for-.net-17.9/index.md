---
title: 'Excluding Fonts from Output HTML using GroupDocs.Viewer for .NET 17.9'
date: Fri, 29 Sep 2017 18:15:26 +0000
draft: false
url: /2017/09/29/releasing-groupdocs.viewer-for-.net-17.9/
author: 'Usman Aziz'
summary: ''
tags: ['dotNET document rendering API', 'dotNET document viewer API', 'asp.net document viewer API', 'C# document viewer API', 'document viewer API for asp.net', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are excited to release another monthly release, version 17.9, of [GroupDocs.Viewer for .NET](https://www.groupdocs.com/products/viewer/net). This version allows you excluding fonts from HTML representation of the document and saving them as external resources. Also, we have extended the support of responsive HTML for **MS Visio documents**, **SVG images**, **MS Word documents**, **Open Office Text** and **Rich Text document format**. The latest version also includes some important bug fixes for the issues found in prior releases. We recommend you to upgrade to the latest version for an improved experience.

## Excluding Fonts when Rendering to HTML {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-RenderingdocumentswithComments}Embedded fonts increase the size of the rendering result, therefore, in order to prevent adding fonts into HTML, we introduced **ExcludeFonts** property of **HtmlOptions** class. For more details on excluding fonts from HTML representation, please visit [this documentation article](https://docs.groupdocs.com/viewer/net "GroupDocs.Viewer features").

## GIF Images with Animation in Output HTML {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-IgnoringemptyrowswhenrenderingCellsdocuments}In earlier versions, when rendering document into HTML, GIF images were converted into PNG format. Therefore, the images were displayed without animation in the resultant HTML. From version 17.9, we have added the support of saving the GIF images as it is when rendering the documents into HTML.

## .NET Document Viewer API - Improvements {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-IgnoringresourceprefixforHTMLresources}Following are the improvements that we made in version 17.9.

*   Showing local time when rendering email messages
*   Responsive HTML output for rendering MS Visio documents, SVG images and Text documents
*   Improved rendering into HTML for rotated documents

## Document Rendering API for .NET - FixesFollowing issues are fixed in GroupDocs.Viewer for .NET 17.9.

*   Slow rendering and gigabytes of RAM consumption for Word document of 1758 pages
*   Issue with recipient and sent date when rendering from .eml message to image
*   File extension field does not include period
*   Incorrect position of parenthesis in output HTML
*   Out Of Memory Exception when rendering PDF into image
*   Blank output HTML page when rendering PDF document
*   Misplaced characters when viewing HTML in Safari for iOS
*   Alignment of radio button text and checkbox text is not proper

## Breaking Changes in v17.9 {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-IgnoringemptyrowswhenrenderingCellsdocuments}Following are the breaking changes in GroupDocs.Viewer for .NET 17.9.

### **NuGet Package Name Changed**The NuGet package name is changed from **groupdocs-viewer-dotnet** to **GroupDocs.Viewer**.

### **File Extension Field does not Include Period**There is a breaking change in the version 17.9 related to the file extensions. This change is especially relevant to users who have implemented their own custom ICacheDataHandler. All file extensions from now on will come with the leading dot. Following public members are affected:

*   FileExtension property of ImageOptions class
*   Extension property of the AttachmentBase abstract class
*   SupportedDocumentFormats property of the DocumentFormatsContainer class
*   Extension property of the FileDescription class
*   Extension property of DocumentInfoContainer class
*   OutputExtension property of the CachedDocumentDescription and CachedPageDescription classes.

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/channel/UCgO8dwgI5KAsQCVegviVXYA/playlists "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").





