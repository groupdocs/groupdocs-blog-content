---
title: 'PDF Conversion is Improved in GroupDocs.Conversion for .NET 18.8'
date: Wed, 15 Aug 2018 15:02:39 +0000
draft: false
url: /2018/08/15/pdf-conversion-is-improved-in-groupdocs.conversion-for-.net-18.8/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-conversion-net.png)](https://www.groupdocs.com/products/conversion/net)

GroupDocs.Conversion for .NET 18.8 comes with some new features, improvements and a bug fix. **PdfFormattingOptions** class is introduced when converting to PDF format. Some of the obsolete constructors and properties are removed. Moreover, there's also a security improvement. Please refer to GroupDocs.Conversion for .NET 18.8 release notes for further reference. We'd recommend you to integrate latest version of the API in your applications and share your feedback.

# Features

## PdfFormattingOptions when converting to PDF```
var saveOptions = new PdfSaveOptions();
saveOptions.PdfOptions.FormatingOptions.PageMode = PdfFormatingOptions.PdfPageMode.FullScreen;
saveOptions.PdfOptions.FormatingOptions.PageLayout = PdfFormatingOptions.PdfPageLayout.SinglePage;
```

## Implement specific options for converting TXT documents```
var loadOptions = new TxtLoadOptions
{
   DetectNumberingWithWhitespaces = false,
   LeadingSpacesOptions = TxtLoadOptions.TxtLeadingSpacesOptions.Trim,
   TrailingSpacesOptions = TxtLoadOptions.TxtTrailingSpacesOptions.Trim
};
```

# Improvements

*   Automatically add extension of the converted file if not set
*   Remove obsolete constructors and properties
*   Image to PDF conversion improvement
*   Improve per page savings when converting to Words, Images, Slides, Cells, Pdf, Xps, Html
*   Security improvements update

# Bug Fixes

*   Exception when cache is enabled

# API Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [NuGet](https://www.nuget.org/packages/groupdocs.conversion) - Nuget install
*   [Documentation](https://docs.groupdocs.com/display/conversionnet/Home "Documentation") - Product Wiki
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPBhL0PgywST_NF74_4IF4k "video tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/conversion "Support forum") \- Technical Support Forum for GroupDocs.Conversion
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET "examples,plugins,showcases") - GitHub Source Code Examples

# Feedback

We always welcome you to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/conversion) and our dedicated support team will be there to respond.




