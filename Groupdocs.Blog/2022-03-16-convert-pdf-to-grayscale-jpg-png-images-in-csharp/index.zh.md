---
title: "'使用 C# 将 PDF 转换为灰度'"
date: Wed, 16 Mar 2022 12:05:00 +0000
draft: false
url: /zh/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/
author: 'Shoaib Khan'
summary: "您脑海中的第一个也是最重要的问题可能是，是否仅将 RGB 图像转换为灰度图像？不，您几乎可以将任何文档格式（包括图像) 转换为黑白或灰度单色图像。对比度范围从最弱的黑色到最强的白色。在本文中，我们将讨论**如何使用 C#** 将彩色 PDF 文档转换为灰度 JPG 和 PNG 图像格式。"
tags: ['convert to grayscale', 'Convert to Grayscale in CSharp', 'document to image', 'PDF to Grayscale', 'PDF to Grayscale in CSharp', 'PDF to JPG Grayscale', 'PDF to PNG Grayscale']
categories: ['GroupDocs.Conversion Product Family']
---

您脑海中的第一个也是最重要的问题可能是，是否仅将 RGB 图像转换为灰度图像？不，您几乎可以将任何文档格式（包括图像) 转换为黑白或灰度单色图像。对比度范围从最弱的黑色到最强的白色。在本文中，我们将讨论如何使用 C#** 将彩色 PDF 文档转换为**灰度 JPG 和 PNG 图像格式。



{{< figure align=center src="images/Converted-Colored-PDF-to-Grayscale-1024x577.jpg" alt="将 PDF 转换为灰度">}}


如果您要进行图像处理，此功能非常有用。由于 RGB 图像由 3 个通道表示并且包含大量数据/噪声，因此需要更多的计算能力来处理这样的图像。另一方面，灰度图像使这个过程相对容易。

## .NET API 将文档转换为灰度

[GroupDocs.Conversion for .NET](https://products.groupdocs.com/conversion/net/) 是一种 API，用于在多种 [支持的文件格式和图像类型](https://docs.groupdocs.com/conversion/net/supported-document-formats/) 。转换结果可以通过多种灵活的选项轻松定制和调整。我将使用此 API 将 PDF 文档转换为灰度 JPG 和 PNG 图像。

您可以从 [下载部分](https://downloads.groupdocs.com/conversion) 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https) 在您的 .NET 应用程序中安装 API ://www.nuget.org/packages/groupdocs.conversion) 。

```
PM> Install-Package GroupDocs.Conversion
```

  
如果我们谈论它的实现，它是一个后端 API，可以在任何 .NET 应用程序中集成或实现，而无需任何依赖。有关其 API 的更多信息，请访问其 [文档](https://docs.groupdocs.com/conversion/net/)。

## 使用 C# 将 PDF 转换为灰度 JPG 图像

让我们通过将彩色 PDF 文档转换为黑白图像格式来快速实现目标。以下步骤展示了如何使用 C# 将 PDF 转换为灰度 JPG。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) 类加载 PDF 文档。
* 准备[图像转换选项](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions)。
* 设置转换文件格式为JPG。
* 将灰度选项设置为 true。
* 使用 [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) 方法转换为图像。

以下 C# 源代码将 PDF 文档转换为灰度 JPG 图像。

```
// 在 C# 中将 PDF 转换为灰度 JPG
using (Converter converter = new Converter("path/document.pdf"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Jpg,
        Grayscale = true,
        
        // Aditional Conversion Options
        Height = 1024,       
        Width = 1024,
        FlipMode = ImageFlipModes.FlipX,
        RotateAngle = 90,
        /*
        Brightness = 50,// Brightness
        Gamma = 0.5F,   // Gamma Settings
        Contrast = 50   // Contrast
        */
    };
    converter.Convert("path/grayscaleDocument.jpg", options);
}
```

此外，还有许多其他选项可以控制高度、宽度、水平和垂直翻转以及文档旋转。您还可以将具有不同设置的水印应用于输出图像。

## 使用 C# 将 PDF 转换为灰度 PNG 图像

同样，彩色 PDF 文档可以转换为其他灰度图像格式。以下步骤展示了如何使用 C# 将 PDF 转换为灰度 PNG。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) 类加载 PDF 文档。
* 准备[图像转换选项](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions)。
* 将转换文件格式设置为PNG。
* 将灰度选项设置为 true。
* 使用 [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) 方法转换为 PNG 图像。

以下 C# 源代码将 PDF 文档转换为灰度 PNG 图像。

```
// 在 C# 中将 PDF 转换为灰度 PNG
using (Converter converter = new Converter("path/document.pdf"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Png,
        Grayscale = true
    };
    converter.Convert("path/grayscaleDocument.png", options);
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

最后，我们了解了如何在 C# 中将 PDF 文档转换为 JPG 或 PNG 图像格式。要构建您自己的转换应用程序，您可以从 [文档](https://docs.groupdocs.com/conversion/net/) 了解有关低代码和高代码转换自动化 .NET API 的更多信息。

最好的方法是体验 [GitHub](https://github.com/groupdocs-conversion) 上提供的示例。如有任何疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [在 C# 中将图像转换为 PDF](https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/)
* [使用 C# 将演示文稿转换为图像](https://blog.groupdocs.com/2022/01/10/convert-presentations-to-images-using-csharp/)
* [在 C# 中将 WebP 图像转换为 JPG、PNG、TIFF 和 PDF](https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/)





