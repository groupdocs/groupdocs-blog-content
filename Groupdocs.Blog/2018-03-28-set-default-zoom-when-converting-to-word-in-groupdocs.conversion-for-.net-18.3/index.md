---
title: 'Set a Watermark as Background in GroupDocs.Conversion for .NET 18.3'
date: Wed, 28 Mar 2018 11:08:09 +0000
draft: false
url: /2018/03/28/set-default-zoom-when-converting-to-word-in-groupdocs.conversion-for-.net-18.3/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-conversion-net.png)](https://www.groupdocs.com/products/conversion/net)

Another monthly release of [GroupDocs.Conversion for .NET 18.3](https://www.nuget.org/packages/groupdocs.conversion) is on-board. This release covers some new features, few improvement and a bug fix. API allows developers to set default zoom when converting to Cells, Words and Slides. However, zoom option for PDF conversion is improved, PSD to PDF conversion is improved and XPS to PDF conversion issue is fixed. For further details included in this month’s release, please visit the [release notes](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+18.3+Release+Notes)

# Features

*   Set default zoom when converting to Cells, Words and Slides
*   Specific options for converting CSV documents

# New Properties Introduced

## DefaultFont in CellsLoadOptions Class```
var config = new ConversionConfig();
var conversionHandler = new ConversionHandler(config);
var loadOptions = new CellsLoadOptions();
loadOptions.DefaultFont = "Verdana";
var saveOptions = new PdfSaveOptions();
var convertedDocument = conversionHandler.Convert("source.xlsx", loadOptions, saveOptions); 
```

## Detect page orientation for the supported formats```
var documentInfo = conversionHandler.GetDocumentInfo("source.docx");
Console.Write(documentInfo.PageOrientation); 
```

## Show watermark behind the text```
var saveOptions = new PdfSaveOptions();
saveOptions.WatermarkOptions.Background = true; 
```

# Improvements

*   Set zoom when converting to Pdf document
*   Update API for getting document info to detect page orientation for the supported formats
*   Set default font to replace all missing fonts when converting Words and Cells document
*   Conversion improvement when converting Psd and Odg to Pdf

# Bug Fixes

*   XPS to PDF conversion failed

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




