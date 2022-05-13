---
title: "使用 C# 为 PDF 文件添加水印"
date: Tue, 27 Jul 2021 14:34:00 +0000
draft: false
url: /zh/2021/07/27/watermark-pdf-files-using-csharp/
author: 'Shoaib Khan'
summary: "为了保护您的文件免遭任何非法使用或为您的文档应用品牌，可以使用水印。在本文中，您将学习使用 C# 以编程方式将水印添加到 PDF 文件。我们将分别研究添加水印文本和图像水印。"
tags: ['dotNET Watermarking API', 'Image Watermark in C#', 'Watermark in C#', 'Watermark PDF in C#', 'Watermark Text in C#']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermarks-to-pdf-in-csharp.jpg" alt="在 CSharp 中将水印应用于 PDF">}}


为了保护您的文件免受任何非法使用或将品牌应用于您的文档，可以使用水印。在本文中，您将学习使用 C# 以编程方式将水印添加到 PDF 文件。我们将分别研究添加水印文本和图像水印。

以下主题涵盖以下内容：

* [.NET 水印 API][1]
* [将文本水印应用于 PDF][2]
* [将图像水印应用于 PDF][3]

## PDF 文件的 .NET 水印 API {#dotnet-watermarking-api}

[GroupDocs.Watermark][4] 提供 .NET 水印 API，允许处理 PDF 文件中的文本和图像水印。除了 PDF 文件，API 还允许为文字处理文档、电子表格、演示文稿、电子邮件、图像、Visio 绘图和许多其他格式添加、删除和提取水印。从[文档][5]，您可以进一步检查功能和[支持的文件格式][6]。

您可以从 [下载部分][7] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Watermark
```

## 使用 C# 将文本水印添加到 PDF {#text-watermark-to-pdf}

水印文本可以应用于所有页面或任何选择性页面上的 PDF 文件。可以通过在所需位置插入格式化文本来添加它。

以下步骤显示如何将水印文本添加到 PDF 文件。

* 使用 [Watermarker][9] 类加载 PDF 文档。
* 使用 [TextWatermark][10] 类初始化文本水印。
* 通过添加旋转角度、对齐方式、不透明度、前景色和背景色等设置外观。
* 设置目标页面索引（_Optional_）。如果不设置索引，水印会默认应用到所有页面。
* 将文本水印添加到加载的 PDF 文件中。
* 使用适当的[保存][11]方法保存带有水印的更新文件。

源代码展示了如何使用 C# 向 PDF 文件添加文本水印。

```
// 使用 C# 将水印文本添加到 PDF 文件的页面
PdfLoadOptions loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions))
{
    TextWatermark textWatermark = new TextWatermark("Watermark", new Font("Arial", 80))
    {
        RotateAngle = -45,
        Opacity = .3,
        ForegroundColor = Color.DarkBlue,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center
    };
    // If you want to add watermark text to any specific page, provde Page Index.
    /*
    PdfArtifactWatermarkOptions textWatermarkOptions = new PdfArtifactWatermarkOptions();
    textWatermarkOptions.PageIndex = 0;
    */
    watermarker.Add(textWatermark, textWatermarkOptions);
    watermarker.Save("path/text-watermark.pdf");
}
```

上述源代码的输出在给定 PDF 文件的两个页面上都显示了文本水印。



{{< figure align=center src="images/add-text-watermark-to-pdf-in-csharp-1024x646.png" alt="使用 C# 将文本水印添加到 PDF">}}


## 使用 C# 将图像水印添加到 PDF {#image-watermark-to-pdf}

同样，您可以将图像添加到 PDF 文件中，就像我们刚刚添加了文本水印一样。

以下步骤显示了如何将图像作为水印添加到 PDF 文件中。

* 使用 [Watermarker][12] 类加载 PDF 文档。
* 使用 [ImageWatermark][13] 类初始化图像水印。
* 通过调整对齐、旋转、不透明度和其他选项来设置外观。
* 设置目标页面索引。 （选修的）
* 将图像水印添加到 PDF 文件中。
* 使用适当的[保存][14]方法保存带水印的文件。

源代码展示了如何使用 C# 为 PDF 文件添加图像水印。

```
// 使用 C# 将水印图像添加到 PDF 文件的页面 
PdfLoadOptions loadOptions = new PdfLoadOptions();
using (Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions))
{
    ImageWatermark imageWatermark = new ImageWatermark("watermark-logo.png")
    {
        Opacity = 0.7,
        X = 70,
        Y = 350
    };
    // Adding image watermark to the second page  
    PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
    imageWatermarkOptions.PageIndex = 1;
    watermarker.Add(imageWatermark, imageWatermarkOptions);

    watermarker.Save("path/image-watermark.pdf");
}
```

上述源代码的输出显示了给定 PDF 文件第二页上的图像水印。



{{< figure align=center src="images/add-image-watermark-to-pdf-in-csharp-1024x625.png" alt="使用 C# 将图像水印转换为 PDF">}}


## 获取免费 API 许可证

您可以[获得免费的临时许可证][15] 使用 API，而不受评估限制。

## 结论

最后，您学习了如何使用 C# 向 PDF 文件添加水印。我们已经看到在 PDF 文件上添加水印文本和图像作为水印。有关 API 的更多详细信息或了解，请访问 [文档][16]。如有疑问，请通过 [论坛][17] 联系我们。

## 也可以看看

* [使用 C# 为图像添加水印][18]
* [使用 C# 为演示文稿和幻灯片添加水印][19]
* [使用 C# 给 Excel 表格加水印][20]
* [使用 C# 锁定和解锁 PDF 文件的密码保护][21]







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


