---
title: 'Implement Page Rotation when Converting to PDF'
date: Fri, 12 Apr 2019 14:34:18 +0000
draft: false
url: /2019/04/12/implement-page-rotation-when-converting-to-pdf/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for Java', 'GroupDocs.Conversion Product Family']
---

Its time to augment your document conversion experience. You will be pleased to hear the new features, improvements and bug fixes that we'r going to elaborate in this blog post. Did you ever think of converting and rotating a document at the same time? We make your wish come true with this month's release of GroupDocs.Conversion for Java [19.4](https://docs.groupdocs.com/display/conversionjava/GroupDocs.Conversion+for+Java+19.4+Release+Notes).  
You can now set page rotation angle when converting to a PDF or Image format. And it only takes a single line of code.

We implemented following new properties:  

*   _setRotate(PdfSaveOptions.Rotation.On90)_
*   _setRotateAngle(45)_

### Rotation Feature when Converting to Image Format

We enriched _ImageSaveOptions_ class with a new property that takes rotation angle value as parameter.

{{< gist GroupDocsGists 11ac65019418c67b8f05ca037d70bcb3 "Examples-GroupDocs.Conversion.Examples.Java-src-main-java-com-groupdocs-conversion-examples-Conversion-rotatePagesWhenConvertingToImage.java" >}}

### Rotation when Converting to PDF

_PdfSaveOptions_ class covers a new property that takes PdfSaveOptions.Rotation enumeration.

{{< gist GroupDocsGists 3d404d88c825a328adfc6c2782a00e37 "Examples-GroupDocs.Conversion.Examples.Java-src-main-java-com-groupdocs-conversion-examples-Conversion-rotatePagesWhenConvertingToPDF.java" >}}

### More File Formats and Font Substitution Options

Some new document formats are also introduced. Like you can do conversion from **EPS**, **TSV**, **PCL**. API also permits to set default font and font substitution option when converting from .one file.

### Measure Conversion Time

Can we measure or track time for a document conversion? You might be thinking of such a feature. Because its appealing. Therefore, we've introduced this in current release. Let's have a look at its implementation.

{{< gist GroupDocsGists a76fa663bdceb0408649f6a143ea0def "Examples-GroupDocs.Conversion.Examples.Java-src-main-java-com-groupdocs-conversion-examples-Conversion-measureConversionTime.java" >}}

### Include Hidden Slides in Converted Document

Yes, this is absolutely right. We've implemented a property _setShowHiddenSlides_ using that you can decide either to convert or skip hidden slides when converting a Slide document.

{{< gist GroupDocsGists 79372ea51728e838525519411556375d "Examples-GroupDocs.Conversion.Examples.Java-src-main-java-com-groupdocs-conversion-examples-Conversion-includeHiddenSlidesInConvertedDocument.java" >}}

## Improvements

We always introduce improvements for better usability. This release covers following improvements.

*   _HideWordTrackedChanges_ option to _WordsLoadOptions_ class
*   _HidePdfAnnotations_ option to _PdfLoadOptions_ class
*   _HideComments_ option to _CellsLoadOptions_, _SlidesLoadOptions_ and _WordsLoadOptions_ class

## Bug Fixes

We listen your feedback carefully and make sure to fix the disruptions that you face. Spreadsheets are one of the best way to represent data. Most of the time you add graphs in it. Previously, API was not converting spreadsheets with graphs properly. It was not showing complete data. However, this issue is now fixed.

### Width and Height not Working

Furthermore, there was no impact of width and height in the output that you set in _ImageSaveOptions_. This issue is also now resolved.

### Will we get PasswordProtectedException?

Yes, we fixed obfuscation config for com.groupdocs.conversion.exceptions package. You will now get proper exception on processing a password protected document without applying password. Eventually, this exception could be then handled.

To learn more about API integration and usage check out the docs [here](https://docs.groupdocs.com/display/conversionjava/Home). To see the implementation and functionalities, check out the GitHub [repository](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java).




