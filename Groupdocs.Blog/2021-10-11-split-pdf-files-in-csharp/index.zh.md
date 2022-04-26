---
title: "如何使用 C# 拆分 PDF 文件"
date: Mon, 11 Oct 2021 04:14:00 +0000
draft: false
url: /zh/2021/10/11/split-pdf-files-in-csharp/
author: 'Shoaib Khan'
summary: "[PDF][1] 是最常用的文件格式之一，具有高度的可移植性。作为开发人员，您可能遇到过以编程方式拆分大型 PDF 文件的情况。今天，本文讨论了**如何在 .NET 应用程序中使用 C# 拆分 PDF 文件**的不同方法。"
tags: ['PDF Separator', 'Separate PDF', 'Split API', 'Split PDF', 'Split PDF Files', 'Split PDF using C#']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/split-pdf-into-multiple-files-using-csharp.jpg" alt="使用 C# 将 PDF 拆分为多个文件">}}


[PDF][2] 是最常用的文件格式之一，具有高度的可移植性。作为开发人员，您可能遇到过以编程方式拆分大型 PDF 文件的情况。在其中一篇文章中，我们学会了[在 Java 中拆分 PDF 文件][3]。今天，本文讨论了**如何在 .NET 应用程序中使用 C# 拆分 PDF 文件**的不同方法。

* [.NET API 拆分 PDF 文件][4]
* [将PDF拆分为多页文件][5]
* [按范围从PDF文件中提取页面][6]
* [使用偶数或奇数过滤器从 PDF 文件中提取页面][7]
* [将PDF拆分为多个单页文件][8]

## .NET API 拆分 PDF 文件 {#split-pdf-dontet-api}

为了分割 PDF 文件，我们将使用 [GroupDocs.Merger for .NET][9]。它是允许快速开发以很少的代码行集成功能的 API。除了拆分之外，它还支持[合并、交换或修剪不同文件格式的文档][10]。

您可以从 [下载部分][11] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][12] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 使用 C# 将 PDF 文件拆分为多页文件 {#split-pdf-to-multipage}

以下步骤指导如何使用 C# 将 PDF 文件拆分为多页文件：

* 定义输出文件格式。
* 使用 [SplitOptions][13] 定义页面间隔。
* 使用 [Merger][14] 类加载 PDF 文件。
* 使用 [Split()][15] 方法根据定义的间隔拆分加载的 PDF。

以下代码示例显示了如何将 PDF 文件拆分为多页文件。

```
/*
 * Split PDF files into multipage files using C#
 */
// 定义输出文件格式
string filePathOut = "path/splitPDF_{0}.{1}";

// 定义拆分间隔和拆分模式
SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 }, SplitMode.Interval);

// 根据拆分选项加载 PDF 文件和拆分 PDF
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
} 
```

## 按范围从 PDF 文件中提取页面 {#extract-pages-by-range}

以下步骤指导如何使用 C# 通过根据给定范围拆分来从 PDF 中提取页面：

* 定义输出文件格式。
* 使用 [SplitOptions][16] 提供页面范围。
* 使用 [Merger][17] 类加载 PDF 文件。
* 使用 [Split()][18] 方法根据定义的范围分割加载的 PDF。

以下代码片段显示了如何通过提供范围来拆分 PDF 和提取页面。

```
/*
 * Split PDF file by Given Range into Single Page files using C#
 */
// 定义输出文件格式
string filePathOut = "path/splitPDF_{0}.{1}";

// 定义范围以提取为单页文档
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7);

// 根据拆分选项加载 PDF 文件和拆分 PDF
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
}
```

## 使用 C# 从 PDF 文件中提取偶数/奇数页 {#extract-even-or-odd-pages}

以下步骤指导如何通过仅在 C# 中应用过滤器在给定范围内拆分来从 PDF 文件中提取偶数/奇数页：

* 定义输出文件格式。
* 使用 [SplitOptions][19] 提供页面范围。
* 使用 [RangeMode][20] 对偶数、奇数或所有页面应用过滤器。
* 使用 [Merger][21] 类加载 PDF 文件。
* 使用 [Split()][22] 方法根据定义的过滤器分离加载的 PDF。

以下代码片段显示了如何提取 PDF 文件定义范围内的所有奇数/偶数页。

```
/*
 * Split PDF file by Given Range & Filter (Even/Odd Pages) into Single Page files using C#
 */
// 定义输出文件格式
string filePathOut = "path/splitPDF_{0}.{1}";

// 定义范围和过滤器以将给定范围内的所有奇数页提取为单页文档
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);

// 根据拆分选项加载 PDF 文件和拆分 PDF
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
}
```

## 将 PDF 文件拆分为多个单页文件 {#split-to-single-pages}

以下步骤指导我们如何在 C# 中拆分 PDF 以将页面提取为多个单页文件：

* 定义输出文件格式。
* 使用 [SplitOptions][23] 定义准确的页码。
* 使用 [Merger][24] 类加载 PDF 文件。
* 使用 [Split()][25] 方法根据定义的页面拆分加载的 PDF。

以下代码示例展示了如何将 PDF 文件拆分为多个单页文件。

```
/*
 * Split PDF file into Single Page files using C#
 */
// 定义输出文件格式
string filePathOut = "path/splitPDF_{0}.{1}";

// 定义要提取为单页文档的页面
SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });

// 根据拆分选项加载 PDF 文件和拆分 PDF
using (Merger merger = new Merger("path/document.pdf"))
{
    merger.Split(splitOptions);
}
```

## 代码更改摘要

在所有场景中，改变的是定义 **SplitOptions** 的方式。以下是每个场景的每个代码片段的更改摘要。您可以根据代码中的要求使用以下设置。在这里，我使用了一个 10 页的 PDF 文件。

* **对于多页文件 - 使用间隔**：\[1,2\]、\[3,4,5\]、\[6,7\]、\[8,9,10\]。

```
new SplitOptions(outputFile,  new int[] { 3, 6, 8 }, SplitMode.Interval)
```

* **提取范围内的页面**：\[3\]、\[4\]、\[5\]、\[6\]

```
new SplitOptions(outputFile, 3, 6);
```

* **带过滤器的范围**：\[3\]、\[5\]、\[7\]

```
new SplitOptions(outputFile, 3, 8, (Integer)RangeMode.OddPages);
```

* **单个页面**：\[3\]、\[4\]、\[9\]

```
new SplitOptions(outputFile, new int[] { 3, 4, 9 });
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][26] 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们讨论了使用 C# 拆分 PDF 文件的方法。首先，我们将 PDF 文件拆分为多页和单页文档。我们还从 PDF 文件中提取页面。首先，我们提取所有页面，然后提取给定范围内的偶数/奇数页。您可以尝试使用 GroupDocs.Merger API 构建自己的 PDF 拆分 .NET 应用程序。

要了解有关 API 的更多信息，请访问 [文档][27]。如有疑问，请通过 [论坛][28] 联系我们。

## 也可以看看

* [使用 C# 合并文档][29]
* [使用 C# 将多种文件类型合并为单个文档][30]
* [使用 C# 重新排列 PDF 页面][31]
* [使用 C# 在 Word 中重新排列页面][32]
* [如何在 Java 中拆分 PDF 文件][33]







[1]: https://docs.fileformat.com/pdf/
[2]: https://docs.fileformat.com/pdf/
[3]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/
[4]: #split-pdf-dontet-api
[5]: #split-pdf-to-multipage
[6]: #extract-pages-by-range
[7]: #extract-even-or-odd-pages
[8]: https://blog.groupdocs.com/wp-admin/post.php?post=23730&action=edit#split-to-single-pages
[9]: https://products.groupdocs.com/merger/net/
[10]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[11]: https://downloads.groupdocs.com/merger
[12]: https://www.nuget.org/packages/groupdocs.merger
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/rangemode
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[24]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[25]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/merger
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[30]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[31]: https://blog.groupdocs.com/2022/02/22/move-pdf-pages-using-csharp/
[32]: https://blog.groupdocs.com/2022/02/05/move-word-pages-using-csharp/
[33]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/


