---
title: "在 C# 中将 PowerPoint PPT、PPTX 和 OpenOffice 演示文稿转换为 PDF"
date: Thu, 05 Mar 2020 21:59:00 +0000
draft: false
url: /zh/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
aliases:
- /2020/03/05/convert-pptx-to-pdf-in-csharp/
- /2020/03/05/convert-ppt-to-pdf-in-csharp/
- /2020/03/05/convert-pptx-ppt-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "[PDF][1]无疑是[Portable Document Format][2]，是最常用的文件格式之一。 Microsoft PowerPoint 的[PPT][3] 和 [PPTX][4] 格式在商务文档中同样受欢迎。由于文档格式的流行和 PDF 格式的固定布局性质，因此需要**将 PPT/PPTX 转换为 PDF** 格式。"
tags: ['Convert PPT to PDF in CSharp', 'Convert PPTX to PDF in CSharp', 'CSharp PPT to PDF', 'CSharp PPTX to PDF']
categories: ['GroupDocs.Conversion Product Family']
---

[PDF][5]无疑是[Portable Document Format][6]，是最常用的文件格式之一。 Microsoft PowerPoint 的[PPT][7] 和[PPTX][8] 格式在商务文档中享有盛誉。由于文档格式的流行和 PDF 格式的固定布局性质，因此需要**将 PPT/PPTX 转换为 PDF** 格式。



{{< figure align=center src="images/Convert-PPT-to-PDF-csharp.png" alt="C# 中的 PPTX 到 PDF">}}


考虑到今天的 .NET 开发人员，本文将为上述文件格式转换提供解决方案。 GroupDocs 支持 [50+ 文档格式][9] 的转换，因此提供本地 API（.NET 和 Java）、云 API 和在线 [转换应用程序][10]。在本文之后，您将熟悉使用 [GroupDocs.Conversion for .NET][11] 转换 Microsoft 和 OpenOffice 演示文稿的不同方法。

下面讨论以下主题：

* [如何将完整的演示文稿转换为 PDF][12]
* [将特定PPT幻灯片转换为PDF][13]
* [将幻灯片的连续子集转换为 PDF][14]
* [PowerPoint PPT/PPTX 格式的可能转换][15]
* [使用高级选项转换演示文稿][16]
* [在转换为 PDF 时应用水印][17]

## 在 C# 中将 PPT 转换为 PDF {#ppt-to-pdf}

[GroupDocs.Conversion][18] 让这一切变得如此简单；演示文件的流行和苛刻的转换。只需使用下面提到的两行 CSharp 代码，您就可以快速将任何类型的演示文稿，如 PPTX 或 PPT 转换为 PDF。

* 使用源文档创建 [Converter][19] 类的新实例。
* 实例化 [PdfConvertOptions][20] 对象。
* 调用 Converter 类的 [Convert()][21] 方法。

以下代码示例将完整的 PowerPoint PPTX 转换为 C# 中的 PDF。

```
// 使用 C# 将整个 PPT 转换为 PDF
using (Converter converter = new Converter("path/presentation.pptx"))
{
    converter.Convert("path/converted-presentation.pdf", new PdfConvertOptions());
}
```

## 在 C# 中将 PPT 的特定幻灯片转换为 PDF {#specific-slides}

我们可能需要只转换选定的幻灯片，而不是转换整个演示文稿。 GroupDocs.Conversion 允许将演示文稿的特定幻灯片转换为生成的 PDF 文档。以下是显示如何实现此目的的步骤和 C# 源代码。

* **使用 [Converter][22] 类加载**演示文稿。
* 为 PDF 准备 [ConversionOptions][23]。
* **列出要转换的选定幻灯片编号**。
* **使用 [Convert()][24] 方法将**转换为 PDF。

以下源代码将演示文稿的第 1 和第 3 张幻灯片转换为 PDF。

```
// 使用 C# 仅将特定的 PPT 幻灯片转换为 PDF
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        Pages = new List<int>{ 1, 3 }
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## 使用 C# 将 PPTX 的连续幻灯片转换为 PDF {#successive-slides}

对需求稍作修改，下面是代码的小改动。可以选择演示文稿的某些连续幻灯片以将其转换为 PDF 格式。只需在前面设置起始页码和连续页数。

* **使用 [Converter][25] 类加载**演示文件。
* 使用 [PDF 转换选项][26] 设置**起始页码**和**连续幻灯片计数**。
* **使用 [Convert()][27] 方法以 PDF 格式保存**选定的幻灯片。

以下代码片段将幻灯片编号 2、3 和 4 转换为 C# 中的 PDF 格式。

```
// 使用 C# 将几个连续的 PPT 幻灯片转换为 PDF
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        PageNumber = 2,
        PagesCount = 3
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## PPT/PPTX 的可能转换 {#possible-conversions}

这不仅是转换时可以作为目标文档格式的 PDF。您可以参考[所有可能的转换的文档][28]。对开发者来说更重要的是，我们可以通过调用 Converter 类的 GetPossibleConversions() 方法来检索所有可能的 PPT/PPTX 演示文稿的转换格式。

* 使用 [Converter][29] 类定义源格式。
* 使用 [GetPossibleConversions()][30] 方法获取源格式的所有可能转换。

以下源代码显示了如何使用 C# 检索 PPTX 格式的所有可能转换。

```
// 使用 .NET API 列出可能的 PPT 转换
string sourceFile = "path/presentation.pptx";
using (Converter converter = new Converter(sourceFile))
{
    PossibleConversions conversions = converter.GetPossibleConversions();
    Console.WriteLine("{0} is of type {1} and could be converted to:", sourceFile, conversions.Source.Extension);
    foreach (var conversion in conversions.All)
    {
        Console.WriteLine("\t {0} as {1} conversion.", conversion.Format, conversion.IsPrimary?"primary": "secondary");
    }
}
```

## 使用高级选项将 PPT 转换为 PDF {#ppt-to-pdf-adv}

转换演示文稿时还有更多选项。这些选项很少需要，但是在需要时，它们证明了它们的重要性。 [**PdfConvertOptions**][31] 在转换为 PDF 时可以控制转换结果。除了常见的转换选项外，它还有许多其他选项，可以从 [文档][32] 中详细查看。只是为了概述，我们可以使用提到的选项和更多自定义 PPT 转换：

* [缩放][33]
* [边距][34]
* [灰度][35]
* [格式选项][36]
* [图像质量][37]
* [旋转][38]
* [水印][39]

```
// 使用 C# 使用高级选项将演示文稿转换为 PDF
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        PageNumber = 2,
        PagesCount = 1,
        Rotate = Rotation.On180,
        Dpi = 300,
        Width = 1024,
        Height = 768
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## 在 C# 中将 PPTX 或 PPT 转换为 PDF 时添加水印 {#watermarked}

想要在将演示文稿转换为 PDF 格式时保护您的演示文稿？在生成的 PDF 上留下水印。下面提到的步骤和源代码显示了如何在将 PPT/PPTX 演示文稿转换为 PDF 格式时添加水印。

* **加载**使用 [Converter][40] 类的 PPT 文件。
* **准备[文本水印选项][41]**并定义：
    
    * 水印文字和字体
    
    * 水印颜色
    * 宽度和高度
    * 旋转角度
    * 透明度
* **将准备好的水印**添加到[PDF转换选项][42]。
* **使用 [Convert()][43] 方法将演示文稿保存为 PDF。

以下 C# 代码示例在将 PPT 转换为 PDF 时添加了带有旋转角度和透明度的水印。

```
// 使用 C# 将水印应用于演示文稿幻灯片，同时将其转换为 PDF
using (Converter converter = new Converter("path/presentation.pptx"))
{
    PdfConvertOptions options = new PdfConvertOptions
    {
        Watermark = new WatermarkTextOptions("Watermark")
        {
            Color = Color.Blue,
            Width = 100,
            Height = 100,
            Background = true,
            RotationAngle = -45,
            Transparency = 0.5
        }
    };
    converter.Convert("path/converted-presentation.pdf", options);
}
```

## 结论

让我们总结一下我们讨论的内容。我们学习了在 C# 中将 PPT 转换为 PDF 格式的不同方法。我们分别查看了用于转换**特定幻灯片列表**、演示幻灯片的任何**连续子集**以及将**PPT转换为带有自定义水印**和其他选项的 PDF 的步骤和代码示例。从 [文档][44] 中了解有关 **GroupDocs.Conversion** 的更多信息。

## 让我们谈谈

您可以使用上面突出显示的功能构建自己的应用程序。如果您在 [论坛][45] 上与我们联系以讨论、解决问题或分享您的反馈，我们将非常高兴。有一个美好的发展时间。

## 也可以看看

* [用 Java 将 PowerPoint 和 OpenOffice 演示文稿转换为 PDF][46]







[1]: https://wiki.fileformat.com/view/pdf/
[2]: https://en.wikipedia.org/wiki/PDF
[3]: https://wiki.fileformat.com/presentation/ppt/
[4]: https://wiki.fileformat.com/presentation/pptx/
[5]: https://wiki.fileformat.com/view/pdf/
[6]: https://en.wikipedia.org/wiki/PDF
[7]: https://wiki.fileformat.com/presentation/ppt/
[8]: https://wiki.fileformat.com/presentation/pptx/
[9]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[10]: https://products.groupdocs.app/conversion/family
[11]: https://products.groupdocs.com/conversion/net
[12]: #ppt-to-pdf
[13]: #specific-slides
[14]: #successive-slides
[15]: #possible-conversions
[16]: #ppt-to-pdf-adv
[17]: #watermarked
[18]: https://products.groupdocs.com/conversion
[19]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[20]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[21]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter/methods/convert/2
[22]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[23]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[24]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[25]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[26]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[27]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[28]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[29]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[30]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/getpossibleconversions/index
[31]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[32]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/#ConverttoPDFwithadvancedoptions-PdfOptions
[33]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptions/properties/zoom
[34]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginleft
[35]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptions/properties/grayscale
[36]: https://docs.groupdocs.com/display/conversionnet/Convert+to+PDF+with+advanced+options#ConverttoPDFwithadvancedoptions-PdfFormattingOptions
[37]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptimizationoptions/properties/imagequality
[38]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/rotate
[39]: https://apireference.groupdocs.com/conversion/net
[40]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[41]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/watermarktextoptions
[42]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[43]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[44]: https://docs.groupdocs.com/conversion/net/
[45]: https://forum.groupdocs.com/c/conversion
[46]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/


