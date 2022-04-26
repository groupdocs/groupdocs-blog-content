---
title: 'Introducing HTML Minification in GroupDocs.Viewer for .NET 17.12'
date: Thu, 28 Dec 2017 06:12:12 +0000
draft: false
url: /2017/12/28/introducing-html-minification-in-groupdocs.viewer-for-.net-17.12/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'asp.net document viewer API', 'C# document viewer API', 'Document viewer API', 'document viewer API for .net', 'document viewer API for asp.net']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are back with another version of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). In this release, we have added **HTML minification** for optimized rendering of documents into HTML. Not only this, we have also introduced rendering of **MS Project** documents by specifying time intervals. Let’s have a quick overview of some exciting features of GroupDocs.Viewer for .NET 17.12.

# .NET Document Rendering API - New Features

## HTML MinificationWhen you are looking for the ways to optimize the rendering of documents into HTML, one of the solutions you might want to use is the compression of the output content (HTML, CSS, and SVG). This solution is suitable in case you are providing your content from the web server over the internet. GroupDocs.Viewer provides **EnableMinification **property of **HtmlOptions** class that lets you get output content minified (as shown in below code sample).```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
  
// Create HTML handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
string guid = "document.docx";
  
HtmlOptions options = new HtmlOptions();
options.EnableMinification = true;
List pages = htmlHandler.GetPages(guid, options);
  
foreach (PageHtml page in pages)
{
    Console.WriteLine("Page number: {0}", page.PageNumber);
    Console.WriteLine("Html content: {0}", page.HtmlContent);
} 
```Currently, minification is only applied to HTML. However, we are going to provide minification for CSS as well in upcoming versions of the API. For more details, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Rendering MS Project Document with Custom Page Size and Time UnitWhen you are rendering MS Project documents into image, HTML or PDF, GroupDocs.Viewer API tries to find optimal output size and time unit depending on the project's overall length. In case you need to set your own page size or time unit, you can set **ProjectOptions** class properties of corresponding  **RenderOptions ** (**HtmlOptions** or **ImageOptions**) or **PdfFileOptions** class for rendering into PDF,  as shown in the example below.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
   
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
string guid = "document.mpp";
   
// Set Project options to render content with a specified size and time unit.
ImageOptions options = new ImageOptions();
options.ProjectOptions.PageSize = PageSize.A2;
options.ProjectOptions.TimeUnit = TimeUnit.Days;
  
// Get pages 
List pages = imageHandler.GetPages(guid, options);
   
foreach (PageImage page in pages)
{
     Console.WriteLine("Page number: {0}", page.PageNumber); 
     Stream imageContent = page.Stream;
} 
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Removing Cache Files of a Specific DocumentOn the request of our valuable customers, we have added the support of removing cache files for a specific document. Following code sample demonstrates the usage of this feature.```
//Init viewer config
ViewerConfig viewerConfig = new ViewerConfig();
viewerConfig.StoragePath = "c:\\storage"; 

// Init viewer image or HTML handler 
ViewerImageHandler viewerImageHandler = new ViewerImageHandler(viewerConfig); 

// Set the guid of the document you want to clear. 
string guid = "document.docx"; 

//Clear files from cache related to specified document. 
viewerImageHandler.ClearCache(guid);
```For more details on clear cache feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Support of ODG FormatSince version 17.12, we have added the support of rendering **ODG** (OpenDocument Graphics) file format.

## Improved Rendering of JPEG Image as HTMLIn previous versions of the API, the JPEG image was converted into PNG format ensuring the high quality of the image when it is displayed inside the HTML page. However, it was resulting in the bigger size of the output HTML page. Therefore, we have implemented the feature of rendering JPEG as HTML without converting image format to PNG.

# Document Viewer API for .NET - Fixes

Following issues are fixed in version 17.12 of GroupDocs.Viewer for .NET.

*   "Index was out of range" exception when rendering XLSX as PDF
*   Blank output when rendering PDF document as HTML
*   CAD document layouts with the size different than model are not rendered correctly
*   Alignment of radio button text and checkbox text is not proper

# Related Links and Resources

We have a few channels and resources for you to download, learn, try and get technical support on **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - Github Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").




