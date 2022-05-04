---
title: "Watermark PDF Files using C#"
seoTitle: "Add Watermark to PDF using C# | Text and Image Watermarks"
description: "Add image watermarks or apply text watermarks to PDF files using C#. Either watermark all or selective pages of PDF using .NET Watermarking API."
date: Tue, 27 Jul 2021 14:34:00 +0000
draft: false
url: /2021/07/27/watermark-pdf-files-using-csharp/
author: 'Shoaib Khan'
summary: "To protect your files from any illegal use or to apply branding to your documents, watermarks can be used . In this article, you will learn to programmatically add the watermarks to PDF files using C#. We will separately looking into adding watermark text and image watermarks."
tags: ['.NET Watermarking API', 'Image Watermark in C#', 'Watermark in C#', 'Watermark PDF in C#', 'Watermark Text in C#']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermarks-to-pdf-in-csharp.jpg" alt="Apply Watermark to PDF in CSharp">}}


To protect your files from any illegal use or to apply branding to your documents, watermarks can be used. In this article, you will learn to programmatically add the watermarks to PDF files using C#. We will separately look into adding watermark text and image watermarks.

The following topics are covered below:

*   [.NET Watermarking API][1]
*   [Apply Text Watermark to PDF][2]
*   [Apply Image Watermark to PDF][3]

## .NET Watermarking API for PDF files {#dotnet-watermarking-api}

[GroupDocs.Watermark][4] provides .NET watermarking API that allows working with text as well as image watermarks within the PDF files. Along with the PDF files, the API allows adding, removing, and extraction of watermarks for word-processing documents, spreadsheets, presentations, email messages, images, Visio drawings, and many other formats. From the [documentation][5], you may further check the features and [supported file formats][6].

You can download the **DLLs** or **MSI** installer from the [downloads section][7] or install the API in your .NET application via [NuGet][8].

```
PM> Install-Package GroupDocs.Watermark
```

## Add Text Watermark to PDF using C# {#text-watermark-to-pdf}

The watermark text can be applied to PDF files on all the pages or any selective page. It can be added by inserting the formatted text on the required position.

The following steps show how to add watermark text to PDF files.

*   Load the PDF document using [Watermarker][9] class.
*   Initialize the text watermark using [TextWatermark][10] class.
*   Set the appearance by adding rotation angle, alignment, opacity, foreground and background colors, etc.
*   Set the targetted page index (_Optional_). If you do not set the index, the watermark will be applied to all pages by default.
*   Add the text watermark to the loaded PDF file.
*   Save the update file with watermark using the appropriate [Save][11] method.

The source code shows how to add text watermark to PDF files using C#.

{{< gist GroupDocsGists 0fa75a5b1203743baf225f527098c3d3 "TextWatermarkToPDF.cs" >}}

The output of the above source code shows the text watermark on both the pages of the given PDF file.



{{< figure align=center src="images/add-text-watermark-to-pdf-in-csharp-1024x646.png" alt="Add Text Watermark to PDF using C#">}}


## Add Image Watermark to PDF using C# {#image-watermark-to-pdf}

Similarly, you can add images to the PDF file as we just added the text watermark.

The following steps show how to add an image to PDF files as watermarks.

*   Load the PDF document using [Watermarker][12] class.
*   Initialize the image watermark using [ImageWatermark][13] class.
*   Set the appearance by adjusting the alignment, rotation, opacity, and other options.
*   Set the targetted page index. (Optional)
*   Add the image watermark to the PDF file.
*   Save the watermarked file using the appropriate [Save][14] method.

The source code shows how to add image watermark to PDF files using C#.

{{< gist GroupDocsGists 0fa75a5b1203743baf225f527098c3d3 "ImageWatermarkToPDF.cs" >}}

The output of the above source code shows the image watermark on the second page of the given PDF file.



{{< figure align=center src="images/add-image-watermark-to-pdf-in-csharp-1024x625.png" alt="Image Watermark to PDF using C#">}}


## Get a Free API License

You can [get a free temporary license][15] to use the API without the evaluation limitations.

## Conclusion

To conclude, you learned how to add watermarks to PDF files using C#. We have seen adding watermark text as well as images on PDF files as watermarks. For more details or learning about the API, visit [documentation][16]. For queries, contact us via the [forum][17].

## See Also

*   [Add Watermark to Images using C#][18]
*   [Add Watermark to Presentation & Slides using C#][19]
*   [Watermark Excel Sheets using C#][20]
*   [Password Protection to Lock & Unlock PDF Files in C#][21]







[1]: #dotnet-watermarking-api
[2]: #text-watermark-to-pdf
[3]: #image-watermark-to-pdf
[4]: https://docs.groupdocs.com/watermark
[5]: https://docs.groupdocs.com/watermark/net
[6]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://www.nuget.org/packages/groupdocs.watermark
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[15]: https://purchase.groupdocs.com/temporary-license
[16]: https://docs.groupdocs.com/watermark/
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[19]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[20]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[21]: https://blog.groupdocs.com/2021/11/17/password-protection-to-pdf-files-in-csharp/

