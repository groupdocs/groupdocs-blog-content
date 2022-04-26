---
title: "使用 C# 比较 PDF 文档 - 突出显示、接受或拒绝更改"
date: Fri, 10 Dec 2021 10:20:37 +0000
draft: false
url: /zh/2021/12/10/compare-pdf-documents-using-csharp/
aliases:
- /2019/11/06/find-differences-in-pdf-accept-or-reject-changes-in-csharp/
- /2019/11/06/accept-or-reject-pdf-comparison-changes-in-csharp/
author: 'Shoaib Khan'
summary: "由于 PDF 是数字世界中使用最多的格式之一，因此通常需要比较同一文档的两个版本。本文讨论，**如何使用 C# 比较两个 PDF 文档并突出差异**。此外，我们将了解如何比较受密码保护的 PDF 文件、接受和拒绝更改，以及将两个以上的 PDF 文件与 C# 示例进行比较。"
tags: ['compare PDF files', 'Compare PDF in CSharp', 'Compare PDF to Accept or Reject Changes in CSharp', 'pdf comparison']
categories: ['GroupDocs.Comparison Product Family']
---

由于 PDF 是数字世界中使用最多的格式之一，因此通常需要比较同一文档的两个版本。本文讨论，**如何使用 C# 比较两个 PDF 文档并突出差异**。此外，我们将了解如何比较受密码保护的 PDF 文件、接受和拒绝更改，以及将两个以上的 PDF 文件与 C# 示例进行比较。



{{< figure align=center src="images/compare-pdf-files-using-csharp.jpg" alt="使用 .NET API 比较 PDF 文档以发现差异">}}


此处讨论了以下主题：

* [PDF 比较 .NET API][1]
* [比较两个 PDF 文档][2]
* [接受或拒绝 PDF 文档中已识别的更改][3]
* [比较两个以上的 PDF 文档][4]
* [比较受密码保护的 PDF 文件][5]

## .NET API 来比较 PDF 文件 {#pdf-comparison-dotnet-api}

[GroupDocs.Comparison for .NET][6] 是允许在 .NET 应用程序中比较多个 PDF 文档和许多其他具有相同文档格式的文件的 API。我将在本文的 C# 代码示例中使用此 API 来比较 PDF 文档。

您可以从 [下载部分][7] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Comparison
```

## 使用 C# 比较 PDF 文档 {#compare-two-pdf-files}

如果您有多个 PDF 文档副本，您可以比较这些文件以找出差异（添加、删除）。比较 PDF 内容后，您可以创建一个突出显示所有已识别更改的新文档。以下是使用 C# 比较两个 PDF 文档并突出显示差异的步骤。

* 使用 [Comparer][9] 类加载第一个 PDF 文档。
* 使用 [Add()][10] 方法将第二个文件添加到 **Comparer**。
* 通过调用 [Compare()][11] 方法比较两个 PDF 文件并获取更改摘要。

以下 C# 代码片段显示了如何比较 PDF 文档并突出显示结果文档中的更改。

```
/*
 * Compare Two PDF Documents and Hightlight Changes using C#
 */
using (Comparer comparer = new Comparer(@"path/document-ver1.pdf"))
{
    comparer.Add(@"path/document-ver2.pdf");
    comparer.Compare(@"path/compared-result.pdf");
}
```

## 使用 C# 接受或拒绝 PDF 文件的已识别更改 {#accept-reject-changes}

就像跟踪更改功能一样，您可以以编程方式接受或拒绝 PDF 文档中每个已识别的更改。以下步骤说明如何比较 PDF 文档中已识别的更改，然后接受或拒绝这些更改。

* 使用 [Comparer][12] 类加载源和目标 PDF 文件。
* 使用 [Compare()][13] 方法比较加载的文档。
* 使用 [GetChanges()][14] 方法获取已识别的更改。
* 现在遍历更改并设置 [ComparisonAction][15]。
    * 为每个更改选择 **Accept** 或 **Reject**。
* 调用 [ApplyChanges()][16] 方法以获取具有已接受更改的结果文档。

以下代码片段比较两个 PDF 文档，然后接受已识别的更改，然后使用 C# 拒绝另一个。

```
/*
 * Accept and reject identified changes by comparing PDF documents using C#
 */
using (Comparer comparer = new Comparer(@"path/document-1.pdf"))
{
    comparer.Add(@"path/document-2.pdf");
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    
    // Rejecting the first identified change and it will not be added to result document
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges(@"path/rejected-change-result.pdf", new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });

    changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Accept;
    comparer.ApplyChanges(@"path/accepted-change-result.pdf", new ApplyChangeOptions { Changes = changes });
}
```

## 使用 C# 比较两个以上的 PDF 文件 {#compare-multiple-pdf-documents}

同样，您可以比较两个以上的文档。以下是比较多个 PDF 文档的差异并突出显示已识别更改的步骤。

* 使用 [Comparer][17] 类加载第一个 PDF 文件。
* 使用 [Add()][18] 方法将其他文档添加到 **Comparer**。
* 使用 [Compare()][19] 方法比较所有 PDF 文件并获取更改和更改摘要。

以下示例显示如何在 C# 中比较多个 PDF 文件并获取结果文档中的更改。

```
/*
 * Compare Multiple PDF Documents using C#
 */
using (Comparer comparer = new Comparer(@"path/document-1.pdf"))
{
    comparer.Add(@"path/document-2.pdf");
    comparer.Add(@"path/document-3.pdf");
    comparer.Add(@"path/document-4.pdf");

    comparer.Compare(@"path/compare-result.pdf");
}
```

## 使用 C# 比较受密码保护的 PDF 文档 {#compare-password-protected-pdf-files}

您可以通过在加载这些文档时提供密码来比较受密码保护的文件。以下步骤展示了我们如何使用 C# 比较受密码保护的文档的 PDF 内容。

* 通过提供密码准备源文件和目标文件的加载选项。
* 使用 [Comparer][20] 类加载源文档。
* 使用准备好的加载选项将目标文档添加到 **Comparer**。
* 通过调用 [Compare()][21] 方法获取差异摘要。

以下示例比较了两个受密码保护的 PDF 文件，并使用 C# 在单独的文档中突出显示了已识别的差异。

```
/*
 * Compare Password Protected PDF Documents using C#
 */
using (Comparer comparer = new Comparer(@"path/protected-document-1.pdf", new LoadOptions(){ Password = "SourceFilePassword" }))
{
    comparer.Add(@"path/protected-document-2.pdf", new LoadOptions() { Password = "TargetFilePassword" });
    comparer.Compare(@"path/compared-protected-docs-result.pdf");
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][22] 使用 API 而不受评估限制。

## 结论

最后，我们学习了如何使用 C# 比较两个或多个 PDF 文件。此外，我们强调了差异并以编程方式接受或拒绝已识别的更改。最后，我们看到了如何在 .NET 应用程序中比较受密码保护的 PDF 文档。

其他几个 [自定义][23] 可用于控制比较结果。您可以设置比较敏感度、仅显示摘要页面、忽略 **gaps** 等。从 [documentation][24] 了解有关 **GroupDocs.Comparison for .NET** 的更多信息。您可以为各种 [文档格式][25] 构建自己的文档比较应用程序。如有疑问，请通过 [论坛][26] 联系我们。

## 也可以看看

* [使用 C# 进行图像比较并找出差异][27]
* [使用 C# 比较 Word 文档][28]
* [用Java差异库比较文档][29]







[1]: #pdf-comparison-dotnet-api
[2]: #compare-two-pdf-files
[3]: #accept-reject-changes
[4]: #compare-multiple-pdf-documents
[5]: #compare-password-protected-pdf-files
[6]: https://products.groupdocs.com/comparison/
[7]: https://downloads.groupdocs.com/comparison/net
[8]: https://www.nuget.org/packages/groupdocs.comparison
[9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[10]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[12]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges/index
[15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/comparisonaction
[16]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/applychanges/index
[17]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://docs.groupdocs.com/comparison/net/comparison/
[24]: https://docs.groupdocs.com/comparison/net
[25]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[28]: https://blog.groupdocs.com/2021/12/01/compare-word-documents-using-csharp/
[29]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/


