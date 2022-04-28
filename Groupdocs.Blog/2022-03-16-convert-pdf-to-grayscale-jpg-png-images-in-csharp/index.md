---
title: 'Convert PDF to Grayscale using C#'
seoTitle: "Convert PDF to Grayscale JPG & PNG Images using C#"
description: "Transform PDF documents to grayscale JPG or PNG images in C#. Apply gamma, manage contrast or control brightness within .NET application."
date: Wed, 16 Mar 2022 12:05:00 +0000
draft: false
url: /2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/
aliases:
    - /2019/10/30/convert-documents-to-grayscale-image-with-contrast-in-csharp/
    - /2019/10/30/convert-document-to-image-with-contrast-in-csharp/
author: 'Shoaib Khan'
summary: 'The first and foremost question in your mind could be, is it about converting an RGB image to Grayscale only? No, you can convert almost any document format (including images) to a black-and-white or grayscale monochrome image. The contrast ranges from black at the weakest intensity to white at the strongest. In this article, we will discuss **how to convert color PDF document to a grayscale JPG and PNG image formats using C#**.'
tags: ['convert to grayscale', 'Convert to Grayscale in CSharp', 'document to image', 'PDF to Grayscale', 'PDF to Grayscale in CSharp', 'PDF to JPG Grayscale', 'PDF to PNG Grayscale']
categories: ['GroupDocs.Conversion Product Family']
---

The first and foremost question in your mind could be, is it about converting an RGB image to Grayscale only? No, you can convert almost any document format (including images) to a black-and-white or grayscale monochrome image. The contrast ranges from black at the weakest intensity to white at the strongest. In this article, we will discuss how to convert color PDF documents to **grayscale JPG and PNG image formats using C#**.



{{< figure align=center src="images/Converted-Colored-PDF-to-Grayscale-1024x577.jpg" alt="Converted PDF to Grayscale">}}


This feature is quite helpful if you are going to do image processing. As RGB image is represented by 3 channels and contains a lot of data/noise, hence, more computational power is required to process such an image. On the other hand, a grayscale image makes this process comparatively easy.

## .NET API to Convert Documents into Grayscale

[GroupDocs.Conversion for .NET](https://products.groupdocs.com/conversion/net/) is an API that is used for documents conversion between a multitude of [supported file formats and image types](https://docs.groupdocs.com/conversion/net/supported-document-formats/). Conversion results can easily be customized and tuned with multiple flexible options. I will use this API to convert PDF documents to grayscale JPG and PNG images.

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/conversion) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.conversion).

```
PM> Install-Package GroupDocs.Conversion
```

  
If we talk about its implementation, it is a back-end API that can be integrated or implemented within any .NET application without any dependency. For more information about its API, visit its [documentation](https://docs.groupdocs.com/conversion/net/).

## Convert PDF to Grayscale JPG Image using C#

Let’s quickly achieve the target by transforming the color PDF document to black and white image formats. The following steps show how to convert the PDF to grayscale JPG using C#.

*   Load the PDF document using [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) class.
*   Prepare the [image conversion options](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
*   Set the conversion file format as JPG.
*   Set the grayscale option to true.
*   Convert to image using [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) method.

The following C# source code converts the PDF document to a grayscale JPG image.

{{< gist GroupDocsGists 3e3c9f756ece5d6f94f90603ec2798bd "PdfToJpgGrayscale.cs" >}}

Additionally, there are many other options to control the height, width, horizontal and vertical flip, and document rotations. You can also apply the watermarks with different settings to the output image.

## Convert PDF to Grayscale PNG Image using C#

Similarly, the color PDF document can be converted to other image formats in grayscale. The following steps show how to convert the PDF to grayscale PNG using C#.

*   Load the PDF document using [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) class.
*   Prepare the [image conversion options](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
*   Set the conversion file format as PNG.
*   Set the grayscale option to true.
*   Convert to PNG image using [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) method.

The following C# source code converts the PDF document to a grayscale PNG image.

{{< gist GroupDocsGists 3e3c9f756ece5d6f94f90603ec2798bd "PdfToPngGrayscale.cs" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To conclude we learned how PDF documents can be converted to JPG or PNG Images formats in C#. To build your own conversion application, you may learn more about the low code and high code Conversion Automation .NET APIs from the [documentation](https://docs.groupdocs.com/conversion/net/).

The best way is to experience the examples that are available on [GitHub](https://github.com/groupdocs-conversion). Contact us for any query via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Convert Images to PDF in C#](https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/)
*   [Transform Presentations to Images using C#](https://blog.groupdocs.com/2022/01/10/convert-presentations-to-images-using-csharp/)
*   [Convert WebP Images to JPG, PNG, TIFF, and PDF in C#](https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/)




