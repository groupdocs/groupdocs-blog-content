---
title: "'使用 C# 将演示文稿转换为图像'"
date: Mon, 10 Jan 2022 04:03:00 +0000
draft: false
url: /zh/2022/01/10/convert-presentations-to-images-using-csharp/
author: 'Shoaib Khan'
summary: 'Probably you want to use your presentation slides within web applications or you want to use its slides thumbnails. In such cases, you need to convert your PowerPoint presentation slides to images. In this article, you will learn **how to convert the PPT or PPTX presentations into JPG and PNG images** programmatically using C#.

本文讨论了以下主题：

* .NET API 转换演示文稿
* 将 PPT/PPTX 转换为 JPG 图片
* 将 PPT/PPTX 转换为 PNG 图像'
tags: ['Convert PPT', 'Convert PPT to JPG in CSharp', 'Convert PPT to PNG in CSharp', 'Convert PPTX', 'PPT to JPG in CSharp', 'PPT to PNG in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

可能您想在 Web 应用程序中使用您的演示幻灯片，或者您想使用它的幻灯片缩略图。在这种情况下，您需要将 PowerPoint 演示文稿幻灯片转换为图像。在本文中，您将学习**如何使用 C# 以编程方式将 PPT 或 PPTX 演示文稿转换为 JPG 和 PNG 图像** 文件。



{{< figure align=center src="images/convert-ppt-to-jpg-png-image-using-dotnet.jpg" alt="使用 .NET 将 PPT 转换为 JPG 或 PNG 图像">}}


此处讨论了以下主题：

* [.NET API 转换演示文稿](#ppt-convert-dotnet-api)
* [将 PPT/PPTX 转换为 JPG 图片](#ppt-to-jpg)
* [将PPT/PPTX转换为PNG图片](#ppt-to-png)

## .NET API 转换演示文稿 {#ppt-convert-dotnet-api}

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/) 展示了允许在 .NET 应用程序中将演示文件转换为图像的 .NET API。在本文中，我们将使用其 [GroupDocs.Conversion for .NET](https://products.groupdocs.com/conversion/net/) 将 PPT/PPTX 演示文稿转换为图像格式。此外，API 支持许多其他文件格式的转换，例如文字处理文档、电子表格、演示文稿、电子书、图像以及 [文档](https://docs.groupdocs.com/conversion/网络/支持的文档格式/) 。

您可以从 [下载部分](https://downloads.groupdocs.com/conversion) 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.conversion) 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 使用 C# 将演示文稿转换为 JPG 图像 {#ppt-to-jpg}

让我们快速跳转到目标并将我们的演示文稿转换为图像格式。以下步骤展示了如何在 C# 中将 Powerpoint PPT 或 PPTX 转换为 JPG 图像格式。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) 类加载演示文件。
* 使用 [ImageConvertOptions](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions) 类准备图像转换选项。
* 定义转换文件格式为JPG。
* 使用 [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) 方法转换为图像。

以下 C# 源代码将 PowerPoint 演示文稿转换为 JPG 格式。

```
// 使用 C# 将 PPT、PPTX 演示文稿转换为 JPG 图像
SavePageStream getPageStream = page => new FileStream(string.Format("path/convertedPPT{0}.jpg", page), FileMode.Create);

using (Converter converter = new Converter("path/presentation.ppt"))
{
    ImageConvertOptions options = new ImageConvertOptions 
    { 
        Format = ImageFileType.Jpg 
    };  
    converter.Convert(getPageStream, options);
}
```

## 使用 C# 将演示文稿转换为 PNG 图像 {#ppt-to-png}

最常用的图像格式之一是 PNG。让我们以类似的方式将幻灯片转换为 PNG。以下步骤指导如何在 C# 中将 Powerpoint PPT 或 PPTX 转换为 PNG 图像格式。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter) 类加载演示文稿 PPT/PPTX 文件。
* 准备 [图片转换选项](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions)。
* 将转换文件格式设置为PNG。
* 使用 [Convert()](https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index) 方法将演示文稿转换为图像。

以下 C# 代码示例将 PowerPoint 演示文稿转换为 PNG 格式。

```
// 使用 C# 将 PPT、PPTX 演示文稿转换为 PNG 图像
SavePageStream getPageStream = page => new FileStream(string.Format("path/convertedPPT{0}.png", page), FileMode.Create);

using (Converter converter = new Converter("path/presentation.ppt"))
{
    ImageConvertOptions options = new ImageConvertOptions 
    { 
        Format = ImageFileType.Png 
    };  
    converter.Convert(getPageStream, options);
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

最后，我们了解了如何在 C# 中将演示文稿转换为 JPG 或 PNG 图像格式。要构建您自己的转换应用程序，您可以使用 [文档](https://docs.groupdocs.com/conversion/net/) 了解有关 Conversion Automation .NET API 的更多信息。最好的方法是体验 [GitHub](https://github.com/groupdocs-conversion) 上提供的示例。如有任何疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [在 C# 中将演示文稿转换为 PDF](https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/)
* [使用 C# 将 Excel 电子表格转换为 PDF](https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/)
* [使用 C# 将 JSON 转换为 CSV 和 CSV 转换为 JSON](https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/)