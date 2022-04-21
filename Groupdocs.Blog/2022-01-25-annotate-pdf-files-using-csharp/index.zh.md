---
title: "'使用 C# 添加或删除注释或标记 PDF 文件'"
date: Tue, 25 Jan 2022 14:15:00 +0000
draft: false
url: /zh/2022/01/25/annotate-pdf-files-using-csharp/
author: 'Shoaib Khan'
summary: 'No more long discussions within long email threads on the content of the document(s). You can use annotations to markup documents with personalized messages and their replies. This article discussed **how to programmatically annotate PDF files to markup documents using C#**. Additionally, we will also discuss how to remove annotations from PDF files.

本文讨论了以下主题：

* .NET API 注释 PDF 文件
* 为 PDF 添加注释
    * 箭头注释
    * 矩形注释
    * 椭圆或椭圆注释
    * 距离注释
* 从 PDF 文件中删除注释'
tags: ['Add annotations in PDF', 'add annotations in PDF using csharp', 'annotate PDF', 'Annotate PDF in CSharp']
categories: ['GroupDocs.Annotation Product Family']
---

不再在长电子邮件线程中就文档内容进行长时间讨论。您可以使用注释来标记带有个性化消息及其回复的文档。本文讨论**如何使用 C# 以编程方式注释 PDF 文件以标记文档**。此外，我们还将讨论如何从 PDF 文件中删除注释。

下面将简要讨论以下主题：

* [.NET API 注释 PDF 文件](#dotnet-annotation-api)
* [为 PDF 添加注释](#add-annotations-to-pdf)
    * [箭头注释](#add-arrow-annotation)
    * [矩形注释](#add-area-annotation)
    * [椭圆或椭圆注释](#add-ellipse-annotation)
    * [距离注释](#add-distance-annotation)
* [从 PDF 文件中删除注释](#remove-annotations)

## .NET API 注释 PDF 文件 {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) 有它的 .NET API 来处理文档和图像中的注释。它允许您从 PDF 和 Word 文档、电子表格和演示文稿中添加、删除和提取注释。此外，它还支持图像、网页、电子邮件、Visio 绘图等等。您可以查看文档以获取 [支持的注释文档格式](https://docs.groupdocs.com/annotation/net/supported-document-formats/) 的完整列表。

从 [下载部分](https://downloads.groupdocs.com/annotation) 下载其 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.annotation)。您也可以使用包管理器中的以下命令。

```
PM> Install-Package GroupDocs.Annotation
```

## 使用 C# 向 PDF 添加注释 {#add-annotations-to-pdf}

可以在文档中添加许多不同类型的注释，但是，我们将在本文中仅讨论其中的几个。



{{< figure align=center src="images/added-annotations-to-pdf.jpg" alt="为 PDF 添加注释">}}


以下是一些受支持的注释。您可以[单独了解每个注释](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/)。

<figure class="wp-block-table is-style-regular"><table><tbody><tr><td>- 区域/矩形注释<br>- 箭<br>- 距离<br>- 椭圆<br>- 强调<br>- 关联<br>- 观点<br>- 折线</td><td>- 替换<br>- 资源编辑<br>- 三振出局<br>- 文本域<br>- 文本编辑<br>- 下划线<br>- 水印</td></tr></tbody></table></figure>

## 使用 C# 将箭头注释添加到 PDF {#add-arrow-annotation}

以下是如何在 C# 中为 PDF 文档添加箭头注释的步骤。



{{< figure align=center src="images/arrow-annotation.jpg" alt="在 Java 和 C# .NET 中以编程方式添加箭头注释">}}


* 使用 [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) 类加载 PDF 文档。
* 初始化[Arrow Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation)。
* 定义箭头标注的位置、大小、页码。
* 使用 [Add](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index) 方法添加定义的箭头注释。
* 使用适当的 [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) 方法保存带注释的文档。

以下 C# 代码示例展示了如何向 PDF 文档添加箭头注释。

```
// 使用 C# 向 PDF 文档添加箭头注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(100, 100, 50, 50),

        // optional --
        CreatedOn = DateTime.Now,
        Message = "Your Message",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -3407872,
        PenStyle = PenStyle.Solid,
        PenWidth = 2
    };
    annotator.Add(arrow);
    annotator.Save("path/annotation.pdf");
}
```

## 使用 C# 在 PDF 中插入矩形或区域注释 {#add-area-annotation}

以下是通过一些自定义将矩形或区域注释添加到 PDF 文档的步骤。它与添加箭头注释非常相似，但使用 **AreaAnnotation**。

* 使用 [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) 类加载 PDF 文档。
* 使用 [AreaAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation) 类初始化矩形注释。
* 指定矩形的位置、大小和颜色。
* 您还可以设置其他属性，如**页码、背景、不透明度、样式、笔宽**、**消息**和**时间**。
* 将定义好的矩形注解添加到注解器中。
* 最后，使用 [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) 方法保存带注释的文件。



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加矩形或区域注释">}}


以下代码示例使用 C# 将矩形/区域注释添加到 PDF 文档。

```
// 使用 C# 在 PDF 文档中添加区域或矩形注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    AreaAnnotation area = new AreaAnnotation
    {
        BackgroundColor = 65535,
        Box = new Rectangle(80, 75, 450, 135),
        Message = "This is area annotation",
        Opacity = 0.2,
        PageNumber = 0,
        PenColor = -131,
        PenStyle = PenStyle.Dash,
        PenWidth = 3
    };
    annotator.Add(area);
    annotator.Save("path/annotation.pdf");
}
```

## 使用 C# 向 PDF 添加椭圆或椭圆注释 {#add-ellipse-annotation}

同样，让我们添加椭圆/椭圆注释。以下步骤显示了如何使用 C# 将椭圆注释或椭圆注释添加到 PDF 文件。



{{< figure align=center src="images/ellipses-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加椭圆或椭圆注释">}}


* 使用 [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) 类加载 PDF 文件。
* 初始化[Ellipse Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation)。
* 设置初始化注解的位置、大小等属性。
* 将创建的椭圆注释添加到 Annotator 对象中。
* 使用 [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) 方法保存带注释的 PDF 文件。

以下 C# 代码示例将椭圆/椭圆注释添加到 PDF 文档。

```
// 使用 C# 在 PDF 文档中添加椭圆或椭圆注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    EllipseAnnotation ellipse = new EllipseAnnotation
    {
        BackgroundColor = -16034924,
        Box = new Rectangle(275, 475, 300, 80),
        Message = "This is ellipse annotation",
        Opacity = 0.2,
        PageNumber = 0,
        PenColor = -16034924,
        PenStyle = PenStyle.Dot,
        PenWidth = 3
    };
    annotator.Add(ellipse);
    annotator.Save("path/annotation.pdf");
}
```

## 使用 C# 将距离注释插入 PDF {#add-distance-annotation}

您可以使用距离注释来指出两个对象之间的距离。以下是使用 C# 向 PDF 文档添加距离注释的步骤。



{{< figure align=center src="images/distance-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加距离注释">}}


* 使用 [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) 类加载 PDF 文档后，使用 [DistanceAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation) 类。
* 设置外观、线条颜色、粗细、样式等。
* 将距离注释添加到注释器中。
* 使用适当的 [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) 方法保存带有注释的 PDF 文件。

以下代码片段显示了如何使用 C# 在 PDF 中添加距离注释。

```
// 使用 C# 向 PDF 文档添加距离注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    DistanceAnnotation distance = new DistanceAnnotation
    {
        Box = new Rectangle(750, 235, 0, 150),
        Message = "This is the heading area",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -21197,
        PenStyle = PenStyle.Solid,
        PenWidth = 3
    };
    annotator.Add(distance);
    annotator.Save("path/annotation.pdf");
}
```

## 使用 C# 从 PDF 文件中删除注释 {#remove-annotations}

有多种方法可以从 PDF 文档中删除注释。或者，您可以一次删除所有注释，或者您可以提供 ID、索引来删除选择性注释。我们在另一篇文章中讨论了[删除注释的不同方式](https://blog.groupdocs.com/2022/01/27/remove-annotations-from-pdf-or-word-documents-using-csharp)。但是，以下是从 PDF 文件中删除所有注释的步骤。

* 加载文档。
* 初始化[保存选项](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions)。
* 将注释类型设置为**无**。
* 使用 [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) 方法保存无注释 PDF 文件。

以下 C# 代码显示了如何从 PDF 文件中删除注释。

```
// 使用 C# 从 PDF 文档中删除所有注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Save("path/document-noAnnotation.pdf", new SaveOptions {AnnotationTypes = AnnotationType.None});
}
```

## 结论

最后，您学习了如何使用 C# 在 .NET 应用程序中向 PDF 文档添加不同的注释。更准确地说，我们添加了箭头、椭圆、面积和距离注释。此外，您还看到了从任何 PDF 文件中删除所有注释的方法之一。

您可以考虑构建自己的文档注释器 .NET 应用程序。有关 **GroupDocs.Annotation for .NET** 的更多信息，请访问 [文档](https://docs.groupdocs.com/annotation/net/) 和 [GitHub](https://github.com/groupdocs-annotation) 存储库。如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/) 上的支持人员。

## 也可以看看

* [使用 C# 中的注释在 PDF 中创建超链接](https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/)
* [在 C# 中使用注释突出显示 PDF](https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/)
* [使用 C# 添加或删除注释或标记 Word 文件](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)