---
title: 'Render TSV and PCL Formats using GroupDocs.Viewer for .NET 18.11'
date: Tue, 06 Nov 2018 07:09:08 +0000
draft: false
url: /2018/11/06/render-tsv-and-pcl-formats-using-groupdocs.viewer-for-.net-18.11/
author: 'Usman Aziz'
summary: ''
tags: ['.net document viewer API', 'asp.net document viewer API', 'document viewer', 'Document Viewer API C#', 'PDF viewer']
categories: ['GroupDocs.Viewer for .NET', 'GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

Today, we are glad to announce the release of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) **18.11**. The latest version includes a couple of new features as well as a bunch of improvements and bug fixes. The API now supports rendering of **TSV** (Tab-separated values) and **PCL** (Printer Command Language) file formats. Below is the list of new features, improvements, and fixes added in v18.11.

# Features Introduced

Since v18.11, we have extended the list of supported file formats and now the API is capable of rendering the following formats:

*   TSV (Tab-separated values)
*   PCL (Printer Command Language)

For a complete list of supported file formats, please visit [this](https://docs.groupdocs.com/display/viewernet/Supported+Document+Formats) documentation article.

# Improvements

We have included the following improvements in version 18.11:

*   Rendering comments from ODP presentation documents that have no author
*   Rendering attachments while working with source document's stream (for sample code snippet, please visit the [documentation](https://docs.groupdocs.com/viewer/net/developer-guide/))
*   Extended support for **_ExcludeFonts_** setting of **_HtmlOptions_** class for _MS OneNote_ documents
*   Exporting font files as external resources when rendering _MS OneNote_ documents
*   Added support for **_DefaultFontName_** option when rendering _MS OneNote_ documents

# Bug Fixes

Following issues are fixed in version 18.11 of GroupDocs.Viewer for .NET.

*   Exception when rendering email message containing ._msg_ file as attachment
*   Issues when rendering Japanese PDF document to HTML
*   Font lightness is ignored for rendering Presentations into HTML
*   Resources are not created in cache after **_GetPrintableHtml()_** is called
*   Unexpected behavior of cache when both Image and Html handlers are instantiated
*   Missing _pst_ and _ost_ formats in _**GetSupportedDocumentFormats()**_

# Related Links and Resources

We have a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Viewer.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - Install GroupDocs.Viewer using NuGet
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Examples / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications
*   [Technical Support Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum for GroupDocs.Viewer

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").




