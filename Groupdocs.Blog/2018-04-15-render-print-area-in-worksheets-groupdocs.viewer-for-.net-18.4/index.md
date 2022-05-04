---
title: 'Render Print Area in Worksheets using GroupDocs.Viewer for .NET 18.4'
date: Sun, 15 Apr 2018 15:38:28 +0000
draft: false
url: /2018/04/15/render-print-area-in-worksheets-groupdocs.viewer-for-.net-18.4/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'asp.net document viewer API', 'C# document viewer API', 'document rendering API', 'document viewer', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

Here we go! Another monthly release of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) is out now. In the current release, you will find new options to render print area and to include or exclude hidden columns and rows in the **Cells** documents. Furthermore, we have added the support of rendering **POTX**, **PPTM**, and **EPS** file formats. Below you find the list of new features, improvements, and fixes added in GroupDocs.Viewer for .NET 18.4.

## Supported File FormatsWe have added the support of following file formats in this version.

*   POTX (PowerPoint Open XML Presentation Template)
*   PPTM (PowerPoint Open XML Macro-Enabled Presentation)
*   EPS (Encapsulated PostScript)

## Managing Text Overflow when Rendering Cells DocumentsWhen cells documents are rendered into HTML, overflowed text inside the cell overlays subsequent cells until it meets non-empty cell. To expand the cell width to fit the overflowed text, we have added a new option _TextOverflowMode.AutoFitColumn_ for _CellsOptions.TextOverflowMode_ property of _HtmlOptions_, _ImageOptions_ or _PdfOptions_ classes. The following code sample shows how to use this feature.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
   
// Create html handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
string guid = "document.xlsx";
   
// Set Cells options to hide overflowing text
HtmlOptions options = new HtmlOptions();
options.CellsOptions.TextOverflowMode = TextOverflowMode._AutoFitColumn_;
  
// Get pages 
List pages = htmlHandler.GetPages(guid, options);
   
foreach (PageHtml page in pages)
{
    Console.WriteLine("Page number: {0}", page.PageNumber);
    Console.WriteLine("Html content: {0}", page.HtmlContent);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Rendering Print Area in Cells DocumentsStarting from 18.4, GroupDocs.Viewer provides a new option _RenderPrintAreaOnly _in _GroupDocs.Viewer.Converter.Options.CellsOptions_class which enables rendering sections of the worksheet(s) defined as [print area](https://support.office.com/en-us/article/set-or-clear-a-print-area-on-a-worksheet-27048af8-a321-416d-ba1b-e99ae2182a7e). GroupDocs.Viewer renders each print area in a worksheet as a separate page. The following code sample shows how to use this feature.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
  
// Create html handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
string guid = "document.xlsx";
  
// Enable redering of print area
HtmlOptions options = new HtmlOptions();
options.CellsOptions.RenderPrintAreaOnly = true;
  
// Get pages 
List pages = htmlHandler.GetPages(guid, options);
  
foreach (PageHtml page in pages)
{
    Console.WriteLine("Page number: {0}", page.PageNumber);
    Console.WriteLine("Html content: {0}", page.HtmlContent);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Rendering Hidden Rows and ColumnsSometimes cells document may contain hidden columns and rows. By default, hidden columns and rows are not rendered by the API. However, you can now control the inclusion of hidden content in the rendering results using _ShowHiddenRows _and _ShowHiddenColumns_ properties of _GroupDocs.Viewer.Converter.Options.CellsOptions_class as shown in the following code sample.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
  
// Create html handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
string guid = "document.xlsx";
  
// Enable redering of hidden rows and columns
HtmlOptions options = new HtmlOptions();
options.CellsOptions.ShowHiddenRows = true;
options.CellsOptions.ShowHiddenColumns = true;
  
// Get pages 
List pages = htmlHandler.GetPages(guid, options);
  
foreach (PageHtml page in pages)
{
    Console.WriteLine("Page number: {0}", page.PageNumber);
    Console.WriteLine("Html content: {0}", page.HtmlContent);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Simple File Storage InterfaceStarting from v18.4, GroupDocs.Viewer provides the simple interface _IFileStorage_ to implement custom file storage. This interface is an alternative to complex and overloaded _ICacheDataHandler_ and _IInputDataHandler_ interfaces. For sample implementations of custom file storage, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Bug FixesFollowing issues are fixed in version 18.4 of GroupDocs.Viewer for .NET.

*   Invalid PDF when rendering Excel document with multiple pages per sheet
*   DefaultFontName setting is not working for rendering Text documents into PDF and image
*   Incorrect rendering of the content in header and footer of Word document
*   Local links are ignored when rendering PDF to HTML
*   Discrepancy when rendering as JPEG and HTML

## ImprovementsFollowing are the improvements that we have made in version 18.4.

*   Added prefix for CSS classes when rendering Email messages
*   Minified CSS content when rendering into HTML with EnableMinification is set to true
*   Improved rendering comments from Presentation documents
*   Added support JpegQuality option when rendering Microsoft Project documents
*   Extended support for DefaultFontName setting to PDF documents when rendering into HTML
*   Responsive HTML output required in the case of HTML representation

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on our **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").





