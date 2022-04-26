---
title: "使用 C# 比较 Word 文档"
date: Wed, 01 Dec 2021 09:58:00 +0000
draft: false
url: /zh/2021/12/01/compare-word-documents-using-csharp/
aliases:
- /2014/07/19/groupdocs-comparison-for-dot-net-library-compare-two-word-documents-in-c-sharp-asp-net/
author: 'Shoaib Khan'
summary: "文字处理文档是起草合同、协议、文件和许多其他官方文件的最常用方式。如果您需要比较和合并两个 Word 文档，就像 Microsoft Word 的跟踪更改选项一样，我们可以在 .NET 应用程序中以编程方式完成。在本文中，我们将讨论**如何比较两个 Word 文档并使用 C# 突出显示已识别的差异**。此外，我们将了解如何比较受密码保护的文档、**接受和拒绝更改**，以及将两个以上的文档与 C# 示例进行比较。"
tags: ['automate document comparison', 'compare two word documents', 'compare two word documents and highlight differences', 'Compare Word Documents CSharp', 'compare word files in c#', 'GroupDocs Comparison']
categories: ['GroupDocs.Comparison Product Family']
---

文字处理文档是起草合同、协议、文件和许多其他官方文件的最常用方式。如果您需要比较和合并两个 Word 文档，就像 Microsoft Word 的跟踪更改选项一样，我们可以在 .NET 应用程序中以编程方式完成。在本文中，我们将讨论**如何比较两个 Word 文档并使用 C# 突出显示已识别的差异**。此外，我们将了解如何比较受密码保护的文档、**接受和拒绝更改**，以及将两个以上的文档与 C# 示例进行比较。



{{< figure align=center src="images/compare-word-files-using-csharp.jpg" alt="使用 .NET API 比较 Word 文档以发现差异">}}


此处讨论了以下主题：

* [文档比较.NET API][1]
* [比较两个Word文档][2]
* [接受或拒绝 Word 文档中已识别的更改][3]
* [比较两个以上的Word文档][4]
* [比较受密码保护的 Word 文件][5]

## .NET API 来比较 Word 文档 {#doc-comparison-dotnet-api}

[GroupDocs.Comparison][6] 提供了一个 .NET API，它允许在 .NET 应用程序中[比较然后合并多种文件格式的各种文档][7]。我将使用它的 .NET API 即 [GroupDocs.Comparison for .NET][8] 来比较 Word 文档。

您可以从 [下载部分][9] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][10] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Comparison
```

## 使用 C# 比较 Word 文档 {#compare-two-word-files}

如果您有一个文档的两个版本，您可以比较这些文档以找出它们的差异（添加、删除）并创建一个显示所有更改的新文档。以下是比较任意两个 Word 文档并突出显示差异的步骤。

* 使用 [Comparer][11] 类加载第一个 Word 文档。
* 使用 [Add()][12] 方法将第二个文件添加到 **Comparer**。
* 只需调用 [Compare()][13] 方法即可比较获取更改摘要。

以下 C# 代码显示了如何比较 Word 文档并获取结果文档中的更改。

```
/*
 * Compare Two Word Documents and Hightlight Changes using C#
 */
using (Comparer comparer = new Comparer("path/document.docx"))
{
    comparer.Add("path/document-ver2.docx");
    comparer.Compare("path/compared-result.docx");
}
```

## 使用 C# 接受或拒绝 Word 文档的已识别更改 {#accept-reject-changes}

与 MS Word 的跟踪更改选项类似，您可以接受或拒绝每个已识别的更改。以下是比较然后接受或拒绝 Word 文档中已识别的更改的步骤。

* 使用 [Comparer][14] 类加载源文档并添加目标 Word 文档。
* 使用 [Compare()][15] 方法对加载的文档进行比较。
* 使用 [GetChanges()][16] 方法获取已识别的更改。
* 现在您可以遍历更改并设置每个更改的[ComparisonAction][17]。
    * 对于每个更改，您可以选择 **Accept** 或 **Reject**。
* 完成更改后，调用 [ApplyChanges()][18] 方法以获取具有应用更改的结果文档。

以下 C# 源代码比较两个 Word 文档，然后接受一个已识别的更改，然后拒绝另一个。

```
/*
 * Accept and reject identified changes by comparing Word documents using C#
 */
using (Comparer comparer = new Comparer("path/document-1.docx"))
{
    comparer.Add("path/document-2.docx");
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    
    // Rejecting the first identified change and it will not be added to result document
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges("path/rejected-change-result.docx", new ApplyChangeOptions { Changes = changes, SaveOriginalState = true });

    changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Accept;
    comparer.ApplyChanges("path/accepted-change-result.docx", new ApplyChangeOptions { Changes = changes });
}
```

## 使用 C# 比较两个以上的文档 {#compare-multiple-word-documents}

同样，可以一次比较两个以上的文档。以下是比较多个 Word 文档的差异并突出显示已识别更改的步骤。

* 使用 [Comparer][19] 类加载第一个 Word 文档。
* 继续使用 [Add()][20] 方法将其他文档添加到 **Comparer**。
* 调用 [Compare()][21] 方法获取更改和更改摘要。

以下 C# 代码显示了如何比较两个以上的 Word 文档并获取结果文档中的更改。

```
/*
 * Compare Multiple Word Documents using C#
 */
using (Comparer comparer = new Comparer("path/document-1.docx"))
{
    comparer.Add("path/document-2.docx");
    comparer.Add("path/document-3.docx");
    comparer.Add("path/document-4.docx");

    comparer.Compare("path/compare-result.docx");
}
```

## 使用 C# 比较受密码保护的 Word 文档 {#compare-password-protected-word-docs}

如果您的文档受密码保护，只需在加载文档时提供密码即可。以下步骤展示了我们如何使用 C# 比较受密码保护的文档的内容。

* 通过提供密码准备源文件和目标文件的加载选项。
* 使用 [Comparer][22] 类加载源文档。
* 使用准备好的加载选项将目标文档添加到 **Comparer**。
* 通过调用 [Compare()][23] 方法获取差异摘要。

以下 C# 代码示例比较两个受密码保护的 Word 文件，并生成突出显示差异的结果文档。

```
/*
 * Compare Password Protected Word Documents using C#
 */
using (Comparer comparer = new Comparer("path/protected-document-1.docx", new LoadOptions(){ Password = "SourceFilePassword" }))
{
    comparer.Add("path/protected-document-2.docx", new LoadOptions() { Password = "TargetFilePassword" });
    comparer.Compare("path/compared-protected-docs-result.docx");
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][24] 使用 API 而不受评估限制。

## 结论

总而言之，我们学会了使用 C# 比较两个或多个 Word 文档。此外，在突出差异之后，我们学会了以编程方式接受和拒绝已识别的更改。最后，我们还讨论了如何比较 .NET 应用程序中受密码保护的 Word 文档。

还有许多其他[自定义来控制比较结果][25]，例如设置比较敏感度、仅显示摘要页面、忽略**差距**等等。详细了解 **GroupDocs.Comparison for .NET**。访问它的[文档][26]，开始为各种[支持的文档格式][27]构建您自己的文档比较应用程序。如有疑问，请通过 [论坛][28] 联系我们。

## 也可以看看

* [使用 C# 比较图像以发现差异][29]
* [使用 C# 比较 PDF 文档 – 突出显示、接受或拒绝更改][30]
* [如何在 Java 中比较文本、Word 和 PDF 文件][31]







[1]: #doc-comparison-dotnet-api
[2]: #compare-two-word-files
[3]: #accept-reject-changes
[4]: #compare-multiple-word-documents
[5]: #compare-password-protected-word-docs
[6]: https://products.groupdocs.com/comparison/
[7]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[8]: https://products.groupdocs.com/comparison/net/
[9]: https://downloads.groupdocs.com/comparison/net
[10]: https://www.nuget.org/packages/groupdocs.comparison
[11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[12]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[16]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges/index
[17]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/comparisonaction
[18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/applychanges/index
[19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[22]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[23]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/comparison/net/comparison/
[26]: https://docs.groupdocs.com/comparison/net
[27]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[30]: https://blog.groupdocs.com/2021/12/10/compare-pdf-documents-using-csharp/
[31]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/


