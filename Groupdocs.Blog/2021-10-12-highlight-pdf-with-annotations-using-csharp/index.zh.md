---
title: "在 C# 中使用注释突出显示 PDF"
date: Tue, 12 Oct 2021 14:08:00 +0000
draft: false
url: /zh/2021/10/12/highlight-pdf-with-annotations-using-csharp/
author: 'Shoaib Khan'
summary: "在查看或吸引查看者查看重要内容时，您可能需要突出显示文档的某些部分。作为开发人员，您可以通过在应用程序中使用高亮注释来自动化此功能。在本文中，您将学习**如何使用 C# 突出显示 PDF 文件中的文本和任何区域**。"
tags: ['annotate PDF', 'Annotate PDF in CSharp', 'Highlight Annotation', 'Highlight PDF in CSharp', 'Highlight Text in PDF', 'Text Highlight']
categories: ['GroupDocs.Annotation Product Family']
---

在查看或吸引查看者查看重要内容时，您可能需要突出显示文档的某些部分。作为开发人员，您可以通过在应用程序中使用高亮注释来自动化此功能。在本文中，您将学习**如何使用 C# 突出显示 PDF 文件中的文本和任何区域**。

以下主题涵盖以下内容：

* [.NET API 在 PDF 中突出显示][1]
* [如何以编程方式在 PDF 中突出显示][2]



{{< figure align=center src="images/add-highlight-annotation-in-pdf-using-groupdocs.jpg" alt="在 PDF 中突出显示文本 - 以编程方式">}}


## .NET API 在 PDF 中突出显示 {#highlight-pdf-dotnet-api}

[GroupDocs.Annotation][3] 提供 .NET API，允许在 .NET 应用程序内的文档中操作注释及其自动化。在本文的示例中，我正在使用此 API 突出显示 PDF 文件中的文本。

您可以从 [下载部分][4] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][5] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Annotation
```

## 使用 C# 在 PDF 中突出显示 {#how-to-highlight-pdf}

以下是从 .NET 应用程序中突出显示 PDF 中的文本或任何区域的步骤。

* 使用 [Annotator][6] 类加载源 PDF 文档。
* 创建 [HighlightAnnotation][7] 对象。
* 定义高亮属性，如颜色、不透明度、页码和点。
* 使用 [Add][8] 方法将定义的突出显示添加到加载的 PDF 文档中。
* 使用 [Save][9] 方法保存带注释的 PDF。

**注意：** 您可以更改高亮颜色、不透明度和其他属性。

以下代码示例展示了如何使用 C# 以编程方式突出显示 PDF 中的文本。

```
// 在 C# 中使用突出显示注释突出显示 PDF
using (Annotator annotator = new Annotator(@"path/sample.pdf"))
{
    HighlightAnnotation highlight = new HighlightAnnotation
    {
        BackgroundColor = 0xFFF000,
        CreatedOn = DateTime.Now,
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(120, 270),
            new Point(600, 270),
            new Point(120, 300),
            new Point(600, 300)
        }
    };
    annotator.Add(highlight);
    annotator.Save(@"path/annotation-highlight.pdf");
}
```

以下是上述代码的输出。



{{< figure align=center src="images/highlight-annotation-in-pdf-using-groupdocs.jpg" alt="在 PDF 中突出显示文本 - 以编程方式">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][10] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们学习了如何使用 C# 以编程方式在 PDF 文件中添加高亮注释。此外，我们可以更改高亮颜色、不透明度和其他属性。许多[不同类型的注释][11] 可以使用相同的 API 以类似的方式添加。

要了解 API，请访问 [文档][12]。如有疑问，请通过 [论坛][13] 联系我们。

## 也可以看看

* [使用C#给PDF文件加水印][14]
* [使用 C# 为图像添加水印][15]
* [使用 C# 添加或删除注释或标记 Word 文件][16]







[1]: #highlight-pdf-dotnet-api
[2]: #how-to-highlight-pdf
[3]: https://products.groupdocs.com/annotation/
[4]: https://downloads.groupdocs.com/annotation
[5]: https://www.nuget.org/packages/groupdocs.annotation
[6]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[7]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/highlightannotation
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[15]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[16]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/


