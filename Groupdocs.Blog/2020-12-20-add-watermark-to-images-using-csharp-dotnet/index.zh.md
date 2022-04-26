---
title: "使用 C# 向图像添加水印"
date: Sun, 20 Dec 2020 11:03:00 +0000
draft: false
url: /zh/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
aliases:
- /2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
- /2019/10/21/csharp-dotnet-api-to-add-watermark-to-images/
- /2019/10/21/c-api-to-add-watermark-on-photos-or-images/
author: 'Shoaib Khan'
summary: "今天让我们看看如何给图片添加水印。这有助于您为您的官方摄影打上烙印，并保护您的照片免遭任何未经授权的使用。本文将指导您**使用 C# 以编程方式将文本和图像水印添加到图像文件中**。在较早的一篇文章中，我们已经看到 [使用 Java 向图像添加基于文本和图像的水印][1]。阅读本文后，您将不难在 .NET 应用程序中使用 C# 为 **JPG/JPEG、PNG、WebP、GIF、TIFF、JP2、BMP** 图像添加水印。"
tags: ['add watermark in csharp', 'how to add watermark in csharp', 'watermark dotnet api', 'watermark images in csharp']
categories: ['GroupDocs.Watermark Product Family']
---

今天我们来看看，如何给图片添加水印。这可以帮助您为您的官方摄影打上烙印，并保护您的照片免遭任何未经授权的使用。本文将指导您**使用 C# 以编程方式将文本和图像水印添加到图像文件中**。在之前的一篇文章中，我们已经看到[使用 Java 向图像添加基于文本和图像的水印][2]。阅读本文后，您将不难在 .NET 应用程序中使用 C# 为 **JPG/JPEG、PNG、WebP、GIF、TIFF、JP2、BMP** 图像添加水印。

现在让我们分别看看，我们如何使用 [.NET Watermarking API for documents and images][3] 在 C# 中的图片、照片或图像文件上轻松添加基于文本和图像的水印。

* [在图像上添加文字作为水印][4]
* [在图像中插入图像水印][5]

## .NET 的文本和图像水印 API {#mce_0}



{{< figure align=center src="images/groupdocs-watermark-net.png" alt=".NET 的水印 API - GroupDocs">}}


**GroupDocs.Watermark for .NET** 是一个 API，用于在 .NET 应用程序中为不同文件格式的图像或文档添加水印。它提供了有效的水印方法，允许您添加文本水印以及其他第三方工具难以自动删除的图像水印。

从[文档][6]，您可以进一步检查功能和[支持的文件格式][7]。

您可以从 [下载部分][8] 下载 DLL 或 MSI 安装程序，或从 [NuGet][9] 获取。

```
Install-Package GroupDocs.Watermark
```

## 使用 C# 将文本作为水印添加到图像中 {#add-text-watermark-to-image-using-csharp}



{{< figure align=center src="images/text-watermark-on-png-using-java.png" alt="使用 Java 和 .NET 将文本水印添加到 PNG 图像">}}


该 API 允许您将文本添加到图像作为具有许多自定义的水印。以下步骤指导我们如何在 .NET 应用程序中使用 C# 在图像文件、照片或图片上应用水印。

1. 使用 [Watermarker][10] 加载图像。
2. 使用 [TextWatermark][11] 设置水印文本和样式。
3. 设置其他水印属性，如位置、旋转、不透明度等。
4. 使用 [Add][12] 方法将文本水印添加到图像中。
5. 使用 [Save][13] 方法保存输出图像。

以下 C# 代码示例在 JPG 图像上添加一个文本标签作为带有一些文本旋转的水印。

```
// 使用 C# 将文本水印添加到 JPG
using (Watermarker watermarker = new Watermarker("filePath/image.jpg"))
{
    // Set the Text and Watermark Font
    Font font = new Font("Arial", 30, FontStyle.Bold | FontStyle.Italic);
    TextWatermark watermark = new TextWatermark("GroupDocs", font);

    // Set Watermark Properties
    watermark.ForegroundColor = Color.Black;
    watermark.TextAlignment = TextAlignment.Right;
    watermark.X = 70;
    watermark.Y = 70;
    watermark.RotateAngle = -30;
    watermark.Opacity = 0.4;
    // watermark.BackgroundColor = Color.Blue;

    // Add the configured watermark to JPG Image
    watermarker.Add(watermark);
    watermarker.Save("filePath/outputImage.jpg");
}
```

## 使用 C# 将图像水印插入图像 {#add-image-watermark-to-image-using-csharp}



{{< figure align=center src="images/image-watermark-on-jpg-image-using-java.jpg" alt="使用 GroupDocs.Watermark 将图像水印添加到 JPG 图像">}}


同样，我们也可以在源图像文件上添加另一个图像作为水印。为此，请使用 **ImageWatermark** 类及其属性来自定义水印外观。

* 创建 [Watermarker][14] 类对象以加载源图像。
* 使用 [ImageWatermark][15] 类准备图像水印。
* 设置水印属性。
* 使用 [Add][16] 方法在源图像上添加图像水印。
* 使用[Save][17]方法保存输出图像。

以下 C# 代码示例在另一个 PNG 文件上添加一个 PNG 图像作为首选位置的水印。

```
// 使用 C# 在图像上添加 PNG 图像水印
using (Watermarker watermarker = new Watermarker("filePath/image.png"))
{
    using (ImageWatermark watermark = new ImageWatermark("filePath/watermarkLogo.png"))
    {
        // Set Watermark Properties
        watermark.X = 20;
        watermark.Y = 80;
        // Add watermark on image file and save the output
        watermarker.Add(watermark);
        watermarker.Save("filePath/outputImage.png");
    }
}
```

## 结论

我相信您现在可以使用 C# 轻松地将水印添加到您的图像文件中。您甚至可以构建自己的 .NET 应用程序，支持对各种文件格式的文档和图像进行水印处理。

您可以拥有 [免费临时许可证][18] 来体验产品的各个方面。免费支持将很乐意让您摆脱任何困惑并[解决您在论坛上与水印相关的查询][19]。

## 也可以看看

* [使用C#在Excel表格中添加水印][20]
* [C#去除文档水印][21]
* [在Java中为图像添加水印][22]







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


