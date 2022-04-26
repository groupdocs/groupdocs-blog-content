---
title: "使用 C# 在 Word、PDF 和其他文档中添加波浪下划线"
date: Sat, 04 Dec 2021 15:37:01 +0000
draft: false
url: /zh/2021/12/04/add-wavy-underline-in-documents-using-csharp/
author: 'Shoaib Khan'
summary: "波浪线下划线通常用于显示文档中的不一致。我们对这些行非常熟悉，因为 Microsoft Word 使用红色波浪下划线表示拼写错误，使用蓝色波浪/波浪下划线表示格式问题。我们还可以通过编程在文档中添加这样的下划线注释。在本文中，我们将学习**如何使用 C# 在 Word、PDF、PPT 和其他文档中添加波浪下划线**。"
tags: ['Annotation in CSharp', 'Squiggly Annotation in CSharp', 'Squiggly Underline in Word', 'Wavy Underline in CSharp', 'Wavy Underline in Word']
categories: ['GroupDocs.Annotation Product Family']
---

波浪线下划线通常用于显示文档中的不一致。我们对这些行非常熟悉，因为 Microsoft Word 使用红色波浪下划线表示拼写错误，使用蓝色波浪/波浪下划线表示格式问题。我们还可以以编程方式在文档中添加这样的下划线注释。在本文中，我们将学习**如何使用 C# 在 Word、PDF、PPT 和其他文档中添加波浪下划线**。



{{< figure align=center src="images/adding-squiggly-annotation.jpg" alt="向文档添加 Squiggly 注释">}}


下面讨论以下主题：

* [.NET API 用于波浪下划线 / Squiggly 注释][1]
* [在Word文档中为文本添加波浪下划线-波浪注释][2]
* [为PDF、PPT等文档中的文本添加波浪下划线][3]

## 用于波浪下划线的 .NET API - Squiggly 注释 {#wavy-underline-dotnet-api}

[GroupDocs.Annotation][4] 提供了注释解决方案，允许在 .NET 应用程序中对文档中的各种注释类型进行操作和自动化。我们将使用其 [GroupDocs.Annotation for .NET][5] API 在使用 C# 的文档中添加波浪形注释。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Annotation
```

## 使用 C# 为 Word (DOC/DOCX) 中的文本添加波浪下划线 - Squiggly Annotation {#add-wavy-underline-in-word}

以下步骤显示了如何使用 C# 在 Word 文档中插入波浪下划线。

* **使用 [Annotator][8] 类加载** Word（DOC、DOCX）。
* **使用 [SquigglyAnnotation][9] 类创建波浪下划线**。
* **个性化**通过设置其颜色、不透明度、坐标、页码等来设置波浪下划线。
* [**Add**][10] 对注释器的波浪形注释。
* **保存**使用 [Save()][11] 方法更新的 Word 文件。

以下 C# 代码示例将波浪下划线添加到 Word 文档的选定文本。

```
/*
 * Add wavy underline (Squiggly Annotation) to text in DOC, DOCX files using C#
 */
using (Annotator annotator = new Annotator("path/document.docx"))
{
    SquigglyAnnotation squiggly = new SquigglyAnnotation
    {
        BackgroundColor = 0xFFF000,
        FontColor = 0xFF0000,
        Message = "This is Squiggly Annotation",
        CreatedOn = DateTime.Now,
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(20, 170),
            new Point(290, 170),
            new Point(20, 200),
            new Point(290, 200)
        }
    };
    annotator.Add(squiggly);
    annotator.Save("path/squiggly-document.docx");
}
```

您可以从各种 [AnnotationModels][12] 添加任何其他注释类型。

## 使用 C# 为 PDF、PPT 和其他文档中的文本添加波浪下划线 {#wavy-underline-in-pdf-ppt-etc}

同样，您可以使用相同的 C# 代码将波浪形下划线添加到任何文档（如果 API 支持您的预期文档文件格式，请检查文档）。

以下是如何使用 C# 在 PDF 文档中插入波浪下划线的步骤。

* **使用 [Annotator][13] 类加载** PDF 文档。
* **使用 [SquigglyAnnotation][14] 类创建波浪下划线**。
* **自定义**波浪/波浪下划线的颜色、不透明度、坐标、页码等。
* **使用 [Add()][15] 方法将波浪形注释添加到注释器。
* **保存**使用 [Save()][16] 方法更新的 PDF 文件。

以下 C# 代码示例将波浪下划线添加到 PDF 文件的选定文本。

```
/*
 * Add wavy underline (Squiggly Annotation) to text in PDF file using C#
 */
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    SquigglyAnnotation squiggly = new SquigglyAnnotation
    {
        FontColor = 0xFF0000,
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(20, 100),
            new Point(150, 100),
            new Point(20, 130),
            new Point(150, 130)
        }
    };
    annotator.Add(squiggly);
    annotator.Save("path/squiggly-document.pdf");
}
```

## 结论

综上所述，我们讨论了如何使用 C# 在 Word 文档中添加波浪/波浪下划线。此外，可以将相同的波浪注释添加到其他文档，如 PDF、PPT 等。 Squiggly 注释是 [API 提供的许多其他注释类型][17] 的新增功能。

详细了解 **GroupDocs.Annotation for .NET**。访问它的[文档][18]，开始为各种[支持的文档格式][19]构建您自己的文档注释应用程序。如有疑问，请通过 [论坛][20] 联系我们。

## 也可以看看

* [使用 C# 添加或删除注释或标记 Word 文件][21]
* [使用 Java 在 PDF 文件中添加或删除注释][22]







[1]: #wavy-underline-dotnet-api
[2]: #add-wavy-underline-in-word
[3]: #wavy-underline-in-pdf-ppt-etc
[4]: https://products.groupdocs.com/annotation/
[5]: https://products.groupdocs.com/annotation/net/
[6]: https://downloads.groupdocs.com/annotation
[7]: https://www.nuget.org/packages/groupdocs.annotation
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation
[15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[18]: https://docs.groupdocs.com/annotation/net
[19]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[20]: https://forum.groupdocs.com/
[21]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/
[22]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/


