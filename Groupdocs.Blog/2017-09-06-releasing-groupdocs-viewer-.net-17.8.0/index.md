---
title: 'New Features and Extended Support of File Formats in GroupDocs.Viewer for .NET 17.8.0'
date: Wed, 06 Sep 2017 14:00:07 +0000
draft: false
url: /2017/09/06/releasing-groupdocs-viewer-.net-17.8.0/
author: 'Usman Aziz'
summary: ''
tags: ['dotNET document rendering API', 'dotNET document viewer API', 'document viewer for .net', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

Another month, another version. Today we are releasing version 17.8.0 of [GroupDocs.Viewer for .NET](https://www.groupdocs.com/products/viewer/net). This version resolves a number of bugs that were found in prior releases. Furthermore, we have added the support of more file formats as well as introduced new features in this monthly release. Please continue to find out more about version 17.8.0.

## Rendering Documents with Comments {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-RenderingdocumentswithComments}From version 17.8.0, we have extended the support of rendering document comments. Now, rendering comments into HTML and PDF is supported for Microsoft Power Point. Furthermore, rendering comments into HTML is supported for MS Excel and OpenDocument spreadsheet. For more details on rendering documents with comments, please visit [this documentation article](https://docs.groupdocs.com/viewer/net "GroupDocs.Viewer features").

## Ignoring Empty Rows when Rendering Cells Documents {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-IgnoringemptyrowswhenrenderingCellsdocuments}Sometimes Cells document contains information in the beginning of the worksheet and after that, it contains some count of empty (blank) rows and information again e.g. summary row. Rendering complete worksheet may take considerable time and may result in decreased performance. Starting from 17.8.0, we introduced a new option, _CellsOptions.IgnoreEmptyRows,_ which allows omitting rendering of empty rows. For more details, please visit [this documentation article](https://docs.groupdocs.com/viewer/net "GroupDocs.Viewer features").

## Responsive Output for Rendering into HTML {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-ResponsiveoutputforrenderingintoHTML}In order to make your rendering into HTML look well across all type of devices, we added _EnableResponsiveRendering _option of HtmlOptions class. For more details, please visit [this documentation article](https://docs.groupdocs.com/viewer/net "GroupDocs.Viewer features").

## Ignoring Resource Prefix for HTML Resources {#GroupDocs.Viewerfor.NET17.8.0ReleaseNotes-IgnoringresourceprefixforHTMLresources}Since the version 17.8.0, _IgnoreResourcePrefixForCss_ setting is marked as obsolete and has been replaced by _IgnorePrefixInResources_ which applies to all resource types.

## Supported File FormatsWe have added the support of following file formats in version 17.8.0.

*   DNG - Image file format
*   VSDM - MS Visio file format
*   VSTM - MS Visio file format
*   VSSM - MS Visio file format

For more details, please visit [Supported File Formats](https://docs.groupdocs.com/display/viewernet/Supported+Document+Formats "GroupDocs.Viewer features").

## GroupDocs.Viewer for .NET 17.8.0 - ImprovementsFollowing improvements have been made in version 17.8.0.

*   Setting prefix for fonts when rendering Text document as HTML
*   Using single naming convention for HTML resources
*   Using ICacheDataHandler instead of IFileDataStore
*   Implementation of responsive output for rendering into HTML

## Document Rendering API for .NET - FixesFollowing issues have been fixed in version 17.8.0.

*   Exception when rendering Excel document into HTML and image
*   Exception when rendering email message containing .msg file as attachment
*   "Index was out of range" exception when rendering PDF to HTML
*   Unable to render PDF document in HTML/Image mode
*   Rendering MS Project document stops responding
*   Check boxes in PDF document are not rendered correctly

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/groupdocs-viewer-dotnet/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/channel/UCgO8dwgI5KAsQCVegviVXYA/playlists "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").





