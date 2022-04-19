---
title: "在 C# 中将图像转换为 PDF"
date: Wed, 19 May 2021 13:43:15 +0000
draft: false
url: /zh/2021/05/19/convert-images-to-pdf-in-csharp/
aliases:
- /2020/04/27/convert-an-image-to-pdf-in-csharp/
- /2019/11/12/convert-to-pdf-using-groupdocs.conversion-for-.net-and-java/
- /2019/11/12/convert-an-image-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "An Image can be converted to PDF to assure that the image will display correctly across devices without being altered. PDF images are ideal for printing and for storing images online when intended to be downloaded. PDF can hold as many images in one document so can be printed easily or saved as a catalog. This article will guide you to programmatically convert images like JPG, GIF, WebP, PNG to PDF in C# using .NET API for document and image conversion."
tags: ['Convert Images to PDF in CSharp', 'Convert JPG to PDF in CSharp', 'CSharp Image Conversion', 'JPG to PDF in CSharp', 'PNG to PDF in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

可以将图像转换为 PDF 以确保图像在设备之间正确显示而不会被更改。 PDF 图像非常适合打印和在线存储要下载的图像。 PDF 可以在一个文档中包含尽可能多的图像，因此可以轻松打印或保存为目录。本文将指导您使用 .NET API 以编程方式将 JPG、GIF、WebP、PNG 等图像转换为 C# 中的 PDF，以进行文档和图像转换。

以下主题简要介绍如下：

* [图像转换.NET API][2]
* [将JPG图像转换为PDF][3]
* [将PNG、GIF、BMP图像转换为PDF][4]
* [带有高级选项的图像到 PDF 转换][5]

## 用于图像转换的 .NET API {#image-conversion-dotnet-api}

我将使用 [GroupDocs.Conversion for .NET][6] 库将图像转换为 PDF 格式。该库允许我们将一长串图像格式转换为 PDF。这里提到了一些受支持的。如需完整列表，请访问 [文档][7]。



{{< figure align=center src="images/convert-images-to-pdf-in-dotnet.jpg" alt="使用 CSharp 将图像转换为 PDF">}}


* 人工智能
* BMP
* CDR
* DJVU
* 动图
* ICO
* JPEG、JPG、JP2
* PNG
* SVGZ
* TGA
* TIF, TIFF
* WEBP

除了图像，API 还允许开发人员转换 Word 文档、电子表格、演示文稿、电子书、Visio 文档、Microsoft Project 文件、PSD 文件、PDL、电子邮件信息等等。 [GitHub][8] 上提供了许多示例来获得上述支持。

您可以从 [下载部分][9] 下载 DLL 或 MSI 安装程序，或从 [NuGet][10] 获取。

```
Install-Package GroupDocs.Conversion
```

## 在 C# 中将 JPG 转换为 PDF {#jpg-to-pdf}



{{< figure align=center src="images/Sample.jpg" alt="JPEG图像">}}


要将您的 JPG 图像简单地转换为 PDF 格式，您可以按照以下步骤操作：

* 使用 [Converter][11] 类加载 JPG 文件。
* 实例化 [PdfConvertOptions][12] 类。
* 调用 [Convert][13] 方法将 JPG 图片转换为 PDF 并保存在提供的路径上。

以下源代码显示了如何在 C# 中将 JPG 图像转换为 PDF。

```
// 在 C# 中将 JPG 图像转换为 PDF
using (Converter converter = new Converter("image.jpg"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("imageToPdf.pdf", options);
}
```

## 在 C# 中将 PNG 图像转换为 PDF {#png-gif-bmp-to-pdf}

如果要转换 PNG 图像，则代码没有区别。以下步骤允许我们使用 C# 将 PNG 图像转换为 PDF。

* 使用 [Converter][14] 类加载 PNG 图像文件。
* 实例化 [PdfConvertOptions][15] 类。
* 调用 [Convert][16] 方法将提供的图片转换为 PDF 并保存在提供的路径上。

以下代码展示了如何使用 C# 将 PNG 图像转换为 PDF。

```
// 在 C# 中将任何图像转换为 PDF。 PNG、WebP、JPG、GIF、TGA 等等...
using (Converter converter = new Converter("image.png"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("imageToPdf.pdf", options);
}
```

## 将任何图像转换为 PDF

同样，您只需在加载时向 **Converter** 类提供 JPG、PNG、GIF、WebP 或任何其他图像。此外，在转换为 PDF 格式时，还有许多 [转换选项][17]。

## 使用高级选项在 C# 中将图像转换为 PDF {#advance-conversion}



{{< figure align=center src="images/AdvancedConversion-300x238.jpg" alt="转换后的输出文档">}}


GroupDocs.Conversion 提供 [PdfConvertOptions][18] 让我们在将 Image 转换为 PDF 时控制转换结果。一些附加选项是：

* [宽度][19] - 转换后的图像宽度。
* [高度][20] - 转换后的图像高度。
* [MarginTop][21] - 转换后的页面上边距。
* [MarginBottom][22] - 转换后的页面底部边距。
* [MarginLeft][23] - 转换后的页面左边距。
* [MarginRight][24] - 转换后的页面右边距。
* [旋转][25] - 页面旋转。可用选项有：无、On90、On180、On270

以下 C# 代码示例使用这些附加选项并将图像转换为 PDF。它设置生成图像的高度和宽度，设置页边距，并将图像旋转 180 度。

```
// 在 C# 中将 JPG、PNG 或其他图像转换为 PDF。调整大小、设置边距或旋转图像。
using (Converter converter = new Converter("image.jpg"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        Width = 233,
        Height = 175,
        MarginTop = 20,
        MarginBottom = 20,
        MarginLeft = 20,
        MarginRight = 20,
        Rotate = Rotation.On180
    };
    converter.Convert("imageToPdfAdv.pdf", options);
}
```

## 获取免费 API 许可证

您可以通过申请 [免费临时许可证][26] 来使用该 API，而不受评估限制。

## 结论

最后，我们学习了使用 .NET 的图像转换 API 将图像转换为 PDF 格式。具体来说，我们讨论了如何在 C# 中以编程方式将 JPG、PNG、WebP 和其他图像转换为 PDF。您可以使用 [文档][27] 探索有关图像转换 API 的更多信息。如需查询，请通过 [论坛][28] 联系我们。

## 也可以看看

* [在 C# 中将 Excel 电子表格转换为 PDF][29]
* [在 C# 中将 CAD 绘图转换为 PDF][30]
* [](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)[在 C# 中将 EML 或 MSG 文件转换为 PDF][31]







[1]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[2]: #image-conversion-dotnet-api
[3]: #jpg-to-pdf
[4]: #png-gif-bmp-to-pdf
[5]: #advance-conversion
[6]: https://products.groupdocs.com/conversion/net
[7]: https://docs.groupdocs.com/conversion/net/supported-document-formats/#SupportedDocumentFormats-ConversionfromImageFiletoOtherDocumentformats
[8]: https://github.com/groupdocs-conversion
[9]: https://downloads.groupdocs.com/conversion/net
[10]: https://www.nuget.org/packages/GroupDocs.Conversion/
[11]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[15]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[16]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[17]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[18]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[19]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/width
[20]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/height
[21]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/margintop
[22]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginbottom
[23]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginleft
[24]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginright
[25]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/rotate
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/conversion
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[30]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[31]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/


