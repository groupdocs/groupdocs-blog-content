---
title: "'使用 C# 从 PDF 或 Word 文档中删除注释'"
date: Thu, 27 Jan 2022 14:29:00 +0000
draft: false
url: /zh/2022/01/27/remove-annotations-from-pdf-or-word-documents-using-csharp/
author: 'Shoaib Khan'
summary: 'Annotations are commonly used in documents for pointing out different observations and providing feedbacks for discussion. We discussed in a separate articles, [how to add different annotations to PDF](https://blog.groupdocs.com/2022/01/25/annotate-pdf-files-using-csharp) and [Word documents](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/) using C#. Today, this article discuss **how to remove annotations from documents like PDF and Word DOC/DOCX files using C#**.

本文讨论了以下主题：

* 注释 .NET API
* 删除所有注释
* 按 ID 删除注释
* 通过注释对象消除注释'
tags: ['Remove Annotation from PDF in CSharp', 'Remove Annotation in CSharp', 'Remove Annotations', 'Remove Annotations from Word in C#']
categories: ['GroupDocs.Annotation Product Family']
---

注释通常用于文档中，用于指出不同的观察结果并为讨论提供反馈。我们在单独的文章中讨论了如何使用 C# 向 PDF 和 Word 文档添加不同的注释。今天，本文讨论**如何使用 C#** 从 PDF 和 Word DOCX 文件等文档中删除注释。

下面讨论以下主题：

* [注释 .NET API](#dotnet-annotation-api)
* [删除所有注释](#remove-all-annotations)
* [按 ID 删除注释](#remove-annotation-by-id)
* [通过注解对象消除注解](#remove-annotations-by-obj)

## 用于注解的 .NET API {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) 提供 .NET API 来处理各种文档和图像中的注释。它允许从 PDF、Word 和许多其他文档中添加、删除和提取注释。您可以查看文档以获取 [支持的注释文档格式](https://docs.groupdocs.com/annotation/net/supported-document-formats/) 的完整列表。

从 [下载部分](https://downloads.groupdocs.com/annotation) 下载其 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.annotation)。您也可以使用包管理器中的以下命令。

```
PM> Install-Package GroupDocs.Annotation
```

## 使用 C# 从 PDF、Word 文档中删除所有注释 {#remove-all-annotations}

有多种方法可以从文档中删除注释。您可以一次删除所有注释，通过提供 ID 删除特定注释，或通过注释对象删除特定注释。有关更多选项，请访问 [文档](https://docs.groupdocs.com/annotation/net/remove-annotation-from-document/) 文章。

以下是使用 C# 从 PDF 或 Word DOC/DOCX 文档中删除所有注释的步骤。

* 使用 [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) 加载文档。
* 初始化[保存选项](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions) 类。
* 将注释类型设置为**无**。
* 使用 [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) 方法保存文件，无需注释。

以下代码显示如何使用 C# 从 PDF 或 Word 文件中删除注释。

```
// 使用 C# 从 PDF 文档中删除所有注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Save("path/document-noAnnotation.pdf", new SaveOptions {AnnotationTypes = AnnotationType.None});
}
```

## 使用 C# 按 ID 删除注释 {#remove-annotation-by-id}

同样，您可以提供注释 ID 以从文档中消除这些注释。只需提供 ID 或 ID 列表即可摆脱指定的注释。以下代码显示如何通过使用 C# 提供 ID 从 PDF 或 Word 文档中删除注释。

```
// 使用 C# 从 PDF 文档中按 ID 删除注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Remove(new List<int>{0,1});
    annotator.Save("path/document-remove-annotation.pdf");
}
```

## 使用 C# 通过注释对象删除注释 {#remove-annotations-by-obj}

您还可以通过证明 Annotation 对象来摆脱特定的注释。为了说明这一点，以下代码示例使用 C# 中的注释对象从 PDF 或 Word 文档中删除注释。

```
// 使用 C# 从 PDF 文档中删除选择性注释
using (Annotator annotator = new Annotator("path/document.pdf"))
{
    annotator.Remove(annotator.Get()[0]);
    annotator.Save("path/document-remove-annotation.pdf");
}
```

## 结论

最后，您已经学习了如何使用 C# 从文档中删除注释。具体来说，我们从 PDF 和 Word 文件中删除了所有注释。后来我们通过提供 ID 和证明注释对象来删除注释。

使用 **GroupDocs.Annotation for .NET** 构建您自己的文档注释移除器 .NET 应用程序。从 [文档](https://docs.groupdocs.com/annotation/net/) 和 [GitHub](https://github.com/groupdocs-annotation) 存储库了解有关 API 的更多信息。如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/) 上的支持人员。

## 也可以看看

* [使用 C# 注释或标记 PDF 文件](https://blog.groupdocs.com/2022/01/25/annotate-pdf-files-using-csharp/)
* [使用 C# 注释或标记 Word 文件](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)
* [在 C# 中使用注释突出显示 PDF](https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/)
* [使用 C# 中的注释在 PDF 中创建超链接](https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/)





