---
title: 'Convert a JPEG file to PSD programmatically in C#'
date: Tue, 26 Nov 2019 16:42:21 +0000
draft: false
url: /2019/11/26/convert-a-jpeg-file-to-psd-programmatically-in-csharp/
author: 'Atir Tahir'
summary: ''
tags: ['document conversion', 'dotnet', 'image to psd', 'jpeg to psd']
categories: ['GroupDocs.Conversion Product Family']
---

You can convert an image file (e.g. JPEG, JPG, PNG) to PSD format and redesign it as per your requirements using GroupDocs.Conversion for .NET. All you have to do is to integrate this [DLL](https://downloads.groupdocs.com/conversion/net) in your web, desktop or console application.

## Implementation

*   Pass source document path as a constructor parameter to the instance of _Converter_ class
*   Instantiate _ImageConvertOptions_
*   Specify resultant image format using _Format_ property of _ImageConvertOptions_ class
*   Declare _SavePageStream_ delegate, which should proved a stream where each document page will be stored
*   Call _Convert_ method of _Converter_ class instance and pass the declared _SavePageStream_ delegate and the instance of _ImageConvertOptions_ from the previous two steps

\[gist id="27d0573878a8342d2a30b0c9ac04a8d9" name="jpegtopsd.cs"\]

Have a look at the source JPEG file:

*   

{{< figure align=center src="images/output.png" alt="">}}

    

Below is the resultant PSD:

*   

{{< figure align=center src="images/psd-1-1024x554.jpg" alt="">}}

    

Learn more about document conversion to image format in this [article](https://docs.groupdocs.com/display/conversionnet/Convert+to+Image). You can download our open-source example [project](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET) in order to evaluate API features. In case of any issue, post it on [forum](https://forum.groupdocs.com/c/conversion).




