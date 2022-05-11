---
title: "使用 C# 从 PDF 中删除页面 |偶数、奇数、列表和范围"
seoTitle: "使用 C# 从 PDF 中删除页面 |偶数、奇数、列表和范围"
date: Tue, 19 Apr 2022 11:00:00 +0000
draft: false
description: "使用 C# 从 PDF 文件中删除任何一组页面。从 .NET 应用程序中的 PDF 文件中删除页面列表、任何给定范围、偶数页或奇数页。"
url: /zh/2022/04/19/delete-pages-from-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "在共享或完成草稿时，我们经常需要从文档中删除不需要的、过时的、高度机密的页面。在本文中，我们将学习**如何使用 C# 以编程方式从 PDF 文档中删除此类页面**。要求有时可能会有所不同，因此我们将讨论删除 PDF 文档中不同页面集的不同方法。"
tags: ['delete pages', 'delete pages in csharp', 'remove pages', 'remove pages in csharp', 'delete pages from pdf in csharp', 'delete pages in csharp']
categories: ['GroupDocs.Merger Product Family']
---

在共享或完成草稿时，我们经常需要从文档中删除不需要的、过时的、高度机密的页面。在本文中，我们将学习**如何使用 C# 以编程方式从 PDF 文档中删除此类页面**。要求有时可能会有所不同，因此我们将讨论删除 PDF 文档中不同页面集的不同方法。

下面讨论以下主题：

- [PDF 页面删除 .NET API](#pdf-page-removal-dotnet-api)
- [删除选择/页面列表](#remove-pdf-pages-list-in-csharp)
- [删除页面范围](#remove-pdf-pages-range-in-csharp)
- [删除偶数或奇数范围的页面](#remove-even-odd-pdf-pages-in-csharp)

## .NET API 从 PDF 中删除页面 {#pdf-page-removal-dotnet-api}

GroupDocs.Merger 展示了允许以编程方式从 PDF 文档中删除页面的 .NET API。此外，它还允许 .NET 应用程序更改页面方向、移动页面、拆分文档、提取和旋转文档页面。我们将使用此 [GroupDocs.Merger for .NET][1] 使用 C# 删除 PDF 文件的选择性页面。有关 API 的详细信息和其他功能，您可以访问[文档][2]。

您可以从 [下载部分][3] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][4] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 使用 C# 从 PDF 中删除选定页面 {#remove-pdf-pages-list-in-csharp}

只需从加载的 PDF 文档中提供要删除的页面列表。以下步骤允许使用 C# 从 PDF 文档中删除提供的选择性页面列表。

- 使用要删除的**页码列表**初始化 [RemoveOptions][5] 类。
- 使用源文档路径或流实例化 [Merger][6] 对象。
- 调用 RemovePages() 方法删除列出的页面。
- 调用适当的 Save() 方法来保存生成的文档。

以下 C# 代码示例从 PDF 文档中删除选定的第 3 页和第 5 页。

```
// 在 C# 中从 PDF 中删除选择性页面
RemoveOptions removeOptions = new RemoveOptions(new int[] { 3, 5 });

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/selected-pages-removed.pdf");
}
```

## 使用 C# 从 PDF 中删除页面范围 {#remove-pdf-pages-range-in-csharp}

同样，您可以删除 PDF 文档中的任何页面范围。以下步骤允许使用 C# 在提供的范围内删除一系列页面。

- 初始化 [RemoveOptions][5]。
- 通过设置**开始**和**结束**页码提供**页范围**。
- 使用源文档路径或流实例化 [Merger][6] 对象。
- 使用范围调用 RemovePages() 方法。
- 调用适当的 Save() 方法来保存生成的文档。

下面的 C# 示例代码从 PDF 文档中删除提供的范围（即 2 到 4）内的所有页面。

```
// 在 C# 中从 PDF 中删除选定的页面范围
RemoveOptions removeOptions = new RemoveOptions(2, 4);

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/pages-range-removed.pdf");
}
```

## 使用 C# 从 PDF 中删除偶数页或奇数页 {#remove-even-odd-pdf-pages-in-csharp}

同样，您可以删除文档的所有偶数页或奇数页。以下步骤展示了如何使用 C# 在给定范围内删除 PDF 文件的偶数页或奇数页。

- 使用页面范围初始化 [RemoveOptions][5] 类。
- 将模式设置为**偶**或**奇**。
- 使用源文档路径或流实例化 [Merger][6] 对象。
- 使用删除选项调用 RemovePages() 方法。
- 调用适当的 Save() 方法来保存生成的文档。

以下 C# 代码示例从 PDF 文档中删除了提供的范围（即 1-6）内的所有偶数页。

```
// 使用 C# 从给定范围内的 PDF 中删除所有偶数页
RemoveOptions removeOptions = new RemoveOptions(1, 6 ,RangeMode.EvenPages);

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/even-pages-removed.pdf");
}
```

以下 C# 代码片段从整个 PDF 文档中删除所有奇数页。

```
// 使用 C# 从给定范围内的 PDF 中删除所有奇数页
RemoveOptions removeOptions = new RemoveOptions(1, 6 ,RangeMode.OddPages);

using (Merger merger = new Merger("path/document-pdf"))
{
    merger.RemovePages(removeOptions);
    merger.Save("path/odd-pages-removed.pdf");
}
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][7] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们刚刚学习了如何在 .NET 应用程序中使用 C# 从 PDF 文档中删除页面。具体来说，我们已经看到了如何通过提供页码和页面范围来删除页面。最后，我们看到了如何从任何 PDF 文档中删除偶数页或奇数页。您可以尝试构建自己的应用程序，以消除 PDF 文件中所选页面的任何变化。

有关 API 的更多详细信息，请访问文档。如有疑问，请通过 [论坛][8] 联系我们。

## 也可以看看
- [C#去除PDF文档水印][9]
- [使用 C# 将 PDF 转换为灰度][10]
- [如何使用 C# 重新排列 PDF 页面][11]
- [使用 C# 查找和替换 PDF 中的文本][12]
- [使用 C# 使用密码锁定和解锁 PDF 文件][13]

[1]: https://products.groupdocs.com/merger/net
[2]: https://docs.groupdocs.com/merger/net/
[3]: https://downloads.groupdocs.com/merger/net
[4]: https://www.nuget.org/packages/groupdocs.merger/
[5]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/removeoptions
[6]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[7]: https://purchase.groupdocs.com/temporary-license
[8]: https://forum.groupdocs.com/
[9]: https://blog.groupdocs.com/2022/03/25/remove-watermark-from-pdf-in-csharp/
[10]: https://blog.groupdocs.com/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/
[11]: https://blog.groupdocs.com/2022/02/22/move-pdf-pages-using-csharp/
[12]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[13]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/

