---
title: 'Working with Folders Contained in Outlook Data Files using GroupDocs.Viewer for .NET 18.12'
date: Thu, 20 Dec 2018 08:02:26 +0000
draft: false
url: /2018/12/20/working-with-folders-contained-in-ostpst-formats-groupdocs.viewer-for-.net-18.12/
author: 'Usman Aziz'
summary: ''
tags: ['.net document viewer API', '.net pdf viewer', 'asp.net document viewer API', 'asp.net pdf viewer', 'C# document viewer API']
categories: ['GroupDocs.Viewer for .NET', 'GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are pleased to announce the monthly release of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) **18.12**. This release includes three new features, two bug fixes, and four improvements. By upgrading to the latest version, you'll be able to get the list of folders and render messages from a specific folder contained in Outlook Data Files (**OST/PST**). Furthermore, it also allows you to ignore empty columns when rendering Excel documents. Below is the list of new features, fixes, and the improvements added in version 18.12.

# Features Introduced

## Working with Folders Contained in OST/PST FormatsGroupDocs.Viewer now also allows you to deal with the folders and the sub-folders in Outlook Data File documents (**OST/PST**). You can retrieve the list of the folders contained by a document and render the messages from a specific folder or the sub-folder such as Inbox, Sent Items, Deleted, Inbox\\Sub\_Folder\_1 etc. This feature is available for rendering the document into HTML, image, and PDF. For working examples, please visit the following documentation articles:

*   [Retrieving the List of Outlook Folders](https://docs.groupdocs.com/viewer/net)
*   [Rendering Messages from Specified Folder](https://docs.groupdocs.com/viewer/net)

## Ignoring Empty Columns in Excel DocumentsSometimes Excel worksheet contains the empty columns along with the columns populated with data. In this case, if the number of empty columns is considerably huge, the rendering time increases and hence, it affects the performance. For such cases, we have introduced a new feature that ignores the empty columns using **_CellsOptions.IgnoreEmptyColumns_** property. For a working example, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

# Improvements

We have included the following improvements in version 18.12:

*   Ignore empty string when it is passed as path to directory with fonts
*   Improve rendering into HTML for Outlook Data Files with subfolders and empty folders
*   Set exception localization feature as obsolete
*   Prevent rendering frozen and invisible CAD layers by default

# Bug Fixes

Following issues are fixed in version 18.12 of GroupDocs.Viewer for .NET.

*   PDF contains blank page when rendering XPS to PDF
*   Issue with the image source when rendering Excel to HTML with embedded resources

# Related Links and Resources

We have a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Viewer.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - Install GroupDocs.Viewer using NuGet
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Examples / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications
*   [Technical Support Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum for GroupDocs.Viewer

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").




