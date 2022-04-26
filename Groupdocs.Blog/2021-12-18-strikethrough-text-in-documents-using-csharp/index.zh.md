---
title: "使用 C# 删除文档中的文本"
date: Sat, 18 Dec 2021 19:10:44 +0000
draft: false
url: /zh/2021/12/18/删除线-text-in-documents-using-csharp/
author: 'Shoaib Khan'
summary: "在某些情况下，您需要指出有错误或不再有效的内容。划掉是在文档中标记无效内容的方法之一。为了在 .NET 应用程序中自动删除，本文展示了**如何使用 C#** 在文档中删除文本。"
tags: ['Cross out Text', 'Cross out Text in CSharp', 'Strikeout Text', 'Strikethrough Text', 'Strikethrough Text in CSharp']
categories: ['GroupDocs.Annotation Product Family']
---



{{< figure align=center src="images/strikethrough-text-using-csharp.jpg" alt="使用 C# 的 StrikeThrough 文本">}}


在某些情况下，您需要指出有错误或不再有效的内容。划掉是在文档中标记无效内容的方法之一。因此，为了在 .NET 应用程序中自动删除，本文展示了**如何使用 C#** 在文档中删除文本。

本文讨论了以下主题。

* [用于删除线注释的.NET API][1]
* [如何删除文档中的文本][2]

## .NET API 到删除线文本 {#strikethrough-text-dotnet-api}

[GroupDocs.Annotation][3] 是一种文档和图像注释解决方案，允许在多种文档格式中自动执行各种注释类型。因此，我将在本文的示例中使用它的 .NET API 来删除文档中的文本。除了删除线注解之外，[文档][5] 中还提到了许多其他[支持的注解类型][4]。

从 [下载部分][6] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Annotation
```

## 如何使用 C# 删除文档中的文本 {#strikethrough-text-using-csharp}

让我们快速开始删除文档中已识别的错误。以下步骤允许您使用 C# 删除文档中的文本。

* 使用 [Annotator][8] 类加载源文档。
* 使用 [StrikeoutAnnotation][9] 类创建和定义删除线注释。
    * 设置删除线颜色。
    * 不透明度，文档页码
    * 坐标和其他属性
* 使用 [Add()][10] 方法将准备好的删除注释添加到注释器。
* 使用 [Save()][11] 方法保存带注释的文档。

以下 C# 代码示例删除了 PDF 文档中的选定文本。

```
/*
 * Strikethrough Text in Word, PDF, Spreadsheets, Presentations using C#
 */
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    StrikeoutAnnotation strikeout = new StrikeoutAnnotation
    {
        FontColor = 0x000000,
        Opacity = 0.7,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(183, 770),
            new Point(308, 770),
            new Point(183, 752),
            new Point(308, 752)
        }
    };
    annotator.Add(strikeout);
    annotator.Save("path/strikethrough-text.pdf");
}
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证][12] 免费使用 GroupDocs.Annotation for .NET。

## 结论

总而言之，您学会了使用 C# 添加删除线注释。使用此注释，您可以以编程方式删除 Word、PDF、电子表格、演示文稿文档中的文本。同样，您可以根据需要尝试各种其他注释类型。

访问其[文档][13]，了解有关 **GroupDocs.Annotation for .NET** 的更多信息。您可以为 [支持的文档格式][14] 构建自己的注释器应用程序。您可以通过 [论坛][15] 联系我们进行查询。

## 也可以看看

* [在 C# 中使用注释突出显示 PDF][16]
* [使用 C# 在文档中添加波浪下划线][17]







[1]: #strikethrough-text-dotnet-api
[2]: #strikethrough-text-using-csharp
[3]: https://products.groupdocs.com/annotation/
[4]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[5]: https://docs.groupdocs.com/annotation/net/
[6]: https://downloads.groupdocs.com/annotation/net
[7]: https://www.nuget.org/packages/groupdocs.comparison
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/strikeoutannotation
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/annotation/net
[14]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[17]: https://blog.groupdocs.com/2021/12/04/add-wavy-underline-in-documents-using-csharp/


