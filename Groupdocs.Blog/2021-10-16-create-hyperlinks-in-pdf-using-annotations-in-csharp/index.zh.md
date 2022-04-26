---
title: "使用 C# 中的注释在 PDF 中创建超链接"
date: Sat, 16 Oct 2021 01:00:00 +0000
draft: false
url: /zh/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/
author: 'Shoaib Khan'
summary: "超链接通常用于将外部数据关联到文档的任何指定区域。我们可以使用链接注释将文档的任何部分转换为超链接。作为程序员，您可以将这些链接注释添加到您的 .NET 应用程序中的文档中。在本文中，我们将讨论**如何使用 C# 在 PDF 文件中创建超链接**。"
tags: ['annotate PDF', 'Annotate PDF in CSharp', 'Create Hyperlink in PDF', 'Link Annotation', 'Link Annotation in CSharp', 'Link Annotation in PDF']
categories: ['GroupDocs.Annotation Product Family']
---

超链接通常用于将外部数据关联到文档的任何指定区域。我们可以使用链接注释将文档的任何部分转换为超链接。作为程序员，您可以将这些链接注释添加到您的 .NET 应用程序中的文档中。在本文中，我们将讨论**如何使用 C# 在 PDF 文件中创建超链接**。

以下主题涵盖以下内容：

* [.NET API 在 PDF 文件中添加超链接][1]
* [如何以编程方式在 PDF 中创建超链接][2]



{{< figure align=center src="images/add-link-annotation-in-pdf-using-groupdocs.jpg" alt="在 PDF 中创建链接 - 以编程方式">}}


## .NET API 在 PDF 中创建超链接 {#hyperlink-dotnet-api}

[GroupDocs.Annotation][3] 为不同类型的应用程序提供注释解决方案。它的 .NET API 允许在您的 .NET 应用程序中对文档中的各种注释进行操作和自动化。我们将使用其 [GroupDocs.Annotation for .NET][4] API 使用 C# 在 PDF 文件中创建超链接注释。

您可以从 [下载部分][5] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Annotation
```

## 使用 C# 在 PDF 中创建超链接 {#how-to-create-hyperlink-annotations}

以下是使用 C# 在 PDF 文件中的任意位置创建超链接的步骤。

* 使用 [Annotator][7] 类加载源 PDF 文档。
* 创建 [Link Annotation][8] 对象。
* 定义超链接属性，如 url、页码、点等。
* 使用 [Add][9] 方法将定义的超链接添加到加载的 PDF 文档。
* 使用 [Save][10] 方法保存带注释的 PDF。

以下代码示例展示了如何使用 C# 将 PDF 文件的任何部分转换为超链接。

```
// 使用 C# 中的链接注释在 PDF 中创建超链接
using (Annotator annotator = new Annotator(@"path/sample.pdf"))
{
    LinkAnnotation link = new LinkAnnotation
    {
        CreatedOn = DateTime.Now,
        PageNumber = 0,
        Points = new List<Point>
        {
            new Point(120, 300),
            new Point(600, 300),
            new Point(120, 270),
            new Point(600, 270)
        },
        Url = @"https://products.groupdocs.com/annotation"
    };
    annotator.Add(link);
    annotator.Save(@"path/annotation-link.pdf");
}
```

以下是上述代码的输出。



{{< figure align=center src="images/link-annotation-in-pdf-using-groupdocs.jpg" alt="在 PDF 中创建链接 - 以编程方式">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][11] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您已经了解了如何添加链接注释以使用 C# 在 PDF 文件中创建超链接。同样，使用链接注释，您可以将文档的任何部分转换为超链接。许多其他 [注释类型][12] 也可以使用相同的 API 以类似的方式添加。通过访问 [文档][13] 进一步了解 API。如有疑问，请通过 [论坛][14] 联系我们。

## 也可以看看

* [使用 C# 给 PDF 文件加水印][15]
* [使用 C# 为图像添加水印][16]
* [在 C# 中使用注释突出显示 PDF][17]
* [使用 C# 添加或删除注释或标记 Word 文件][18]







[1]: #hyperlink-dotnet-api
[2]: #how-to-create-hyperlink-annotations
[3]: https://products.groupdocs.com/annotation/
[4]: https://products.groupdocs.com/annotation/net/
[5]: https://downloads.groupdocs.com/annotation
[6]: https://www.nuget.org/packages/groupdocs.annotation
[7]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[13]: https://docs.groupdocs.com/redaction
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[16]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[17]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[18]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/


