---
title: 'Exclude Specific Fonts from Output HTML using GroupDocs.Viewer for .NET 18.10'
date: Fri, 05 Oct 2018 07:52:19 +0000
draft: false
url: /2018/10/05/exclude-specific-fonts-from-output-html-using-groupdocs.viewer-for-.net-18.10/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'asp.net document viewer', 'C# document viewer API', 'document rendering API', 'document viewer', 'GroupDocs.Viewer for .NET', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are pleased to announce the release of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) **18.10**. The latest version allows setting the list of the fonts that should be excluded from the output HTML to decrease the size of the output files. Furthermore, the inclusion of **5** improvements and **6** bug fixes have made the API more promising. Below is the list of new features, improvements, and fixes added in v18.10.

# Features Introduced

## Setting List of the Fonts to be ExcludedAdding fonts into HTML ensures that the text from the original document will appear similar in HTML, regardless of whether fonts are installed on the viewer's device or not. At the same time, this improvement comes with the cost of the increased size of the output file.Therefore, GroupDocs.Viewer API provides a new setting - **HtmlOptions.ExcludeFontsList**, that prevents adding specific fonts (that are commonly available on most of the devices). The code sample below shows how to prevent adding fonts into output HTML.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
  
// Create html handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
string guid = "presentation.pptx";
  
HtmlOptions options = new HtmlOptions();
options.ExcludeFontsList.Add("Times New Roman");
options.ExcludeFontsList.Add("Arial");
List pages = htmlHandler.GetPages(guid, options);
  
  
foreach (PageHtml page in pages)
{
    Console.WriteLine("Page number: {0}", page.PageNumber);
    Console.WriteLine("Html content: {0}", page.HtmlContent);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

# Improvements

We have included following improvements in version 18.10:

*   Prevent showing items beyond StartDate and EndDate options when rendering MS Project documents
*   Release internal resources for methods which accept URL
*   GetDocumentInfo method's page number depending on the type of ViewerHandler
*   Prevent setting malicious values for HtmlResourcePrefix
*   Improve setting PageSize and TimeScale for MS Project documents by default

# Bug Fixes

Following issues are fixed in version 18.10 of GroupDocs.Viewer for .NET.

*   "Specified watermark font not found" exception when calling _GetPdfFile_ method
*   _OutlookOptions.MaxItemsInFolder_ option not working properly for rendering into image and PDF
*   Incorrect rendering of PDF document into HTML
*   Duplicate link tag when rendering text documents with external resources
*   Exception when rendering PDF document as HTML
*   Images are missing when rendering PDF document into HTML or Image

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





