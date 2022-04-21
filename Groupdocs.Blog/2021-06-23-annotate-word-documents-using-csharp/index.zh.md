---
title: "使用 C# 添加或删除注释或标记 Word 文件"
date: Wed, 23 Jun 2021 11:23:00 +0000
draft: false
url: /zh/2021/06/23/annotate-word-documents-using-csharp/
aliases:
- /2021/06/24/annotate-documents-programmatically-using-groupdocs.annotation-for-.net/
- /2019/10/14/annotate-documents-programmatically-using-groupdocs.annotation-for-.net/
author: 'Shoaib Khan'
summary: "Forget to discuss documents content and feedbacks in long email threads. Simply use annotations to markup documents with messages and replies. In this article, you will learn how to programmatically add and remove annotations to markup Word documents in C# with your .NET applications."
tags: ['Add Annotations in Word using CSharp', 'Annotate Word in CSharp', 'Remove Annotations from Word in C#']
categories: ['GroupDocs.Annotation Product Family']
---

忘记在长电子邮件线程中讨论文档的内容和反馈。只需使用注释来标记带有消息和回复的文档。在本文中，您将学习如何使用 .NET 应用程序以编程方式添加和删除注释以标记 C# 中的 Word 文档。

以下是以下简要讨论的主题：

* [.NET API for Word DOC/DOCX Annotations][1]
* [为Word添加注释][2]
    * [箭头注释][3]
    * [矩形注释][4]
    * [椭圆或椭圆注释][5]
    * [距离注释][6]
* [从 Word 文件中删除注释][7]

## .NET API 用于注释和标记 Word 文件 {#dotnet-annotation-api}

[GroupDocs.Annotation][8] 提供 .NET API 来处理 .NET 应用程序中文档和图像的注释。该 API 允许您从 Word 文档中添加、删除和提取注释。此外，它还支持电子表格、演示文稿、图像、PDF 文件、网页、电子邮件、Visio 绘图。一些 AutoCAD 绘图和 DICOM 等数字成像格式也在列表中。有关 [注释支持的文档格式][9] 的完整列表，您可以访问文档。

从 [下载部分][10] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][11] 在您的 .NET 应用程序中安装 API。您也可以使用包管理器中的以下命令。

```
PM> Install-Package GroupDocs.Annotation
```

## 在 C# 中为 Word 添加注释 {#add-annotations-to-word}

让我们在 Word 文档中添加一些不同类型的注释。有许多不同类型的注释，因此我们将在本文中仅介绍其中的几个。



{{< figure align=center src="images/add-annotations-to-doc-docx-using-groupdocs-dotnet-java-api-1024x624.png" alt="使用 GroupDocs API 向 DOC DOCX 添加注释">}}


有一些受支持的注释类型，您可以[单独了解每个注释][12]。

* 面积/矩形标注
* 箭
* 下划线
* 水印
* 距离
* 三振出局
* 文本域
* 椭圆
* 强调
* 关联
* 观点
* 折线
* 替换
* 资源编辑
*文本编辑

## 使用 C# 在 Word 中添加箭头注释 {#add-arrow-annotation}

以下是在 C# 中向 Word 文档添加箭头注释的步骤。



{{< figure align=center src="images/arrow-annotation.jpg" alt="在 Java 和 .NET 中以编程方式添加箭头注释">}}


* 使用 [Annotator][13] 类加载文档。
* 使用 [ArrowAnnotation][14] 类初始化箭头注释。
* 调整箭头标注的位置、大小、页码。
* 使用 [Add][15] 方法添加创建的箭头注释。
* 使用[Save][16]方法将带注释的Word文档保存到路径中。

以下代码示例演示如何使用 C# 向 Word 文档添加箭头注释。

```
// 使用 C# 向 Word 文档添加箭头注释
using (Annotator annotator = new Annotator("path/document.docx"))
{
    ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(100, 100, 50, 50),
        CreatedOn = DateTime.Now,
        Message = "Your Message",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -3407872,
        PenStyle = PenStyle.Solid,
        PenWidth = 2
    };
    annotator.Add(arrow);
    annotator.Save("path/annotation.docx");
}
```

## 使用 C# 在 Word 中插入矩形或区域注释 {#add-area-annotation}

可以在将任何注释添加到文档时对其进行自定义。以下是通过一些自定义将矩形或区域注释添加到 DOC/DOCX 文档的步骤。它与添加箭头注释非常相似，但这次使用 **AreaAnnotation** 类。

* 使用 [Annotator][17] 类加载 DOC/DOCX 文档。
* 使用 [AreaAnnotation][18] 类初始化矩形标注。
* 调整矩形的位置、大小和颜色。
* 设置其他属性，如**页码、背景、不透明度、样式、笔宽**、**消息**和**时间**。
* 将创建的矩形注解添加到 Annotator。
* 使用[Save][19]方法将注释文件保存到路径。



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="在 .NET 和 Java 中以编程方式添加矩形或区域注释">}}


以下代码示例展示了如何使用 C# 向 Word 文档添加矩形/区域注释。

```
// 使用 C# 在 Word 文档中添加区域或矩形注释
using (Annotator annotator = new Annotator("path/document.docx"))
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
    annotator.Save("path/annotation.docx");
}
```

## 使用 C# 在 Word 中添加椭圆或椭圆注释 {#add-ellipse-annotation}

以下是在 C# 中向文档添加椭圆注释或椭圆注释的步骤。



{{< figure align=center src="images/ellipses-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加椭圆或椭圆注释">}}


* 使用 [Annotator][20] 类加载 DOC/DOCX 文档。
* 使用 [EllipseAnnotation][21] 类初始化椭圆注释。
* 设置初始化椭圆标注的位置和大小。
* 将创建的椭圆注释添加到 Annotator 对象中。
* 提供路径并使用[Save][22]方法保存带注释的Word文件。

以下代码示例演示如何使用 C# 向 Word 文档添加椭圆或椭圆注释。

```
// 使用 C# 在 Word 文档中添加椭圆或椭圆注释
using (Annotator annotator = new Annotator("path/document.docx"))
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
    annotator.Save("path/annotation.docx");
}
```

## 使用 C# 在 Word 中插入距离注释 {#add-distance-annotation}

同样，您可以添加距离注释来标记两点之间的距离。以下是向文档添加距离注释的步骤。



{{< figure align=center src="images/distance-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加距离注释">}}


* 加载Word文档后，使用[DistanceAnnotation][23]类初始化距离标注。
* 设置注释的外观。
* 将距离注释添加到 Annotator 对象。
* 通过指定路径将带注释的 Word 文件保存在给定位置。

以下代码示例展示了如何使用 C# 向 DOC/DOCX 文档添加距离注释。

```
// 使用 C# 向 Word 文档添加距离注释
using (Annotator annotator = new Annotator("path/document.docx"))
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
    annotator.Save("path/annotation.docx");
}
```

## 完整代码

总而言之，这里是完整的代码，其输出显示了所有添加的 **annotations** 和 **messages** with **replies**。下面的 C# 代码向 Word 文件添加箭头、矩形、椭圆、距离注释、消息和回复。

```
// 使用 C# 向 Word 添加多个注释
// 使用 C# 向 DOC/DOCX 添加箭头、区域、椭圆（椭圆）、距离注释以及消息和回复
string outputPath = @"outputPath/annotatedDoc.docx";
string inputFile = @"inputPath/document.docx";

using (Annotator annotator = new Annotator(inputFile))
{
    ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(550, 250, 60, -60),
        CreatedOn = DateTime.Now,
        Message = "This image is little upwards.",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = -3407872,
        PenStyle = PenStyle.Solid,
        PenWidth = 2,
        Replies = new List<Reply>
        {
            new Reply
            {
                Comment = "Please look in to these issues.",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                    Comment = "Change Description",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                Comment = "On-Premises APIs",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                Comment = "Add images as well.",
                RepliedOn = DateTime.Now
            }
        }
    };
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
    annotator.Add(arrow);
    annotator.Add(area);
    annotator.Add(ellipse);
    annotator.Add(distance);

    annotator.Save(outputPath);
}
```

## 使用 C# 从 Word DOC/DOCX 文件中删除注释 {#remove-annotations}

可以轻松删除文档中的注释。有许多选项可以从 Word 文档中删除注释。您可以一次删除所有注释。此外，您可以提供索引以删除特定注释。有关更多选项，请访问 [文档][24] 文章。

以下是从 Word 文件中删除所有注释的步骤。

* 加载文档。
* 使用 [SaveOptions][25] 类初始化保存选项。
* 将注释类型设置为无。
* 保存 Word 文件。它将没有注释。

以下代码显示如何使用 C# 从 Word 文件中删除注释。

```
// 使用 C# 从 Word 文档中删除所有注释
using (Annotator annotator = new Annotator(outputPath))
{
    annotator.Save(remOutputPath, new SaveOptions {AnnotationTypes = AnnotationType.None});
}
```

## 结论

简而言之，您已经学习了如何使用 C# 在 .NET 应用程序中向 Word 文档添加注释。具体来说，我们在 Word DOC/DOCX 文件中添加了箭头、椭圆、面积和距离注释。此外，您还了解了如何从任何 Word 文件中删除所有注释。现在，您可以考虑构建自己的文档注释器 .NET 应用程序。

从 [documentation][26] 和 [GitHub][27] 存储库了解有关 GroupDocs.Annotation for .NET 的更多信息。如需进一步查询，请联系 [论坛][28] 上的支持人员。

## 也可以看看

* [使用 C# 为图像添加水印][29]
* [用Java注释PDF文件][30]







[1]: #dotnet-annotation-api
[2]: #add-annotations-to-word
[3]: #add-arrow-annotation
[4]: #add-area-annotation
[5]: #add-ellipse-annotation
[6]: #add-distance-annotation
[7]: #remove-annotations
[8]: https://products.groupdocs.com/annotation/
[9]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[10]: https://downloads.groupdocs.com/annotation
[11]: https://www.nuget.org/packages/groupdocs.annotation
[12]: https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/
[13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation
[15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[18]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation
[19]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[20]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[21]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation
[22]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[23]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation
[24]: https://docs.groupdocs.com/annotation/net/remove-annotation-from-document/
[25]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions
[26]: https://docs.groupdocs.com/annotation/net/
[27]: https://github.com/groupdocs-annotation
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[30]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/


