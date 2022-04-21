---
title: 'Explicit Font Substitution is Supported in GroupDocs.Conversion for .NET 18.7'
date: Tue, 10 Jul 2018 12:14:14 +0000
draft: false
url: /2018/07/10/explicit-font-substitution-is-supported-in-groupdocs.conversion-for-.net-18.7/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-conversion-net.png)](https://www.groupdocs.com/products/conversion/net)

GroupDocs.Conversion for .NET 18.7 comes with some new features and a bug fix. EmailOptions can be defined in any SaveOptions class such as PdfSaveOptions or CellsSaveOptions. Moreover, API supports explicit font substitution when converting from Word, Cell and Presentation documents. Please refer to GroupDocs.Conversion for .NET 18.7 [release notes](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+18.7+Release+Notes) for further reference. We'd recommend you to integrate latest version of the API in your application and share your feedback.

# Features

Following features are introduced in this month's release:

## Explicit Font Substitution**Converting from Cells** Substitute specific fonts when converting Cells document.```
var loadOptions = new CellsLoadOptions();
loadOptions.FontSubstitutes.Add(new KeyValuePair("Arial", "Tahoma"));
loadOptions.FontSubstitutes.Add(new KeyValuePair("Calibri", "Tahoma"));
```**Converting from Slides** Substitute specific fonts when converting Slides document.```
var loadOptions = new SlidesLoadOptions();
loadOptions.FontSubstitutes.Add(new KeyValuePair("Arial", "Tahoma"));
loadOptions.FontSubstitutes.Add(new KeyValuePair("Calibri", "Tahoma"));
```**Converting from Words** Substitute specific fonts when converting Words document.```
var loadOptions = new WordsLoadOptions();
loadOptions.FontSubstitutes.Add(new KeyValuePair("Angsana New", "Arial Unicode MS"));
loadOptions.AutoFontSubstitution = false;
```

## EmailOptions in SaveOptions ClassEmail specific convert options.```
var options = new PdfSaveOptions
{
    EmailOptions =
    {
        DisplayHeader = true,
        DisplayEmailAddress = true,
        DisplayFromEmailAddress = true,
        DisplayToEmailAddress = true,
        DisplayCcEmailAddress = true,
        DisplayBccEmailAddress = true
    }
};
```

# Bug Fixes

*   Fonts loading folder is not properly set when converting from Words

# API Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [NuGet](https://www.nuget.org/packages/groupdocs.conversion) - Nuget install
*   [Documentation](https://docs.groupdocs.com/display/conversionnet/Home "Documentation") - Product Wiki
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPBhL0PgywST_NF74_4IF4k "video tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/conversion "Support forum") \- Technical Support Forum for GroupDocs.Conversion
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET "examples,plugins,showcases") - GitHub Source Code Examples

# Feedback

We always welcome you to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/conversion) and our dedicated support team will be there to respond.




