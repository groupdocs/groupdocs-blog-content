---
seoTitle: "Extract Images from PDF, Excel, PPT, Word Documents in C#"
title: 'Extract Images from Documents using C#'
date: Wed, 28 Oct 2020 18:27:00 +0000
draft: false
url: /2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
author: 'Shoaib Khan'
description: ".NET API with features to extract images from PDF, spreadsheets, presentations, word-processing documents, and from specific pages using parsing API in C#."
summary: 'In this article, we will be learning to **programmatically extract images from PDF, Excel, PowerPoint, and Word documents in a C#** application using document parsing .NET API. [GroupDocs.Parser for .NET][1] is document parsing and data extraction .NET API. It supports **document parsing** and **extraction of images, text,** and **metadata** from **word-processing documents**, **spreadsheets**, **presentations, archives,** and **email** documents.'
tags: ['csharp parser', 'Dcoument Parsing API', 'extract images from PDF in csharp', 'extract images in csharp', 'Image extractor']
categories: ['GroupDocs.Parser Product Family']
---

In the [previous post][2], we discussed how to extract images from documents in Java. Today, we will be looking to achieve the same objective using C#. No worries if you have not visited the last post. In this article, we will be learning to **programmatically extract images from PDF, Excel, PowerPoint, and Word documents in a C#** application using document parsing .NET API.

{{< figure align=center src="images/extract-images-from-documents-in-csharp-dotnet.png" alt="Extract Images from Documents in .NET">}}

Following topics will be covered here:

*   [Image, Text, and Metadata Extraction .NET API][3]
*   [Image Extraction from PDF documents][4]
*   [Extract Images from Word, Excel, PowerPoint documents][5]
*   [Extract Image from Specific Page][6]
*   [Supported Formats for Image Extraction][7]

## Image, Text, and Metadata Extraction .NET API {#image-extraction-dotnet-api}

{{< figure align=center src="images/groupdocs-parser-net.png" alt="Parse Documents and Extract Data in .NET">}}


[GroupDocs.Parser for .NET][8] is document parsing and data extraction .NET API. It supports **document parsing** and **extraction of images, text,** and **metadata** from **word-processing documents**, **spreadsheets**, **presentations, archives,** and **email** documents. At the end of the article, document formats are [mentioned][9] that are supported by the API for image extraction.

In this article, we will use this API, so I would recommend to [download][10] its binaries or install the API from [NuGet][11] to prepare the environment.

## Extract Images from PDF Documents in C# {#extract-images-from-pdf-in-csharp}



{{< figure align=center src="images/PDF-with-Images.png" alt="PDF Document to Extract Images">}}


You can easily retrieve all the images from any PDF document by following these simple steps.

1.  Instantiate the [Parser][12] class object with the source document.
2.  Call [GetImages][13] method of **Parser** class to get the collection of all the images in [PageImageArea][14] objects.
3.  Iterate over **PageImageArea** to get every image.
4.  Save images on the disk using the [Save][15] method of **PageImageArea**.

Extracted images can be saved in **BMP**, **GIF**, **JPEG**, **PNG**, and **WebP** formats. The complete code is shown below to demonstrate the whole steps.

{{< gist GroupDocsGists 3bc831b64a139c428dffdb138332128a "ExtractImagesFromDocument.cs" >}}



{{< figure align=center src="images/Extracted-Images-from-PDF-using-GroupDocs.Parser-for-Java.png" alt="Extracted Images from Document using GroupDocs.Parser">}}


## Extract Images from Word, Excel, PowerPoint Files in C# {#extract-images-from-word-excel-ppt-in-csharp}

Not restricted to just PDF format, we can take out all the images from word-processing documents, spreadsheets, presentations, with the unchanged code base. Just change the source document path with the file extension, your document will be parsed to extract and save all the images to the disk.

```
using (Parser parser = new Parser("path/document.docx")) // Word Document
// using (Parser parser = new Parser("path/document.xlsx")) // Excel Spreadhseet
// using (Parser parser = new Parser("path/document.pptx")) // Presentation
// using (Parser parser = new Parser("path/document.pdf")) // PDF Document
```

## Image Extraction from Specific Document Page in C# {#extract-images-from-specific-page-in-csharp}

If you want to extract images from a specific page of the document, it can be done easily using the below-mentioned steps and C# code.

*   Get the information about the document using the [GetDocumentInfo][16] method.
*   From the document information, take out the total [PageCount][17] and other information.
*   Use [GetImages(pageIndex)][18] method and pass your target page index to it.
*   To save the retrieved images, traverse the images collection, and save the individual image using the [Save][19] method.

{{< gist GroupDocsGists 3bc831b64a139c428dffdb138332128a "ExtractImagesFromDocumentPage.cs" >}}

## Supported Formats for Image Extraction in C# {#supported-formats-for-image-extraction}

Following are the document formats that are supported by the _GroupDocs.Parser for .NET_ API for image extraction.

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Word Processing Documents</strong></td><td>DOC, DOCX, DOCM, DOT, DOTX, DOTM, ODT, OTT, RTF</td></tr><tr><td><strong>Spreadsheets</strong></td><td>XLS, XLSX, XLSM, XLSB, XLT, XLTX, XLTM, ODS, OTS, XLA, XLAM, NUMBERS</td></tr><tr><td><strong>Presentations</strong></td><td>PPT, PPTX, PPTM, PPS, PPSX, PPSM, POT, POTX, POTM, ODP, OTP</td></tr><tr><td><strong>Portable Documents</strong></td><td>PDF</td></tr><tr><td><strong>Emails</strong></td><td>EML, EMLX, MSG</td></tr><tr><td><strong>Archives**</td><td>ZIP</td></tr></tbody></table></figure>

## More about GroupDocs.Parser

*   [Documentation][20]
*   [Source Code Examples][21]
*   [API Reference][22]
*   Family ([On-Premise APIs][23]| [Cloud APIs][24] | [Free Online App][25]

Let's talk some more @ [Free Support Forum][26]

## Related Articles

*   [Extract Images from Documents using Java][27]
*   [Extract Images from Documents on the Cloud using Python][28]







[1]: https://products.groupdocs.com/parser/net
[2]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[3]: #image-extraction-dotnet-api
[4]: #extract-images-from-pdf-in-csharp
[5]: #extract-images-from-word-excel-ppt-in-csharp
[6]: #extract-images-from-specific-page-in-csharp
[7]: #supported-formats-for-image-extraction
[8]: https://products.groupdocs.com/parser/net
[9]: #supported-formats-for-image-extraction
[10]: https://downloads.groupdocs.com/parser/net
[11]: https://www.nuget.org/packages/GroupDocs.Parser/
[12]: https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser
[13]: https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser/methods/getimages
[14]: https://apireference.groupdocs.com/net/parser/groupdocs.parser.data/pageimagearea
[15]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data.pageimagearea/save/methods/1
[16]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getdocumentinfo
[17]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/idocumentinfo/properties/pagecount
[18]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.parser/getimages/methods/2
[19]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data.pageimagearea/save/methods/1
[20]: https://docs.groupdocs.com/parser/
[21]: https://github.com/groupdocs-parser/
[22]: https://apireference.groupdocs.com/parser
[23]: https://products.groupdocs.com/parser/family
[24]: https://products.groupdocs.cloud/parser/family
[25]: https://products.groupdocs.app/parser)
[26]: https://forum.groupdocs.com/c/parser
[27]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[28]: https://blog.groupdocs.cloud/2020/10/25/extract-images-from-word-excel-ppt-pdf-using-python/

