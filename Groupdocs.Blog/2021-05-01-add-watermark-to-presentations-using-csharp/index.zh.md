---
title: "使用 C# 将水印添加到演示文稿幻灯片"
date: Sat, 01 May 2021 04:00:00 +0000
draft: false
url: /zh/2021/05/01/add-watermark-to-presentations-using-csharp/
author: 'Shoaib Khan'
summary: "Watermarks are normally used to protect the documents from any unauthorized use. To protect your presentations and to claim ownership, today we will learn how to programmatically add text and image watermarks to the Microsoft PowerPoint presentations within .NET applications using C#. In a separate article, we have seen [applying watermarks to images in C#][1]."
tags: ['add watermark in csharp', 'add watermark to presentations in csharp', 'how to add watermark in csharp']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-presentations-in-csharp.jpg" alt="在 C# 中将水印应用于演示文稿">}}


水印通常用于保护文档免受任何未经授权的使用。为了保护您的演示文稿并声明所有权，今天我们将学习如何使用 C# 以编程方式将文本和图像水印添加到 .NET 应用程序中的 Microsoft PowerPoint 演示文稿中。在另一篇文章中，我们看到了[在 C# 中对图像应用水印][3]。

让我们快速开始单独学习，我们如何使用 [用于 .NET 应用程序的水印 API][4] 将基于文本和图像的水印应用于整个演示文稿或特定幻灯片。

* [为演示幻灯片添加文本水印][5]。
* [为演示幻灯片添加图像水印。][6]

## .NET 水印 API

[GroupDocs.Watermark for .NET][7] 是一个水印 API，允许在 .NET 应用程序中向演示文稿和许多其他不同文件格式的文档添加文本和图像水印。它提供了水印方法，可以添加其他工具难以自动删除的水印。

除了演示文稿，API 还支持从文字处理文档、电子表格、电子邮件、PDF 文件、图像、Visio 绘图和许多其他格式中添加、删除和提取水印。在演示文件格式中，它支持 PPT、PPTX、PPS、PPTM、PPSX 等。从[文档][8]，您可以进一步检查功能和[支持的文件格式][9]。

您可以从 [下载部分][10] 下载 DLL 或 MSI 安装程序，或从 [NuGet][11] 获取它。

```
Install-Package GroupDocs.Watermark
```

## 使用 C# 将文本作为水印添加到幻灯片 {#text-watermark-to-slides-in-csharp}

API 提供自定义以将文本作为水印添加到演示文稿中。以下步骤将指导您如何在 .NET 应用程序中的演示文件上应用水印。

* 使用 [Watermarker][12] 加载演示文稿。
* 使用[TextWatermark][13]设置水印文字和样式。
* 设置其他属性，如旋转、大小、不透明度、颜色和位置。
* 提供幻灯片的索引以应用水印。
* 使用[Add][14]方法添加格式化文本水印。
* 使用 [Save][15] 方法保存带水印的演示文稿。

以下代码示例使用 C# 将文本标签添加到 PPTX 演示文稿中作为第一张幻灯片上的水印，并使用 C# 进行旋转。

```
// 使用 .NET API 将文本水印添加到 C# 中的演示文稿幻灯片
using (Watermarker watermarker = new Watermarker("presentation.pptx"))
{
    // Set watermark text, coordinates and formatting
    TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 36))
    {
        RotateAngle = -45,
        X = 100,
        Y = 100,
        Height = 400,
        Width = 400,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center
    };
    // Apply Watermark to only first slide of the presentation
    PresentationWatermarkSlideOptions textWatermarkOptions = new PresentationWatermarkSlideOptions();
    textWatermarkOptions.SlideIndex = 0;
    
    // Add watermark to presentation and save.
    watermarker.Add(watermark, textWatermarkOptions);
    watermarker.Save("text-watermarked-presentation.pptx");
}
```

如果不提供幻灯片索引，默认情况下会在所有幻灯片上添加水印。上面的代码显示了如何提及幻灯片索引，但是，我在 PPTX 演示文稿的所有幻灯片上向您展示了带有文本水印的输出。



{{< figure align=center src="images/text-watermark-to-slide.png" alt="演示幻灯片的文本水印">}}


## 使用 C# 将图像水印插入幻灯片 {#image-watermark-to-slides-in-csharp}

同样，您可以在演示文件上添加图像作为水印。您只需要使用 [ImageWatermark][16] 类而不是 TextWatermark。以下是将图像水印添加到 .NET 应用程序中的演示文稿幻灯片的步骤。

* 使用 [Watermarker][17] 加载演示文稿。
* 使用 [ImageWatermark][18] 加载将用作水印的图像文件。
* 设置图像水印属性，如旋转、大小、不透明度、颜色和位置。
* 设置要应用水印的幻灯片索引。
* 使用 [Add][19] 方法将图像水印添加到演示文稿中。
* 使用 [Save][20] 方法保存带水印的演示文稿。

以下代码示例使用 C# 在第二张幻灯片上将图像添加到 PPTX 演示文稿中作为水印。

```
// 使用 .NET API 将图像水印添加到 C# 中的演示幻灯片
using (Watermarker watermarker = new Watermarker("presentation.pptx"))
{
    // Set watermark image, coordinates and formatting
    ImageWatermark imageWatermark = new ImageWatermark("watermark-image.png");
    imageWatermark.Opacity = .7;
    imageWatermark.X = 80;
    imageWatermark.Y = 120;
    
    // Apply Watermark to only second slide of the presentation
    PresentationWatermarkSlideOptions ImageWatermarkOptions = new PresentationWatermarkSlideOptions();
    ImageWatermarkOptions.SlideIndex = 1;

    // Add watermark to presentation and save.
    watermarker.Add(imageWatermark, ImageWatermarkOptions);
    watermarker.Save("image-watermarked-presentation.pptx");
}
```

以下是上述代码的输出，仅在 PPTX 演示文稿的第二张幻灯片上带有图像水印。



{{< figure align=center src="images/image-watermark-to-slide.jpg" alt="图像水印到演示幻灯片">}}


## 结论

总而言之，您已经学习了如何使用 C# 在演示幻灯片中添加文本和图像水印。现在，您可以构建自己的 .NET 应用程序，该应用程序支持演示文稿文件和演示文稿的特定幻灯片的文本和图像水印。查阅文档以[将水印应用于各种其他文档格式][21]。

您可以拥有 [免费临时许可证][22] 来体验产品的各个方面。免费支持将很乐意让您摆脱任何困惑并[解决您在论坛上与水印相关的问题][23]。

## 也可以看看

* [使用 C# 为图像添加水印][24]
* [使用 C# 在 Excel 工作簿中插入水印][25]
* [在 C# 中查找和删除文档中的水印][26]







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


