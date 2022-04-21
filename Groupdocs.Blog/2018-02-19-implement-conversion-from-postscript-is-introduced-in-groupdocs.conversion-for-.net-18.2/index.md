---
title: 'Implement conversion from PostScript documents using GroupDocs.Conversion for .NET 18.2'
date: Mon, 19 Feb 2018 10:22:53 +0000
draft: false
url: /2018/02/19/implement-conversion-from-postscript-is-introduced-in-groupdocs.conversion-for-.net-18.2/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-conversion-net.png)](https://www.groupdocs.com/products/conversion/net)

We are pleased to announce our next version [GroupDocs.Conversion for .NET 18.2](https://www.nuget.org/packages/groupdocs.conversion). This release covers two new features, one improvement and a bug fix. Blank rows and columns could be skipped when converting Cells document. For further details included in this month’s release, please visit the [release notes](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+18.2+Release+Notes). Following sections will provide you the details about the new features of the API.

# .NET Document Conversion API – New Features

## Convert specific range when converting cells documentConvert specific range when converting to other than cells format. Example: "D1:F8" Following code sample shows how to convert specific range:```
var saveOptions = new PdfSaveOptions();
saveOptions.CellsOptions.ConvertRange = "D1:F8"; 
```

## Conversion from PostScriptConversion from PostScript document is introduced.

# GroupDocs Document Conversion API - Improvements

*   Implement configuration option for selecting if blank rows and columns should be skipped when converting Cells document

# GroupDocs.Conversion for .NET 18.2 - Bug Fixes

*   Just print area is getting converted, not the entire spreadsheet

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




