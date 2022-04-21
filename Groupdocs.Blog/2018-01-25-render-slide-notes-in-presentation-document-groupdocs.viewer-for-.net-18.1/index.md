---
title: 'Render Notes in Presentation Document using GroupDocs.Viewer for .NET 18.1'
date: Thu, 25 Jan 2018 03:25:49 +0000
draft: false
url: /2018/01/25/render-slide-notes-in-presentation-document-groupdocs.viewer-for-.net-18.1/
author: 'Usman Aziz'
summary: ''
tags: ['.NET API', '.NET document rendering API', '.net document viewer API', 'asp.net document viewer API', 'document rendering API', 'document viewer', 'Document Viewer API C#']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are delighted to announce the release of version 18.1 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). The latest version includes the support of rendering **Jpeg2000**, **PostScript**, **POTM** and **PPSM** file formats. Furthermore, we have added the option to show or hide the **notes** when rendering Presentation documents. This version also allows you to work with the layers in CAD documents. Let’s have a quick overview of GroupDocs.Viewer for .NET 18.1.

## Supported File FormatsWe have added the support of following file formats in version 18.1 of GroupDocs.Viewer for .NET.

*   POTM (Microsoft PowerPoint Macro-Enabled Template)
*   PPSM (Microsoft PowerPoint Macro-Enabled Show)
*   JPEG2000 (JP2, J2C, J2K, JPF, JPX, JPM)
*   PS (PostScript)

## Showing/Hiding Notes in Presentation DocumentThe Presentation document may also contain the notes. By default, the notes are not included in the rendering results. However, using version 18.1, you can choose between to show or hide the notes in the output. If you want to show notes in your rendering result, use _SlidesOptions.RenderNotes_ property of RenderOptions (_ImageOptions_ or _HtmlOptions_) as shown in sample code.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
   
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
string guid = "document.pptx";
   
// Set slides options to render notes
ImageOptions options = new ImageOptions();
options.SlidesOptions.RenderNotes = true; // Default value is false
  
// Get pages 
List pages = imageHandler.GetPages(guid, options);
   
foreach (PageImage page in pages)
{
   //...
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Getting List of Layers in CAD DocumentUsing layers in CAD documents is a way of organizing objects in the drawing by associating them with a specific function or a purpose. GroupDocs.Viewer for .NET 18.1 allows you to get the list of layers' names from the drawing. Just cast the _DocumentInfoContainer_ object returned by _GetDocumentInfo_ method of the _ViewerHandler_ and use _Layers_ property, as shown in the example below.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
config.UseCache = true;
   
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
string guid = "withLayers.dwg";
   
CadDocumentInfoContainer documentInfo = (CadDocumentInfoContainer) imageHandler.GetDocumentInfo(guid);
  
// Loop through all layers contained in the drawing 
foreach (string layer in documentInfo.Layers)
    Console.WriteLine("Layer name: {0}", layer);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Rendering Specific Layers of CAD DocumentUsing version 18.1, you can specify the layers that you want to render by adding layer names into the _CadOptions.Layers_ property of corresponding _RenderOptions_ (_ImageOptions_ or _HtmlOptions_) as shown in the example below.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
   
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
string guid = "document.dwg";
   
// Set CAD options to render two Layers
ImageOptions options = new ImageOptions();
options.CadOptions.Layers.Add("electrical");
options.CadOptions.Layers.Add("walls");
  
// Get pages 
List pages = imageHandler.GetPages(guid, options);
   
foreach (PageImage page in pages)
{
     Console.WriteLine("Page number: {0}", page.PageNumber); 
     Stream imageStream = page.Stream;
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Bug FixesFollowing issues are fixed in version 18.1 of GroupDocs.Viewer for .NET.

*   Header contains error message when rendering Word document as PDF
*   API is not creating cache files in CachePath when rendering document from network path

## ImprovementsFollowing are the improvements that we have made in version 18.1.

*   Set output page height and width (for image and HTML) depending on the rendered DWF document's page size
*   Create single styles resource when rendering Text documents as HTML
*   Improve exporting and embedding HTML resources when rendering SVG and Presentation documents

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on our **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").




