---
title: 'Tiled Rendering of CAD Documents using GroupDocs.Viewer for .NET 18.6'
date: Tue, 12 Jun 2018 18:35:57 +0000
draft: false
url: /2018/06/12/tiled-rendering-of-cad-documents-using-groupdocs.viewer-for-.net-18.6/
author: 'Usman Aziz'
summary: ''
tags: ['.NET document rendering API', '.net document viewer API', 'C# document viewer API', 'document viewer', 'Document viewer API', 'PDF viewer']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are pleased to announce the release of version 18.6 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). The latest version provides the support of rendering **DXF** format as well as the tiled rendering of the **CAD** documents. Furthermore, we have added the feature of forced password validation for password protected documents. Along with the new features, there are 14 improvements and bug fixes in this monthly release. Below is the list of new features, improvements, and fixes added in GroupDocs.Viewer for .NET 18.6.

## Supported File FormatsGroupDocs.Viewer for .NET 18.6 supports rendering of DXF file format. For a complete list of supported file formats, please visit [this](https://docs.groupdocs.com/display/viewernet/Supported+Document+Formats) documentation article.

## Forced Password ValidationWhen password protected documents are rendered with the caching enabled, document password is validated only on the first call. All subsequent renderings provide output without checking the document password. In order to alter this behavior and let the API validate document password on each rendering, set _ForcePasswordValidation_ property of the _ViewerConfig_ as shown in the code snippet below.```
//Init viewer config
ViewerConfig viewerConfig = new ViewerConfig();
viewerConfig.StoragePath = "c:\\storage";
  
//Set the password to be validated on every call
viewerConfig.ForcePasswordValidation = true;
// Init viewer html handler
ViewerHtmlHandler viewerHtmlHandler = new ViewerHtmlHandler(viewerConfig);
   
// Set the guid of the document you want to render
string guid = "with-images.pdf";
   
//Set document password
HtmlOptions htmlOptions = new HtmlOptions();
htmlOptions.Password = "documentpassword";
  
//Render document with specified options
List pages = viewerHtmlHandler.GetPages(guid, htmlOptions);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Tiled Rendering or Rendering by Coordinates of CAD DocumentsTiled rendering (or rendering by coordinates) is the process of rendering CAD documents (into an image, HTML or PDF) by dividing into square parts and rendering each part (or tile) separately. In tiled rendering, the amount of memory involved is reduced as compared to rendering the entire document at once. Since the version 18.6, tiled rendering is available for rendering DWG file format into image and HTML. When the tiled rendering is enabled, only the Model is rendered, and every tile composes a separate page. You can add as many tiles as you need. The following code snippet demonstrates how to render DWG drawing into an image by dividing into four equal parts.```
 // Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.StoragePath = @"C:\storage";
   
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
string guid = "document.dwg";
   
// Get document width and height
DocumentInfoContainer docInfo = imageHandler.GetDocumentInfo(guid);
int width = docInfo.Pages[0].Width;
int height = docInfo.Pages[0].Height;
  
// Set tile width and height as a half of image total width
int tileWidth = width / 2;
int tileHeight = height / 2;
  
int pointX = 0;
int pointY = 0;
//Create image options and add four tiles, one for each quarter
ImageOptions options = new ImageOptions();
Tile tile = new Tile(pointX, pointY, tileWidth, tileHeight);
options.CadOptions.Tiles.Add(tile);
pointX += tileWidth;
tile = new Tile(pointX, pointY, tileWidth, tileHeight);
options.CadOptions.Tiles.Add(tile);
  
pointX = 0;
pointY += tileHeight;
tile = new Tile(pointX, pointY, tileWidth, tileHeight);
options.CadOptions.Tiles.Add(tile);
  
pointX += tileWidth;
tile = new Tile(pointX, pointY, tileWidth, tileHeight);
options.CadOptions.Tiles.Add(tile);
// The pages list will contain four images, one for each quarter
List pages = imageHandler.GetPages(guid, options);
   
foreach (PageImage page in pages)
{
     Console.WriteLine("Page number: {0}", page.PageNumber); 
     Stream imageContent = page.Stream;
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Bug FixesFollowing issues are fixed in version 18.6 of GroupDocs.Viewer for .NET.

*   Access to the path 'c:\\windows\\system32\\inetsrv\\vs.bin' is denied
*   Can't set different default fonts when rendering PDF document
*   Incorrect rendering of items with background color in Visio document
*   GetFileList throws "Guid for file should contain extension" when file has no extension
*   Some STL files are not supported
*   Text color is incorrect when rendering PDF
*   The content of the cell is hidden when rendering Excel to HTML
*   Unable to render Presentation documents, after ViewerConfig.FontDirectories are added
*   Wrong number of layouts in DXF

## ImprovementsFollowing are the improvements that we have made in version 18.6.

*   Extended support for _DefaultFontName_ setting to PDF documents when rendering into PDF
*   Added new property _EmbedResources_ which will replace _IsResourcesEmbedded_ property in _HtmlOptions_ class
*   Support of empty string for _ViewerConfig.CacheFolderName_ property
*   Eliminated the gap between the list of tasks and footer when rendering MS Project documents
*   Extended support for _DefaultFontName_ option for CAD documents

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on our **document viewer API**.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - Install GroupDocs.Viewer using NuGet
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Examples / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications
*   [Technical Support Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum for GroupDocs.Viewer

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").




