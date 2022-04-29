---
seoTitle: "Add Watermark to Images in C# | Text & Image Watermarks"
title: 'Add Watermark to Images using C#'
date: Sun, 20 Dec 2020 11:03:00 +0000
draft: false
url: /2020/12/20/add-watermark-to-images-using-csharp-dotnet/
aliases:
    - /2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
    - /2019/10/21/csharp-dotnet-api-to-add-watermark-to-images/
    - /2019/10/21/c-api-to-add-watermark-on-photos-or-images/
author: 'Shoaib Khan'
description: "C# ways to add text to image as watermark, or add image watermarks to PNG, JPG/JPEG, WebP, GIF, TIFF, BMP images using .NET Watermarking API by GroupDocs."
summary: 'Let us see today, how to add watermarks to images. This helps you branding your official photography, and protects your pictures from any unauthorized use. This article will guide you to **programmatically add text and images watermarks to your image files using C#**. In an earlier post, we have seen the same to [add text and image based watermarks to images using Java][1]. After reading this article, it will not be difficult for you to add watermarks to **JPG/JPEG, PNG, WebP, GIF, TIFF, JP2, BMP** images using C# within your .NET application.'
tags: ['add watermark in csharp', 'how to add watermark in csharp', 'watermark dotnet api', 'watermark images in csharp']
categories: ['GroupDocs.Watermark Product Family']
---

Let's see today, how to add watermarks to images. This helps you brand your official photography, and protects your pictures from any unauthorized use. This article will guide you to **programmatically add text and image watermarks to your image files using C#**. In an earlier post, we have seen the same to [add text and image-based watermarks to images using Java][2]. After reading this article, it will not be difficult for you to add watermarks to **JPG/JPEG, PNG, WebP, GIF, TIFF, JP2, BMP** images using C# within your .NET application.

Let's now separately see, how we can easily add text and image-based watermarks on your pictures, photos, or image files in C# using the [.NET Watermarking API for documents and images][3].

*   [Add Text on Images as Watermark][4]
*   [Insert Image Watermark to Images][5]

## Text and Image Watermarking API for .NET {#mce_0}



{{< figure align=center src="images/groupdocs-watermark-net.png" alt="Watermark API for .NET - GroupDocs">}}


**GroupDocs.Watermark for .NET** is an API for adding watermarks to the images or documents of different file formats within .NET applications. It provides effective watermarking methods that allow you to add text watermarks as well as image watermarks that are hard to get automatically removed by other third-party tools.

From the [documentation][6], you may further check the features and [supported file formats][7].

You can download the DLLs or MSI installer from the [downloads section][8] or get it from [NuGet][9].

```
Install-Package GroupDocs.Watermark
```

## Add Text to Images as Watermark using C# {#add-text-watermark-to-image-using-csharp}



{{< figure align=center src="images/text-watermark-on-png-using-java.png" alt="Add Text Watermark to PNG image using Java and .NET">}}


The API allows you to add text to images as a watermark with many customizations. The following steps guide how we can apply watermark on our images files, photos, or pictures using C# within the .NET application.

1.  Load the Image using [Watermarker][10].
2.  Set the watermark text and style using [TextWatermark][11].
3.  Set other watermark properties like position, rotation, opacity, etc.
4.  Add the text watermark to the image using the [Add][12] method.
5.  Save the output image with [Save][13] method.

The following C# code sample adds a text label on a JPG image as a watermark with some text rotation.

{{< gist GroupDocsGists c22738afc8956064dc9c56f62af14622 "AddTextWatermarkToJPG.cs" >}}

## Insert Image Watermark to Images using C# {#add-image-watermark-to-image-using-csharp}



{{< figure align=center src="images/image-watermark-on-jpg-image-using-java.jpg" alt="Add Image Watermark to JPG image using GroupDocs.Watermark">}}


Similarly, we can also add another image as a watermark on our source image files. For this, use **ImageWatermark** class and its properties to customize the watermark appearance.

*   Create [Watermarker][14] class object to load the source image.
*   Prepare image watermark using [ImageWatermark][15] class.
*   Set the watermark properties.
*   Add the image watermark on the source image using [Add][16] method.
*   Save the output image using [Save][17] method.

The following C# code sample adds a PNG image on another PNG file as a watermark on the preferred location.

{{< gist GroupDocsGists 0760dbd15da12362fa4e2f12cee2a073 "AddImageWatermarkToImage.cs" >}}

## Conclusion

I am confident that you can now easily add a watermark to your image files using C#. Even you can build your own .NET application that supports watermarking the documents and images of various file formats.

You can have a [Free Temporary License][18] to experience every aspect of the product. Free support will be happy to get you out of any confusion and [resolve your watermark-related queries on the forum][19].

## See Also

*   [Add Watermark to Excel Sheets using C#][20]
*   [Remove Watermark from Documents in C#][21]
*   [Add Watermark to Images in Java][22]







[1]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[3]: https://products.groupdocs.com/watermark/net
[4]: #add-text-watermark-to-image-using-csharp
[5]: #add-image-watermark-to-image-using-csharp
[6]: https://docs.groupdocs.com/watermark/net/
[7]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/watermark/net
[9]: https://www.nuget.org/packages/GroupDocs.Watermark/
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[18]: https://purchase.groupdocs.com/temporary-license
[19]: https://forum.groupdocs.com/c/watermark
[20]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[21]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[22]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/

