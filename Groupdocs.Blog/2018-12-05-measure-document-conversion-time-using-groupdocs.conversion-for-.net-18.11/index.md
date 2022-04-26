---
title: 'Measure Document Conversion Time using GroupDocs.Conversion for .NET 18.11'
date: Wed, 05 Dec 2018 11:53:22 +0000
draft: false
url: /2018/12/05/measure-document-conversion-time-using-groupdocs.conversion-for-.net-18.11/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-conversion-net.png)](https://www.groupdocs.com/products/conversion/net)

GroupDocs.Conversion for .NET 18.11 comes with a lot of new features and some improvements. Conversion from EPS, TSV and PCL formats is introduced. Furthermore, API provides an option for page rotation when converting to PDF. Please check GroupDocs.Conversion for .NET 18.11 [release notes](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+18.11+Release+Notes) for further reference.

# Improvements

*   Move HideWordTrackedChanges option to WordsLoadOptions class
*   HidePdfAnnotations option to PdfLoadOptions class
*   HideComments option to CellsLoadOptions, Slides CellsLoadOptions and WordsLoadOptions class

# Features

## Setting Default Font and Font Substitution Options

### When Converting OneNote Document```
const string source = "source.one";
var loadOptions = new OneLoadOptions
{
    DefaultFont = "Helvetica",
};
loadOptions.FontSubstitutes.Add(new KeyValuePair("Arial", "Helvetica"));
loadOptions.FontSubstitutes.Add(new KeyValuePair("Harriet", "Transcript"));
```

### Set default font when converting from Diagram```
const string source = "source.vsd";
var loadOptions = new DiagramLoadOptions
{
    DefaultFont = "Helvetica",
};
```

## Measure Conversion TimeMeasure conversion time and return it as a property of ConvertedDocument class```
var convertedDocument = conversionHandler.Convert(source, saveOptions);
Console.WriteLine("Elapsed time: {0}ms", convertedDocument.Elapsed);
```

## Rotation Feature

### When Converting to PDF FormatImplement rotation feature when converting to PDF```
var saveOptions = new PdfSaveOptions {
    Rotate = PdfSaveOptions.Rotation.On90
};
```

### When Converting to Image```
var saveOptions = new ImageSaveOptions {
    RotateAngle = 45
};
```

## Flatten all Form FieldsOption to flatten all form fields when converting PDF documents```
var loadOptions = new PdfLoadOptions
{
    FlattenAllFields = true
};
```

## Include Hidden Slides in Converted DocumentInclude hidden Slides in converted document when converting from Slides```
var loadOptions = new SlidesLoadOptions
{
    ShowHiddenSlides = true
};
```

## New Document Formats IntroducedGroupDocs.Conversion for .NET 18.11 implements conversion from EPS, PCL and TSV. You can also convert documents to TSV format.

# API Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [NuGet](https://www.nuget.org/packages/groupdocs.conversion) - Nuget install
*   [Documentation](https://docs.groupdocs.com/display/conversionnet/Home "Documentation") - Product Wiki
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPBhL0PgywST_NF74_4IF4k "video tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/conversion "Support forum") \- Technical Support Forum for GroupDocs.Conversion
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET "examples,plugins,showcases") - GitHub Source Code Examples

# Feedback

We always welcome you to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/conversion) and our dedicated support team will be there to respond.




