---
title: 'Render STL and IFC File Formats using GroupDocs.Viewer for .NET 17.10'
date: Mon, 30 Oct 2017 13:13:26 +0000
draft: false
url: /2017/10/30/render-stl-and-ifc-file-formats-groupdocs.viewer-for-.net-17.10/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'asp.net document viewer API', 'asp.net pdf viewer', 'document viewer API for .net', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are pleased to announce the release of version 17.10 of [GroupDocs.Viewer for .NET](https://www.groupdocs.com/products/viewer/net). This monthly release has come with 3 new features and more than 10 improvements and bug fixes. **GroupDocs.Viewer for .NET 17.10** allows you to render **STL** and **IFC** file formats. Furthermore, settings to hide/show hidden pages have been extended for Microsoft PowerPoint documents. Please continue to read more about the latest version.

## Render STL and IFC File FormatsFrom version 17.10, GroupDocs.Viewer supports rendering of STL and IFC file formats. For more details on supported file formats, please visit [this documentation article](https://docs.groupdocs.com/display/viewernet/Supported+Document+Formats "GroupDocs.Viewer File Formats").

## Rendering Hidden Sheets, Slides or PagesMicrosoft Excel, PowerPoint and Visio documents may contain hidden pages (slides or sheets). By default, hidden pages are not rendered. In order to include them into the rendering, set **ShowHiddenPages** property of the **RenderOptions** (ImageOptions or HtmlOptions) class as true. This new setting has replaced obsolete **CellsOptions.ShowHiddenSheets** and **DiagramOptions.ShowHiddenPages** properties in **RenderOptions** class. For more details on rendering hidden pages, please visit [this documentation article](https://docs.groupdocs.com/viewer/net "GroupDocs.Viewer Hidden Pages").

## Rendering Worksheets by Dividing into PagesBy default, GroupDocs.Viewer for .NET renders the whole Excel sheet into a single HTML/image page or into a single page of the PDF document. However, the API also allows dividing large Excel sheets into multiple pages. From version 17.10, this feature is supported for rendering the document as PDF and as image with enabled text extraction. For more details, please visit [this documentation article](https://docs.groupdocs.com/viewer/net "GroupDocs.Viewer").

## Improved Document Rendering from Stream into HTMLIn earlier versions, when we render document from the stream and do not provide document name, API has been suppressing saving resources separately and embedding resources into HTML regardless of IsResourcesEmbedded setting. Since the version 17.10, when document name is not provided, API tries to generate document name from the stream. When that stream is rendered again, API will generate the same name. However, try to avoid not passing document name in cases when document name is known because API does not guarantee that document type will be detected and that document name will be unique for the stream (as in some cases, API may generate the same name for two different streams).

## .NET Document Viewer API - FixesFollowing are the issues that are fixed in version 17.10.

*   Gray rectangles instead of image parts
*   Empty space between text is lost when rendering email documents
*   The parameter 'address' cannot be an empty string exception when rendering MSG document
*   Some rows/records are missing when rendering Excel document to HTML
*   Parameter is not valid exception when rendering Excel document to image
*   The output image gets cut when rendering PowerPoint presentation
*   All pages are same when rendering Microsoft Project document into an image
*   Incorrect rendering of PDF document into HTML
*   Exception when rendering CAD file into image

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").





