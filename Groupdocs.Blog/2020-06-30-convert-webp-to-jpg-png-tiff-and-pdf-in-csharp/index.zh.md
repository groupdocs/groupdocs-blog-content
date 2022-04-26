---
title: "在 C# 中将 WebP 转换为 JPG、PNG、TIFF 和 PDF"
date: Tue, 30 Jun 2020 07:03:38 +0000
draft: false
url: /zh/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "在我们之前的 [post][1] 中，我们讨论了 WebP 图像并学习了在 Java 中转换 WebP 图像。今天，在本文中，我们将学习使用 C# 以编程方式将 WebP 图像转换为 JPG、PNG、TIFF 和其他格式。"
tags: ['convert webp in csharp', 'convert webp to jpg in csharp', 'convert webp to pdf in csharp', 'convert webp to png in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

在我们之前的 [post][2] 中，我们讨论了 WebP 图像并学习了在 Java 中转换 WebP 图像。今天，在本文中，我们将学习使用 C# 以编程方式将 WebP 图像转换为 JPG、PNG、TIFF 和其他格式。



{{< figure align=center src="images/convert-webp-to-jpg-png-in-csharp.jpg" alt="在 CSharp 中将 WebP 图像转换为 JPG、PNG 或 PDF 格式">}}


首先，我们将看看以最简单的方式转换 WebP 图像。稍后我们将使用一些自定义选项进行转换，如倾斜、翻转、灰度、调整大小、更改 gamma、对比度和亮度，并为转换后的 JPG 图像添加水印。以下是主题的快速链接：

* [在 C# 中将 WebP 转换为 JPG、PNG 和 TIFF][3]
* [使用高级选项进行 WebP 转换（应用效果）][4]
* [在 C# 中将 WebP 转换为 PDF][5]

本文中的步骤和代码示例使用 [GroupDocs.Conversion for NET][6]。因此，请确保通过以下任一方法安装 API：

* 使用 [NuGet][7] 包管理器安装。
* [下载][8] DLL 并将其引用到项目中。

## 在 C# 中将 WebP 转换为 JPG {#convert-webp-to-jpg-png-tiff-in-csharp}

要将 WebP 图像转换为其他格式，请使用 **Converter** 类。对于简单的转换，您可以使用下面提到的几行 C# 代码。此示例显示了将 WebP 图像快速转换为 JPG 文件。只需按照以下步骤操作：

1. 使用源 WebP 图像实例化 [Converter][9] 对象。
2. 使用 [ImageConvertOptions][10] 类实例化图像转换选项，并将格式设置为 JPG。
3. 使用输出文件路径和转换选项调用 [Convert][11] 方法。

```
// Convert WebP image to JPG, PNG, BMP or any other format in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    ImageConvertOptions options = new ImageConvertOptions
    { // Set the conversion format to JPG
        Format = ImageFileType.Jpg
    };
    converter.Convert(@"./Output/converted-image.jpg", options);
}
```

以下是使用上述代码转换的原始 WebP 图像和转换后的 JPG 图像：



{{< figure align=center src="images/groupdocs_conversion-brand.webp" alt="WebP 图像" caption="WebP 图像">}}
</td><td>

{{< figure align=center src="images/converted-image.jpg" alt="从 WebP 转换为 JPG" caption="转换后的 JPG 图像">}}
</td></tr></tbody></table></figure>

### 在 C# 中将 WebP 转换为 PNG、TIFF 和其他图像格式

使用与上述相同的代码，只需更改文件格式，即 **"ImageFileType.Jpg"** 和输出文件名，您就可以轻松地将 WebP 文件转换为 JPEG、PNG、TIF、TIFF、BMP 等。

这是简单的转换，现在让我们转换不同的效果。

## 使用 C# 中的高级选项将 WebP 转换为 JPG、PNG、TIFF {#convert-webp-and-apply-effects-in-csharp}

除了将WebP转换为其他格式外，我们还可以在转换的同时添加效果。以下是一些效果，例如；转换为**灰度**； **水平或垂直翻转**图像； **旋转**图像到任意角度； **调整大小**图像以使其变小或变大；更改**对比度**、**亮度**、**伽玛**值；甚至将**水印**应用于转换后的图像。



{{< figure align=center src="images/converted-image.jpg" alt="从 WebP 转换为 JPG" caption="WebP 转 JPG">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-grayscale.jpg" alt="在灰度中从 WebP 转换为 JPG" caption="灰度">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-resize.jpg" alt="使用 Resize 从 WebP 转换为 JPG" caption="调整大小">}}
</td></tr><tr><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-flipped.jpg" alt="使用水平翻转从 WebP 转换为 JPG" caption="翻动">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-contrast-50.jpg" alt="从 WebP 转换为 JPG 并更改对比度" caption="对比">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-with-wateramrk.jpg" alt="从 WebP 转换为带水印的 JPG" caption="水印">}}
</td></tr><tr><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-rotated-1.jpg" alt="使用旋转从 WebP 转换为 JPG" caption="旋转">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-brightness-50.jpg" alt="从 WebP 转换为 JPG 并更改亮度" caption="亮度">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-with-gamma-0.5.jpg" alt="使用 Gamma Change 从 WebP 转换为 JPG" caption="伽玛">}}
</td></tr></tbody></table></figure>

这是用于应用这些效果的代码。您可以一个一个地或组合地应用这些效果以获得所需的结果。

```
// Apply effects while converting WebP image to other formats in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Jpg,
        Grayscale = true,   // Convert the image in Grayscale
        Height = 141,       // Resize the Image Height
        Width = 167,        // Resize the image Width
        FlipMode = ImageFlipModes.FlipX,    // Flip the image
        Contrast = 50,      // Change the contrast of image
        RotateAngle = 90,   // Rotate the image
        Brightness = 50,    // Change the brightness
        Gamma = 0.5F,       // Gamma Setting
        Watermark =         // Watermark Settings
        {
            Text = "GroupDocs",
            Width = 100,
            Height = 100,
            Background = false,
            Top = 70,
            Left = 90,
            RotationAngle = -45,
        }
    };
    converter.Convert(@"./Output/converted-with-options.jpg", options);
}
```

## 在 C# 中将 WebP 转换为 PDF {#convert-webp-to-pdf-in-csharp}

除了将 WebP 图像转换为其他图像文件格式外，我们还可以将图像转换为 PDF 格式。下面的 3 行代码将帮助您将 WebP 图像转换为 PDF 格式。

```
// Convert WebP to PDF in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert(@"./Output/converted-webp-image.pdf", options);
}
```

有关转换为 PDF 的更多详细信息和高级选项，您可以访问 [文档][12]。

## 也可以看看

* [在 Java 中将 WebP 转换为 JPG、PNG 和 PDF][13]

[GitHub 存储库][14] 上还有许多其他公开可用的开源示例。下载源代码并使用 [入门][15] 指南快速运行示例。如有任何困难，请查看 [文档][16] 或在 [论坛][17] 上随时与我们联系。







[1]: https://blog.groupdocs.com/2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
[3]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-to-jpg-png-tiff-in-csharp
[4]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-and-apply-effects-in-csharp
[5]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-to-pdf-in-csharp
[6]: https://products.groupdocs.com/conversion/net
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://downloads.groupdocs.com/conversion/net
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/16
[12]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[13]: https://blog.groupdocs.com/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/
[14]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET
[15]: https://docs.groupdocs.com/display/conversionnet/Getting+Started
[16]: https://docs.groupdocs.com/display/conversionnet/Home
[17]: https://forum.groupdocs.com/c/conversion


