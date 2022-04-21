---
title: 'Control Image Quality when Rendering PDF Document as HTML using GroupDocs.Viewer for .NET 18.3'
date: Sun, 11 Mar 2018 16:24:41 +0000
draft: false
url: /2018/03/11/control-image-quality-when-rendering-pdf-document-as-html-using-groupdocs.viewer-for-.net-18.3/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'document rendering API', 'document viewer API for .net', 'document viewer API for asp.net']
categories: ['GroupDocs.Viewer', 'GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are pleased to announce the release of version 18.3 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). Using the latest version, you can now render **XLTM** and **XLTX** file formats. We have also added settings to control the image quality when rendering PDF documents as HTML. Furthermore, this version came up with 11 improvements and bug fixes. Let’s have a quick overview of GroupDocs.Viewer for .NET 18.3.

## Supported File FormatsWe have added the support of following file formats in version 18.3 of GroupDocs.Viewer for .NET.

*   XLTM (Excel Open XML Macro-Enabled Spreadsheet)
*   XLTX (Excel Open XML Spreadsheet Template)

## Specifying Image Quality when Rendering PDF Documents as HTMLWhen rendering PDF documents as HTML, GroupDocs.Viewer creates a single image resource which contains all the images from the PDF document page. The API uses this image as the background for output HTML document. Since version 18.3, we have added the settings that are used to control the quality of the image resource. Following code sample shows how to get the best quality images when rendering PDF document as HTML.```
//Init viewer configuration
ViewerConfig viewerConfig = new ViewerConfig();
viewerConfig.StoragePath = "c:\\storage";
   
// Init ViewerHtmlHandler 
ViewerHtmlHandler viewerHtmlHandler = new ViewerHtmlHandler(viewerConfig);
   
// Set the guid of the document you want to render
string guid = "with-images.pdf";
   
//Set desired image quality in the output HTML document
HtmlOptions htmlOptions = new HtmlOptions();
htmlOptions.PdfOptions.ImageQuality = ImageQuality.High;
  
//Render document with specified options
List pages = viewerHtmlHandler.GetPages(guid, htmlOptions);

foreach (PageHtml page in pages)
{
    //..
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Bug FixesFollowing issues are fixed in version 18.3 of GroupDocs.Viewer for .NET.

*   Text is garbled when rendering Arabic PDF
*   Blur output when rendering PDF as HTML
*   Printable HTML gets messy when adding watermark
*   Content minification prevents styles loading
*   Access to the path "../../fd.xml" is denied
*   ViewerConfig.FontDirectories property is not working for Presentation documents
*   Converting DNG image into JPG provides output with light spots

## ImprovementsFollowing are the improvements that we have made in version 18.3.

*   Extended support of HtmlOptions.ExcludeFonts option for Text documents
*   Improved rendering of MS OneNote documents into HTML by providing pure HTML and SVG
*   Exporting contained images when rendering SVG to HTML
*   Extended support of ShowHiddenSlides option for Open Document Presentation
*   Improved rendering of metafile images into HTML

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on our **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").




