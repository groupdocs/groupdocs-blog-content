---
title: "'使用 C# 查找和替换 PDF 中的文本'"
date: Sat, 19 Feb 2022 04:42:16 +0000
draft: false
url: /zh/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
author: 'Shoaib Khan'
summary: "模板广泛用于生成定制文档。本文指导**如何使用 C# 查找和替换 PDF 文档中的文本和单词**。我们将分别讨论如何以编程方式替换单词和短语，用区分大小写的搜索替换单词，使用正则表达式替换。最后，我们还将学习如何使用 C# 隐藏搜索到的字符串。"
tags: ['Blackout Text in PDF', 'Find &amp; Replace Text in PDF', 'Find Text in PDF', 'Hide Text in PDF', 'Redact PDF files']
categories: ['GroupDocs.Redaction Product Family']
---

模板广泛用于生成定制文档。本文指导**如何使用 C# 查找和替换 PDF 文档中的文本和单词**。我们将分别讨论如何以编程方式替换单词和短语，用区分大小写的搜索替换单词，使用正则表达式替换。最后，我们还将学习如何使用 C# 隐藏搜索到的字符串。

下面将介绍以下主题：

* [用于替换文本的 .NET API](#dotnet-redaction-api)
* [查找和替换单词或短语](#replace-word-or-phrase)
* [区分大小写的单词搜索和替换](#case-sensitive-text-redaction)
* [替换为正则表达式 (RegEx)](#replace-text-using-regex)
* [用彩色框隐藏文本](#hide-text-with-colored-box)

## 用于替换文本的 .NET Redaction API {#dotnet-redaction-api}

GroupDocs 展示了用于 .NET 的 GroupDocs.Redaction，该 API 用于编辑、隐藏或删除 .NET 应用程序中的文档、演示文稿、电子表格、PDF 文件和图像的内容甚至元数据。有关 API 的更多详细信息，请访问其文档。

您可以从 [下载部分](https://downloads.groupdocs.com/redaction) 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.redaction) 。

```
PM> Install-Package GroupDocs.Redaction
```

无需安装任何 PDF 编辑器或任何其他第三方软件进行编辑。以下是以下示例中使用的 PDF 文档的屏幕截图。同样的方法也适用于其他文档格式，代码几乎没有或几乎没有变化。



{{< figure align=center src="images/original-doc.png" alt="">}}


## 使用 C# 在 PDF 中查找和替换单词或短语 {#replace-word-or-phrase}

您可以使用此功能隐藏任何机密数据，还可以从模板创建新的自定义文档。以下步骤说明了如何在 C# 应用程序中查找包含其他文本的 PDF 文档中的任何单词/短语。

* **使用 [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) 类加载** PDF 文件。
* 使用 [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction) 和 [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions) 查找确切的短语或单词。
* **使用 [Apply()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) 方法应用编辑**。
* **保存**使用 [Save()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) 方法更改的新文档。

以下代码查找并替换 C# 中的单词。更准确地说，它通过将“John Doe”替换为单词“\[censored\]”来隐藏所有出现的“John Doe”。

```
// 使用 C# 查找确切的短语并将其替换为其他文本
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

代码的输出如下。



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## 使用 C# 在 PDF 中查找和替换区分大小写的文本或短语 {#case-sensitive-text-redaction}

您可以执行区分大小写的搜索和编辑。以下代码替换了 C# 中单词“John Doe”但不替换“john doe”的区分大小写的存在。

```
// 查找确切的短语（区分大小写) 并使用 C# 将其替换为其他文本
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

代码的输出如下。



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## 使用 C# 用正则表达式 (RegEx) 替换 PDF 中的文本 {#replace-text-using-regex}

您还可以使用正则表达式替换任何特定的文本模式。以下步骤允许您在 .NET 应用程序中使用正则表达式 (RegEx) 搜索后编辑 PDF。

* **使用 [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) 类加载** PDF 文档。
* 使用带有 [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions) 的 [RegexRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction) 类查找正则表达式匹配。
* 使用 [Apply()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) 方法对文档进行更改。
* **保存**使用适当的 [Save()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) 方法编辑的文档。

以下代码显示了如何使用 RegEx 在 PDF 文档中查找特定文本模式，然后使用 C# 将其替换/隐藏为其他文本。

```
// 使用正则表达式查找文本并使用 C# 将其替换为其他文本
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

上述代码的输出如下。



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## 用 C# 中的彩色框替换文本 {#hide-text-with-colored-box}

如果您只想隐藏您的 PDF 文件的搜索内容（私人信息) ，您只需在其上放置一个封面即可。 API 允许您隐藏搜索到的文本。以下 C# 代码将黑色矩形放置在提到的私有文本上。

```
// 在 PDF 中查找文本并通过使用 C# 在其上绘制矩形来隐藏它
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions(System.Drawing.Color.Black)));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

上述代码的输出如下。



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们学习了如何使用不同的搜索技术在 PDF 文件中查找某些文本。稍后我们讨论了如何通过使用 C# 替换或隐藏 .NET 应用程序中的文本来编辑 PDF 文件。更准确地说，我们只是搜索单词、短语、区分大小写搜索以及使用 C# 中的正则表达式。最后，我们将搜索结果替换为其他文本或在其上用矩形框隐藏。

有关 API 的更多详细信息，请访问 [文档](https://docs.groupdocs.com/redaction)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [在 C# 中编辑扫描的 PDF 文档](https://blog.groupdocs.com/2021/09/25/redact-text-and-scanned-images-using-csharp/)
* [使用 C# 在多个文件中搜索同义词](https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp/)
* [用 C# 构建您的全文搜索解决方案](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)





