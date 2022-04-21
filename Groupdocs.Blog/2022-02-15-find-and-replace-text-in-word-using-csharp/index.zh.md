---
title: "'使用 C# 在 Word 文档中查找和替换单词'"
date: Tue, 15 Feb 2022 10:41:00 +0000
draft: false
url: /zh/2022/02/15/使用 csharp 查找并替换文字中的文字/
author: 'Shoaib Khan'
summary: "替换文档中的单词或短语的原因可能有很多。无论您是想在公开共享文档之前删除敏感内容，还是想隐藏/删除电子邮件 ID 或社会安全号码等所有私人信息，您都需要编辑文档内容。本文将指导您**如何使用 C# 在 .NET 应用程序中以编程方式编辑 Word 文档**。我们将分别讨论如何通过隐藏文本进行编辑，以及如何使用不同的技术**查找和替换文本、单词或短语**。"
tags: ['case sensitive find and replace', 'Find &amp; Replace in Word', 'Find and replace text', 'Redact in CSharp', 'Redact Word in CSharp', 'Replace words in CSharp', 'text redaction']
categories: ['GroupDocs.Redaction Product Family']
---

替换文档中的单词或短语的原因可能有很多。无论您是想在公开共享文档之前删除敏感内容，还是想隐藏/删除电子邮件 ID 或社会安全号码等所有私人信息，您都需要编辑文档内容。本文将指导您**如何使用 C# 在 .NET 应用程序中以编程方式编辑 Word 文档**。我们将分别讨论如何通过隐藏文本进行编辑，以及如何使用不同的技术**查找和替换文本、单词或短语**。

下面将介绍以下主题：

* [用于替换文本的 .NET API](#dotnet-redaction-api)
* [查找和替换单词或短语](#replace-word-or-phrase)
* [区分大小写的搜索和替换单词或短语](#case-sensitive-text-redaction)
* [使用正则表达式替换文本 (RegEx)](#replace-text-using-regex)
* [用彩色框隐藏文本](#hide-text-with-colored-box)

## 用于替换文本的 .NET Redaction API {#dotnet-redaction-api}

GroupDocs.Redaction for .NET 是文档编辑 API，允许从各种文件格式的文档中查找并替换预期数据。除了文本编辑和光栅化，API 还提供元数据、注释、电子表格和图像编辑功能。文档中提供了 Word 文档、电子表格、演示文稿、图像和 PDF 文档的[支持的文件格式](https://docs.groupdocs.com/redaction/net/supported-document-formats/)。

您可以从 [下载部分](https://downloads.groupdocs.com/redaction) 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https) 在您的 .NET 应用程序中安装 API ://www.nuget.org/packages/groupdocs.redaction) 。

```
PM> Install-Package GroupDocs.Redaction
```

在此过程中无需安装 MS Office 或任何其他第三方软件。现在让我们开始看看处理在文档中查找和替换文本的不同方法。以下是示例中用于演示的 Word 文档的屏幕截图。相同的方法将适用于其他文档格式，而无需对代码进行任何更改。



{{< figure align=center src="images/original-doc.png" alt="">}}


## 使用 C# 在 Word 文档中查找和替换单词或短语 {#replace-word-or-phrase}

以下步骤说明了如何在 Word 文档中查找任何单词/短语，然后将所有出现的地方替换为 C# 应用程序中的一些其他文本。

* 使用 [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) 类加载 Word 文档 (DOC/DOCX)。
* 使用带有 [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions) 的 [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction) 类查找确切的短语或单词。
* 使用 Redactor 的 [Apply](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) 方法应用编辑。
* 使用 [Save](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) 方法保存更改。

以下代码查找并替换 C# 中的单词。更准确地说，它将所有出现的“John Doe”替换为“\[censored\]”。

```
// 使用 C# 查找确切的短语并将其替换为其他文本
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
  redactor.Save();
}
```

代码的输出如下。



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## 使用 C# 在 Word 文件中进行区分大小写的搜索和替换 {#case-sensitive-text-redaction}

同样，您可以通过查找确切的单词并将其替换为任何其他单词来执行 Word 文档的区分大小写的编辑。以下代码使用 C# 替换 DOCX 文件中存在的单词“John Doe”，但这次搜索将区分大小写。

```
// 查找确切的短语（区分大小写) 并使用 C# 将其替换为其他文本
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
  redactor.Save();
}
```

代码的输出如下。



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## 使用 C# 使用正则表达式 (RegEx) 替换 Word 文件中的文本 {#replace-text-using-regex}

要查找和替换 Word（DOC、DOCX) 文件中的任何文本模式，您可以使用正则表达式。以下步骤允许您使用 C# 使用 RegEx 编辑 Word 文档。

* 使用 [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) 类加载 Word 文档。
* 使用带有 [ReplacementOptions](https://apireference.groupdocs.com/redaction) 的 [RegexRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction) 类查找正则表达式匹配/net/groupdocs.redaction.redactions/replacementoptions) 。
* 使用 [Apply](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) 方法替换所有正则表达式匹配文本。
* 使用[保存](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index)方法获取编辑过的Word文件。

以下代码显示了如何使用 RegEx 在 Word 文件中查找文本模式，然后使用 C# 将其替换/隐藏为其他文本。

```
// 使用正则表达式查找文本并使用 C# 将其替换为其他文本
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
  redactor.Save();
}
```

上述代码的输出如下。



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## 使用 C# 在带有彩色框的 Word 文档中隐藏机密文本 {#hide-text-with-colored-box}

如果您不想替换您的私人内容而只想覆盖它，API 允许您通过在其上绘制一个框来隐藏该内容。以下代码使用 C# 将黑色矩形放置在预期文本上以使文本变黑。

```
// 查找文本并通过使用 C# 在其上绘制矩形来隐藏它
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions(System.Drawing.Color.Black)));
  redactor.Save();
}
```

上述代码的输出如下。



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

最后，您学习了如何使用不同的技术在 Word（DOC、DOCX) 文件中查找文本并以不同方式替换结果。更准确地说，我们讨论了如何查找文本、单词或短语，即使它是区分大小写的搜索或在 C# 中使用正则表达式。后来我们用其他一些文本替换了搜索结果，或者将彩色矩形框放在搜索的文本上。

有关 API 的更多信息，请访问 [文档](https://docs.groupdocs.com/redaction)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [用 C# 构建您的全文搜索解决方案](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)
* [通过比较 C# 中的两个图像找出差异](https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/)





