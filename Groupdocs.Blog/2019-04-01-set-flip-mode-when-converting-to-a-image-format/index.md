---
title: 'Set Flip Mode when Converting to a Image Format'
date: Mon, 01 Apr 2019 12:00:22 +0000
draft: false
url: /2019/04/01/set-flip-mode-when-converting-to-a-image-format/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

With our latest release of GroupDocs.Convesion for .NET [19.3](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+19.3+Release+Notes), some new properties are introduced in **ImageSaveOptions** class. When converting to a Image format you can now always set brightness and contrast. API permits you to do mirror-reversal across a horizontal/vertical axis using FlipMode property. Based on your feedback, we resolved some previously logged issues and improved document conversion experience. Such as, image quality is improved when converting to a **WebP** format. Furthermore, **JpegQuality** issue is now resolved for PDF to JPEG conversion.

## New Properties in ImageSaveOptions

FlipMode offers horizontal, vertical, horizontal and vertical at the same time or no Flip at all. Control gamma correction, brightness and contrast when converting to a image format.

{{< gist GroupDocsGists 84c57a1baba85299495b2e28cc2915c0 "Examples-CSharp-GroupDocs.Conversion.Examples.CSharp-Conversion-ConvertToImageWithExtendedOption.cs" >}}

## Fix - ImageSaveOptions.JpegQuality Issue

You can select desired image quality when converting to JPEG format. Quality scale must be between 0 and 100. Previously, despite of setting **JpegQuality** to any value (0-100), API was not reflecting any change in the output. This issue is now fixed.

GroupDocs.Conversion for .NET 19.3 is now available to [download](http://nuget.org/packages/GroupDocs.Conversion). Let us know what you think by sending [feedback](https://forum.groupdocs.com/c/conversion)!




