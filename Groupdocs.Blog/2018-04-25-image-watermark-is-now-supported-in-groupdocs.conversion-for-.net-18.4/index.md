---
title: 'Image Watermark is now Supported in GroupDocs.Conversion for .NET 18.4'
date: Wed, 25 Apr 2018 07:53:23 +0000
draft: false
url: /2018/04/25/image-watermark-is-now-supported-in-groupdocs.conversion-for-.net-18.4/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-conversion-net.png)](https://www.groupdocs.com/products/conversion/net)

Following our monthly release process, GroupDocs.Conversion for .NET 18.4 has been released and available for [download](https://www.nuget.org/packages/groupdocs.conversion). This release covers some new features, one improvement and a bug fix. You can specify bookmark, headings and expanded level when converting from Words to PDF and XPS. Grayscale PDF conversion is introduced. Aside these, HTML 5 compliant markup generation is improved. For further details included in this month’s release, please visit the [release notes](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+18.4+Release+Notes). We'd recommend you to integrate latest version of the API in your application and share your feedback.

# Features

## Specify bookmark, headings and expanded levelAPI allows to specify bookmark, headings and expanded level when converting from Words to PDF and XPS formats.

## Option for creating Linearize PDF when converting to PDF```
var saveOptions = new PdfSaveOptions();
saveOptions.PdfOptions.Linearize = true; 
```

## Implement option for converting to grayscale PDF```
var saveOptions = new PdfSaveOptions();
saveOptions.PdfOptions.Grayscale = true; 
```

## Resource optimization when converting to PDF```
var saveOptions = new PdfSaveOptions();
  
// all images in the document are re-compressed. The compression is defined by the ImageQuality property.
saveOptions.PdfOptions.OptimizationOptions.CompressImages = true;
  
//  value in percent where 100% is unchanged quality and image size. To decrease the image size, use ImageQuality less than 100
saveOptions.PdfOptions.OptimizationOptions.ImageQuality = 50;
  
// Link duplcate streams
saveOptions.PdfOptions.OptimizationOptions.LinkDuplcateStreams = true;
  
// Remove unused objects
saveOptions.PdfOptions.OptimizationOptions.RemoveUnusedObjects = true;
  
// Remove unused streams
saveOptions.PdfOptions.OptimizationOptions.RemoveUnusedStreams = true;
  
// Make fonts not embedded if set to true
saveOptions.PdfOptions.OptimizationOptions.UnembedFonts = true; 
```

## Image watermarkA new property **byte\[\] Image** is introduced.```
byte[] image = System.IO.File.ReadAllBytes ( "image.jpg" );
var saveOptions = new PdfSaveOptions();
saveOptions.WatermarkOptions.Image = image; 
```

# Improvements

*   Create HTML 5 compliant markup when converting to html

# Bug Fixes

*   Index was outside the bound of the array, when cache is enabled and watermarks are applied

# API Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [Downloads](https://downloads.groupdocs.com/conversion/net) - MSI Package as well as Zipped DLLs
*   [NuGet](https://www.nuget.org/packages/groupdocs.conversion) - Nuget install
*   [Documentation](https://docs.groupdocs.com/display/conversionnet/Home "Documentation") - Product Wiki
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPBhL0PgywST_NF74_4IF4k "video tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/conversion "Support forum") \- Technical Support Forum for GroupDocs.Conversion
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET "examples,plugins,showcases") - GitHub Source Code Examples

# Feedback

We always welcome you to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/conversion) and our dedicated support team will be there to respond.




