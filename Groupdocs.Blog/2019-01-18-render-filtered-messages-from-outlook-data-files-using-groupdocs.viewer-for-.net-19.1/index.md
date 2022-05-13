---
title: 'Render Filtered Messages from Outlook Data Files using GroupDocs.Viewer for .NET 19.1'
date: Fri, 18 Jan 2019 10:03:57 +0000
draft: false
url: /2019/01/18/render-filtered-messages-from-outlook-data-files-using-groupdocs.viewer-for-.net-19.1/
author: 'Usman Aziz'
summary: ''
tags: ['dotNET document rendering API', 'dotNET document viewer API', 'dotNET pdf viewer', 'dotNET viewer for Office Document', 'C# document viewer API', 'document rendering API', 'document viewer for .net', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are delighted to announce that we have rolled out version 19.1 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). The latest version brings five new features, three bug fixes, and three improvements. You can now obtain the email messages as well as filter the messages contained in Outlook Data Files (OST/PST). Furthermore, we have extended our list of supported file formats by adding the support of VCF file format. Please have a look at the [release notes](https://docs.groupdocs.com/display/viewernet/GroupDocs.Viewer+for+.NET+19.1+Release+Notes) for more details on new features, fixes, and improvements.

# Features Introduced

## Rendering Filtered Messages from Outlook Data FilesThere might be the case when you want to render only the selected messages from Outlook Data Files (OST/PST). To deal with such case, we have introduced a new feature which allows you to filter the messages that you want to render from Outlook Data Files. At the moment, the following filters are available:

*   Filter by subject and content using **_OutlookOptions.TextFilter_**
*   Filter by the sender's and recipient's email addresses using **_OutlookOptions.AddressFilter_**

For a working example, please visit the following documentation article:

*   [Rendering Filtered Messages in Outlook Data Files](https://docs.groupdocs.com/viewer/net)

## Rendering Email Messages Contained in Outlook Data FilesGroupDocs.Viewer for .NET now supports getting and rendering email messages that are contained in Outlook Data Files as attachments. These email messages are listed as **_Attachments _**in **_DocumentInfoContainer _**object that is returned by **_GetDocumentInfo _**method of the corresponding **_ViewerHandler_**. For working examples, please visit the following documentation article:

*   [Obtaining and Rendering Email Messages Contained in Outlook Data Files](https://docs.groupdocs.com/viewer/net)

## Obtaining Layer's Visibility Status in CAD DocumentsThe CAD document allows setting the visibility of the layers it contains. The layers are invisible when they frozen or switched off, otherwise, they are visible. The latest release of GroupDocs.Viewer for .NET allows getting the visibility status of the layers within a CAD document. This feature can be useful to decide which layer to render relying on a layer's visibility status. For a working example, please visit the following documentation article:

*   [Obtaining Layer's Visibility Status in CAD Documents](https://docs.groupdocs.com/viewer/net)

## Support for VCF File FormatSince version 19.1, GroupDocs.Viewer for .NET allows you to render VCF file format. Please visit [this](https://docs.groupdocs.com/display/viewernet/Supported+Document+Formats) article for a complete list of the supported file formats.

# Improvements

We have included the following improvements in version 19.1.

*   Added support for rendering password protected ODS documents
*   Simplified caching interface
*   Added descriptive exception message when non-existing default font name is set

# Bug Fixes

The following issues are fixed in the latest release of GroupDocs.Viewer for .NET.

*   Header is missing when rendering Word document
*   Exception when getting document info of .msg file using _MemoryStream_
*   Images are not visible in Chrome browser when rendering OneNote documents

# Related Links and Resources

We have a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Viewer for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - Install GroupDocs.Viewer for .NET using NuGet
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Documentation
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Examples / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications
*   [Technical Support Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum for GroupDocs.Viewer for .NET

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").





