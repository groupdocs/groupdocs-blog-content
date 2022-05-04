---
title: 'Render a Part of MS Project Document using GroupDocs.Viewer for .NET 18.8'
date: Mon, 13 Aug 2018 05:51:50 +0000
draft: false
url: /2018/08/13/render-a-part-of-ms-project-document-using-groupdocs.viewer-for-.net-18.8/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'asp.net document viewer API', 'C# document viewer API', 'document viewer API for .net', 'GroupDocs.Viewer', 'GroupDocs.Viewer for .NET', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

Today, we are glad to announce the release of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) 18.8. In this version, we have introduced the feature of rendering a part of MS Project document specifying the start date and end date. We have also made it possible to set _ForcePasswordValidation_ property of the _ViewerConfig_ using the configuration files such as _app.config_ and _web.config_. Furthermore, the latest version also includes 14 improvements and bug fixes. Below is the list of new features, improvements, and fixes added in v18.8.

# Features Introduced

## Rendering a Part of MS Project DocumentYou can now render a part of MS Project document according to specified _StartDate_ and _EndDate_ properties of _ProjectOptions_ class as shown in the below code snippet. When only one of these properties is set, rendering starts from the project's start date or ends on the project's end date correspondingly.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
   
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
string guid = "document.mpp";
   
// Set Project options to render tasks from year 2018 only
ImageOptions options = new ImageOptions();
options.ProjectOptions.StartDate = new DateTime(2018, 01, 01);
options.ProjectOptions.EndDate = new DateTime(2018, 12, 31);
  
// Get pages 
List pages = imageHandler.GetPages(guid, options);
   
foreach (PageImage page in pages)
{
     Console.WriteLine("Page number: {0}", page.PageNumber); 
     Stream imageContent = page.Stream;
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

# Improvements

We have included following improvements in the latest version:

*   Security improvements
*   Rendering comments from Presentation documents into images when ExtractText option is enabled
*   Retrieving list of resources only when loading page from cache
*   Reduced count of calls to storage methods
*   Extended support for DefaultFontName option for MS Project documents rendering to image and HTML
*   Added ForcePasswordValidation configuration via configs
*   Extended support for rendering comments from ODP document format

# Bug Fixes

Following issues are fixed in version 18.8 of GroupDocs.Viewer for .NET.

*   Deadlock when rendering documents in multiple processes
*   An exception raises while retrieving HTML pages from the source document
*   Relative and absolute resource paths in the same HTML page
*   Exception when the file name contains curly braces
*   Legend is shifted and incorrect formatting when rendering PPTX as HTML
*   Incorrect font when rendering PPTX as HTML
*   Incorrect character position in HTML mode in Safari for iOS

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





