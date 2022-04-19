---
title: 'Watermark Password Protected Documents using C#'
date: Sat, 25 Dec 2021 07:54:23 +0000
draft: false
url: /2021/12/25/watermark-password-protected-documents-using-csharp/
aliases:
    - /2019/11/22/watermark-password-protected-documents-using-groupdocs-watermark-net-api/
author: 'Shoaib Khan'
summary: "Watermarking is one of the ways to protect your documents from illegal use; branding your files; mentioning your documents as drafts or confidential. In order to watermark your files programmatically, this article guides you on **how to add watermark to your password-protected files using C#**. We will separately look into adding text and image watermarks to the protected files."
tags: ['Document Watermarking', 'Watermark Protected Documents using CSharp', 'Watermark Protected Files using CSharp', 'watermark using csharp', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/watermark-protected-files-using-csharp.jpg" alt="Watermark Protected Docs using C#">}}


Watermarking is one of the ways to protect your documents from illegal use; branding your files; mentioning your documents as drafts or confidential. In order to watermark your files programmatically, this article guides you on **how to add watermark to your password-protected files using C#**. We will separately look into adding text and image watermarks to the protected files.

The following topics are discussed here:

*   [.NET API to Watermark Password Protected Files][1]
*   [Add Watermark to Protected Files using C#][2]
    *   [Apply Text Watermark][3]
    *   [Apply Image Watermark][4]

## .NET API to Watermark Password Protected Files {#watermarking-dotnet-api}

[GroupDocs.Watermark][5] provides a watermarking solution and showcases [.NET API that allows working with watermarks][6] within .NET applications. I will use this API to add text and image watermarks to password-protected files.

You can download the **DLLs** or **MSI** installer from the [downloads section][7] or install the API in your .NET application via [NuGet][8].

```
PM> Install-Package GroupDocs.Watermark
```

## Adding Watermark to Password-Protected Files using C# {#add-watermark-to-protected-files}

It's quite simple; just a few lines of code allow you to put a watermark in your files. Just follow the following steps for adding either type of watermark.

*   **Load** the protected document/file.
*   **Apply** text/image watermark.
*   **Save** the watermarked file.

Let's separately see how to add text watermarks, and then image watermarks.

## Add Text Watermark to Protected Files using C# {#text-watermark-to-protected-file}

Text watermarks are most used to put the company name within documents; mention the document as DRAFT or CONFIDENTIAL; or any other similar reasons. The following steps guide how to insert text watermark to password-protected files using C#.

*   Prepare the [loading option][9] using exsiting password.
*   Load the protected file using [Watermarker][10] class and **loading option**.
*   Prepare the watermark using [TextWatermark][11] class.
*   Set the watermark's text, appearance, rotation, opacity, color, and other properties.
*   Add watermark to document using [Add()][12] method.
*   Save the watermarked file using the [Save()][13] method.

The following C# code inserts a text watermark to a protected PDF document.

{{< gist GroupDocsGists 02f763046a5c3b45f722e88c0ead9029 "AddTextWatermarkToPasswordProtectedDocument.cs" >}}

## Add Image Watermark to Protected Files using C# {#image-watermark-to-protected-file}

If you want to insert your logo or some other image as a watermark, you can add it using the ImageWatermark class. The following steps allow you to add an image watermark to your password-protected documents using C#.

*   Prepare the [loading option][14] using exsiting password.
*   Load the protected file using [Watermarker][15] class and **loading option**.
*   Load the watermark image file using [ImageWatermark][16] class.
*   Set the watermark's appearance, alignment, coordinates, rotation, opacity, and other properties.
*   Add watermark to document using [Add()][17] method.
*   Save the watermarked file using the [Save()][18] method.

The following C# code inserts an image watermark to the protected MS Word DOCX document.

{{< gist GroupDocsGists 02f763046a5c3b45f722e88c0ead9029 "AddImageWatermarkToPasswordProtectedDocument.cs" >}}

## Get a Free API License

You can use the APIs for free by [getting a temporary license][19].

## Conclusion

To conclude, we learned to add text watermarks, as well as image watermarks to password-protected files within the .NET applications using C#. Further, we added a few customizations to the appearance of watermarks while adding.

Similarly, you can apply watermarks to the selective **pages of documents**, chosen **slides of the presentations**, and specific **sheets of workbooks** within your documents. See the [related articles][20] for details.

To learn more about [GroupDocs.Watermark for .NET][21], visit its [documentation][22]. For queries, contact us via the [forum][23].

## Related Articles {#releated-articles}

*   [Find and **Remove Watermarks** from Documents in C#][24]
*   [Watermark **Excel Sheets** using C#][25]
*   [Watermark **PDF** Files using C#][26]
*   [Add Watermark to **Presentation Slides** using C#][27]
*   [Add Watermark to **Images** using C#][28]







[1]: #watermarking-dotnet-api
[2]: #add-watermark-to-protected-files
[3]: #text-watermark-to-protected-file
[4]: #image-watermark-to-protected-file
[5]: https://products.groupdocs.com/watermark/
[6]: https://products.groupdocs.com/watermark/net/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://www.nuget.org/packages/groupdocs.watermark
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options/loadoptions
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options/loadoptions
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[19]: https://purchase.groupdocs.com/temporary-license
[20]: #releated-articles
[21]: https://products.groupdocs.com/watermark/net/
[22]: https://docs.groupdocs.com/watermark/
[23]: https://forum.groupdocs.com/
[24]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[25]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[26]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[27]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[28]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/

