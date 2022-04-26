---
title: "使用 C# 将多个文件类型合并到单个文档中"
date: Tue, 04 May 2021 20:10:39 +0000
draft: false
url: /zh/2021/05/04/merge-multiple-file-types-using-csharp/
author: 'Shoaib Khan'
summary: 'To combine the data that is present in multiple documents, and sometimes in documents of different file types, there comes the need to merge all your documents or the portion of the documents into one. In this article, you will learn, how to merge multiple documents of either the same or different file types in one file using C#.

以下是本文涵盖的主题：

* .NET API - 合并多种文档类型
* 将 PDF、Word、Excel 文件合并为一个 PDF
* 将多个文件的选择性页面合并为一个文件

[继续阅读...][1]'
tags: ['Merge Documents in CSharp', 'Merge Files in CSharp', 'Merge multiple file types in CSharp', 'merge two or more files']
categories: ['GroupDocs.Merger Product Family']
---

要合并多个文档中存在的数据，有时是不同文件类型的文档中的数据，需要将所有文档或文档的一部分合并为一个。在本文中，您将学习如何使用 C# 以编程方式将相同或不同文件类型的多个文档合并到一个文件中。



{{< figure align=center src="images/merged-pdf-word-excel-files-to-pdf-in-csharp.jpg" alt="在 C# 中将 PDF Word Excel 演示文稿合并为一个 PDF">}}


以下是以下涵盖的主题：

* [.NET API - 合并多种文档类型][2]
* [将 PDF、Word、Excel 文件合并为一个 PDF][3]
* [将多个文件的选择性页面合并为一个文件][4]

## .NET API 用于合并多种文档类型 {#dotnet-api-to-merge-multiple-file-types}

今天，我将使用 GroupDocs.Merger for .NET 将不同文件格式的文档合并到一个文件中。 .NET API 允许将相同或不同格式的各种文档合并到一个文件中。此外，它还允许文档拆分、修剪文档以及交换、移动、删除、旋转或排列页面。此外，它还支持设置或删除密码以管理 [支持的文档格式][5] 的安全性。

API 支持的一些文档类型包括：文字处理文档、电子表格、演示文稿、HTML、PDF、电子书、Visio 绘图、CSV 和 TSV。

从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 在 C# 中将 PDF、Word、Excel 文件合并为一个 PDF {#merge-multiple-files-into-one-pdf-in-csharp}

只需几行代码，您就可以将 PDF 文档与 Word 文档、演示文稿和 Excel 电子表格相结合。以下是如何将多种文件类型的文档合并为一个文件的步骤。

* 使用 [Merger][8] 类加载源文档。
* 使用 [Join][9] 方法继续合并其他文档。
* 使用 [Save][10] 方法将合并后的文档保存为输出。

以下源代码展示了如何在 C# 中将 PDF、Word 和 Excel 文档合并为一个 PDF 文件。

```
// 使用 C# 将两种或多种不同类型的文件合并为一个
using (Merger merger = new Merger("document.pdf"))
{
    merger.Join("document.docx");
    merger.Join("spreadsheet.xlsx");
    merger.Save("merge_document.pdf");
}
```

同样，您也可以合并相同文件格式的文件。下面说的是加入word文档、PDF文档得到的输出。以及使用上述 C# 代码的电子表格。



{{< figure align=center src="images/merged-pdf-word-excel-to-one-file.jpg" alt="将不同的文件类型合并为一个 PDF C#">}}


## 在 C# 中将多个 PDF、Word、Excel 文件的选择性页面合并为一个 PDF {#merge-selective-pages-of-multiple-files-into-one-pdf-in-csharp}



{{< figure align=center src="images/merged-selective-pages-of-pdf-word-excel-to-one-file.jpg" alt="将不同文件类型的选择性页面合并为一个 PDF C#">}}


并非总是希望合并整个文档。您可能想从一个文档中选择几页，从下一个文档中选择一些其他页面，依此类推。 API 提供了将多种文件类型的选择性页面合并到一个文件中的不同方法。

* 使用 [Merger][11] 类加载源文档。
* 使用 [JoinOptions][12] 类设置合并选项。
* 使用 [Join][13] 方法合并文档。
* 通过为每个文档设置不同的连接选项来继续组合文档。
* 使用[Save][14]方法保存合并后的文档。

以下源代码显示了如何使用 C# 将 PDF 文件与 Word 文档的第一页以及提供范围内的 Excel 工作簿的偶数表合并为单个 PDF 文件。

```
// 使用 C# 将两种或多种不同类型文件的选择性页面合并为一个
using (Merger merger = new Merger("document.pdf"))
{
    // Merge first page of DOCX file
    JoinOptions joinOptions = new JoinOptions(new int[] {1});
    merger.Join("document.docx", joinOptions);
    
    // Merge all the even pages/sheets of the spreadsheet from the provided range
    joinOptions = new JoinOptions(1,2, RangeMode.EvenPages);
    merger.Join("spreadsheet.xlsx", joinOptions);

    merger.Save("merge_document.pdf");
}
```

## 结论

总而言之，您已经了解了如何在 .NET 应用程序中使用 C# 将两个或多个不同文件类型的文档合并到一个文件中。此外，您还学习了如何仅组合多种文件类型的选择性页面。

您可以使用 [documentation][15] 了解有关 .NET 的 GroupDocs.Merger 的更多信息。如果您有任何疑问，请通过我们的 [论坛][16] 告诉我们。

## 也可以看看

* [在C#中合并相同格式的文档][17]
* [在 Java 中拆分或合并文档][18]







[1]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[2]: #dotnet-api-to-merge-multiple-file-types
[3]: #merge-multiple-files-into-one-pdf-in-csharp
[4]: #merge-selective-pages-of-multiple-files-into-one-pdf-in-csharp
[5]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/merger/net
[7]: https://www.nuget.org/packages/groupdocs.merger
[8]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[9]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/joinoptions
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[15]: https://docs.groupdocs.com/merger/net
[16]: https://forum.groupdocs.com/
[17]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[18]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/


