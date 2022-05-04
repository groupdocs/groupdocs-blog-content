---
title: "Add Watermark to Presentation Slides using C#"
seoTitle: "Add Watermark to Presentations in C# | Text and Image Watermarks"
description: "C# ways to add text to presentation slides as watermark, or apply image watermarks to PPT, PPTX, PPS & more formats using .NET Watermarking API by GroupDocs."
date: Sat, 01 May 2021 04:00:00 +0000
draft: false
url: /2021/05/01/add-watermark-to-presentations-using-csharp/
author: 'Shoaib Khan'
summary: "Watermarks are normally used to protect the documents from any unauthorized use. To protect your presentations and to claim ownership, today we will learn how to programmatically add text and image watermarks to the Microsoft PowerPoint presentations within .NET applications using C#. In a separate article, we have seen [applying watermarks to images in C#][1]."
tags: ['add watermark in csharp', 'add watermark to presentations in csharp', 'how to add watermark in csharp']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-presentations-in-csharp.jpg" alt="Apply Watermark to Presentation in C#">}}


Watermarks are normally used to protect the documents from any unauthorized use. To protect your presentations and to claim ownership, today we will learn how to programmatically add text and image watermarks to the Microsoft PowerPoint presentations within .NET applications using C#. In a separate article, we have seen [applying watermarks to images in C#][3].

Let's quickly move to separately learn, how we can apply text and image-based watermarks to the whole presentation or specific slide using the [watermarking API for .NET applications][4].

*   [Add text watermarks to presentation slides][5].
*   [Add image watermarks to presentation slides.][6]

## Watermarking API for .NET

[GroupDocs.Watermark for .NET][7] is a watermarking API that allows adding text and image watermarks to the presentations and many other documents of different file formats within .NET applications. It provides watermarking methods that add watermarks that are hard to get automatically removed by other tools.

Along with the presentations, the API supports adding, removing, and extracting watermarks from word-processing documents, spreadsheets, email messages, PDF files, images, Visio drawings, and many other formats. Among presentation file formats, it supports PPT, PPTX, PPS, PPTM, PPSX, and others. From the [documentation][8], you may further check the features and [supported file formats][9].

You can download the DLLs or MSI installer from the [downloads section][10] or get it from [NuGet][11].

```
Install-Package GroupDocs.Watermark
```

## Add Text to Slides as Watermark using C# {#text-watermark-to-slides-in-csharp}

The API provides customizations to add text to presentations as watermark. The following steps guide you how to apply watermark on presentation files within .NET application.

*   Load the presentation using [Watermarker][12].
*   Set watermark text and style using [TextWatermark][13].
*   Set other properties like rotation, size, opacity, color, and position.
*   Provide the index of the slide to apply the watermark.
*   Add the formatted text watermark using [Add][14] method.
*   Save the watermarked presentation using the [Save][15] method.

The following code sample adds a text label to the PPTX presentation as a watermark on the first slide with rotation using C#.

{{< gist GroupDocsGists c5637a7b8dd5d881e58e502c109ca4a0 "AddTextWatermarkToPresentation.cs" >}}

If you do not provide a slide index, the watermark will be added on all the slides by default. The above code shows how to mention the slide index, however, I have shown you the output with a text watermark on all the slides of the PPTX presentation.



{{< figure align=center src="images/text-watermark-to-slide.png" alt="Text Watermark to Presentation Slide">}}


## Insert Image Watermark to Slides using C# {#image-watermark-to-slides-in-csharp}

Likewise, you can add images on presentation files as watermark. You just have to use the [ImageWatermark][16] class instead of the TextWatermark. The following are the steps to add image watermark to presentation slides within your .NET applications.

*   Load the presentation using [Watermarker][17].
*   Load the image file that will be used as a watermark using [ImageWatermark][18].
*   Set image watermark properties like rotation, size, opacity, color, and position.
*   Set the slide index on which to apply the watermark.
*   Add the image watermark to the presentation using [Add][19] method.
*   Save the watermarked presentation using the [Save][20] method.

The following code sample adds an image to the PPTX presentation as a watermark on the second slide using C#.

{{< gist GroupDocsGists c5637a7b8dd5d881e58e502c109ca4a0 "AddImageWatermarkToPresentation.cs" >}}

The following is the output of the above code with an image watermark only on the second slide of the PPTX presentation.



{{< figure align=center src="images/image-watermark-to-slide.jpg" alt="Image Watermark to Presentation Slide">}}


## Conclusion

To sum up, you have learned how to add text and image watermarks to your presentation slides using C#. Now you can build your own .NET application that supports text as well as image watermarks for the presentation files and specific slides of the presentation. Consult the documentation to [apply watermarks to various other document formats][21].

You can have a [Free Temporary License][22] to experience every aspect of the product. Free support will be happy to get you out of any confusion and [resolve your queries related to watermarks on the forum][23].

## See Also

*   [Add Watermark to Images using C#][24]
*   [Insert Watermark to Excel Workbooks using C#][25]
*   [Find and Remove Watermarks from Documents in C#][26]







[1]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[2]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[3]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[4]: https://products.groupdocs.com/watermark/net
[5]: #text-watermark-to-slides-in-csharp
[6]: #image-watermark-to-slides-in-csharp
[7]: https://products.groupdocs.com/watermark/net
[8]: https://docs.groupdocs.com/watermark/net/
[9]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[10]: https://downloads.groupdocs.com/watermark/net
[11]: https://www.nuget.org/packages/GroupDocs.Watermark/
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[19]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[20]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[21]: https://docs.groupdocs.com/watermark/net/adding-watermarks/
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://forum.groupdocs.com/c/watermark
[24]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[25]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[26]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/

