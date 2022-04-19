---
title: 'Convert Presentations to Images using C#'
date: Mon, 10 Jan 2022 04:03:00 +0000
draft: false
url: /2022/01/10/convert-presentations-to-images-using-csharp/
author: 'Shoaib Khan'
summary: 'Probably you want to use your presentation slides within web applications or you want to use its slides thumbnails. In such cases, you need to convert your PowerPoint presentation slides to images. In this article, you will learn **how to convert the PPT or PPTX presentations into JPG and PNG images** programmatically using C#.'
tags: ['Convert PPT', 'Convert PPT to JPG in CSharp', 'Convert PPT to PNG in CSharp', 'Convert PPTX', 'PPT to JPG in CSharp', 'PPT to PNG in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

Probably you want to use your presentation slides within web applications or you want to use its slides thumbnails. In such cases, you need to convert your PowerPoint presentation slides to images. In this article, you will learn **how to convert the PPT or PPTX presentations into JPG and PNG image** files programmatically using C#.



{{< figure align=center src="images/convert-ppt-to-jpg-png-image-using-dotnet.jpg" alt="Convert PPT to JPG or PNG Image using .NET">}}


The following topics are discussed here:

*   [.NET API to Convert Presentations](#ppt-convert-dotnet-api)
*   [Convert PPT/PPTX to JPG Image](#ppt-to-jpg)
*   [Convert PPT/PPTX to PNG Image](#ppt-to-png)

## .NET API to Convert Presentations {#ppt-convert-dotnet-api}

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/) showcases .NET API that allows conversion of presentation files to images within .NET applications. In this article, we will use its [GroupDocs.Conversion for .NET](https://products.groupdocs.com/conversion/net/) to convert the PPT/PPTX presentations to images formats. Additionally, the API supports the conversion of many other file formats like word-processing documents, spreadsheets, presentations, eBooks, images, and many others that are mentioned in the [documentation](https://docs.groupdocs.com/conversion/net/supported-document-formats/).

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/conversion) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.conversion).

```
PM> Install-Package GroupDocs.Conversion
```

## Convert Presentation to JPG Image using C# {#ppt-to-jpg}

Let's quickly jump to the objective and transform our presentations into image formats. The following steps show how to convert the Powerpoint PPT or PPTX to JPG image format in C#.

*   Load the presentation file using [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) class.
*   Prepare the image conversion options using [ImageConvertOptions](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions) class.
*   Define the conversion file format as JPG.
*   Convert to image using [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) method.

The following C# source code converts the PowerPoint presentation to JPG format.

{{< gist GroupDocsGists 1f2215108328c1e282d8469b1f74f29f "ConvertPptToJpg.cs" >}}

## Convert Presentation to PNG Image using C# {#ppt-to-png}

One of the most in-use image formats is PNG. Let's convert our slides into PNG in a similar way. The following steps guide how to convert the Powerpoint PPT or PPTX to PNG image format in C#.

*   Load the presentation PPT/PPTX file using [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) class.
*   Prepare the [Image Convert Options](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions).
*   Set the conversion file format as PNG.
*   Convert the presentation to image using [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) method.

The following C# code example converts the PowerPoint presentation to PNG format.

{{< gist GroupDocsGists 1f2215108328c1e282d8469b1f74f29f "ConvertPptToPng.cs" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To conclude we learned how presentations can be converted to JPG or PNG Images formats in C#. To build your own conversion application, you may learn more about the Conversion Automation .NET API using the [documentation](https://docs.groupdocs.com/conversion/net/). The best way is to experience the examples that are available on [GitHub](https://github.com/groupdocs-conversion). Contact us for any query via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Convert Presentations to PDF in C#](https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/)
*   [Excel Spreadsheets to PDF Conversion using C#](https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/)
*   [Convert JSON to CSV and CSV to JSON using C#](https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/)




