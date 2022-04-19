---
title: "在 C# 中将文档转换为 HTML 时显示和隐藏页面边框"
date: Wed, 29 Apr 2020 20:18:10 +0000
draft: false
url: /zh/2020/04/29/convert-doc-docx-to-html-in-csharp-and-show-or-hide-page-borders/
author: 'Shoaib Khan'
summary: "要么您想将文档转换为 HTML 格式以获取您网站的内容，要么您遇到了要求以 HTML 格式提交文档的在线文档提交网站。无论哪种情况，您都需要一个**DOC 到 HTML 转换器**。但是，如果您需要以编程方式将**文档转换为 HTML**，那么本文仅供您参考。本文将介绍以下在 C# 中将文档转换为 HTML 的方法："
tags: ['convert document to html in csharp', 'convert docx to html', 'convert docx to html in csharp', 'convert to html', 'show or hide html page borders']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-doc-to-html-with-show-and-hide-borders.png" alt="在 CSharp 中将 DOCX 转换为 HTML">}}


要么您想将文档转换为 HTML 格式以获取您网站的内容，要么您遇到了要求以 HTML 格式提交文档的在线文档提交网站。无论哪种情况，您都需要一个**DOC 到 HTML 转换器**。但是，如果您需要以编程方式将**文档转换为 HTML**，那么本文仅供您参考。本文将介绍以下在 C# 中将文档转换为 HTML 的方法：

* 在 C# 中将 DOCX 等文档最简单地转换为 HTML。
* 使用自定义选项转换为 HTML。
* 使用显示或隐藏页面边框的选项进行转换。

## C# 文档转换库

[GroupDocs.Conversion for .NET][1] 是一个易于使用的强大 API，能够将 [支持的文档格式][2] 广泛列表中的任何文档转换为任何支持的目标格式。您可以从 [下载][3] 部分下载 API 或从 [NuGet][4] 安装它。

## 在 C# 中将 DOCX 转换为 HTML - 简单

这是最简单且非常有用的转换。我最好说您可以将任何文档转换为 HTML 格式。只需从 [支持的格式列表][5] 中检查您的格式，然后继续进行转换即可。

* 创建 [Converter][6] 类的实例以从您的源文档开始。
* 实例化 [MarkupConvertOptions][7] 对象。
* 调用Converter类的[Convert][8]方法。
* 就是这样。

您的文档将被转换为 HTML，并且生成的文档将在您的存储库中。以下小代码示例显示了使用 C# 中的 Converter 类将 **DOCX 文件转换为 HTML**。

```
// Converting DOCX to HTML in C#
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions();
    converter.Convert("converted.html", options);
}
```

## 使用自定义选项将 DOC/DOCX 转换为 HTML

GroupDocs.Conversion 提供了不同的其他选项来获得所需的转换结果。自定义选项包括：

* 固定布局
* 固定布局 - 显示边框
* 格式
* 页码
* 页面
*页数
* 使用 PDF
* 水印
* 飞涨

您可以访问 [文档][9] 或 [GitHub 示例][10] 详细查看每个选项。我将在下面的代码示例中再次将 DOCX 转换为 HTML 格式时展示一些自定义项。

```
// Converting DOCX to HTML in C# with advance options.
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions
    { // Setting customized options
        PageNumber = 2,
        PagesCount = 1,
        FixedLayout = true
    };
    converter.Convert("converted.html", options);
}
```

## 将 DOC/DOCX 转换为 HTML - 显示或隐藏页面边框

最后但同样重要的是，您现在可以在使用 C# 将文档转换为 HTML 时控制页面边框的可见性。 .NET 的 GroupDocs.Conversion 将此控制权交给 C# 程序员。下面的示例显示，通过将 [MarkupConvertOptions][12] 类的 [FixedLayoutShowBorders][11] 属性设置为 true 或 false，您可以在生成的 HTML 文档中显示或隐藏页面边框。

```
// Converting DOCX to HTML in C# with show or hide borders control.
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions
    {
        PageNumber = 2,
        FixedLayout = true,
        PagesCount = 1,
        FixedLayoutShowBorders = false
    };
    converter.Convert("converted.html", options);
}
```

下面的图像显示了原始 DOCX 文档和转换后的带有和不带有页面边框的 HTML。



{{< figure align=center src="images/word-docx-document-1-759x1024.png" alt="Docx 文档转换成 HTML" caption="原始 DOCX 文件">}}




{{< figure align=center src="images/doc-to-html-file-with-borders-and-no-borders-1024x716.jpg" alt="带有页面边框和无边框的 HTML 文件。" caption="<em>上图显示了从 DOCX 转换而来的带有显示边框和不显示边框选项的 HTML 文件。</em>">}}


## 了解有关 GroupDocs.Conversion 的更多信息

* [文档][13]
* [源代码示例][14]
* [GroupDocs.Conversion - 文档和图像转换解决方案][15]

**让我们多谈谈@** [免费支持论坛][16]。







[1]: https://products.groupdocs.com/conversion/net
[2]: https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats
[3]: https://downloads.groupdocs.com/conversion/net
[4]: https://www.nuget.org/packages/groupdocs.conversion
[5]: https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/4
[9]: https://docs.groupdocs.com/display/conversionnet/Convert+to+HTML+with+advanced+options
[10]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET/blob/master/Examples/GroupDocs.Conversion.Examples.CSharp/AdvancedUsage/Converting/ConvertToHtmlWithAdvancedOptions.cs
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions/properties/fixedlayoutshowborders
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
[13]: https://docs.groupdocs.com/display/conversionnet/Getting+Started
[14]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET
[15]: https://products.groupdocs.com/conversion
[16]: https://forum.groupdocs.com/c/conversion


