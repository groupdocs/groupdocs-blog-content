---
title: "'使用 Java 搜索和替换 Word 文档中的文本'"
date: Fri, 04 Feb 2022 15:24:00 +0000
draft: false
url: /zh/2022/02/04/find-and-replace-text-in-word-documents-using-java/
author: 'Shoaib Khan'
summary: "在其中一篇文章中，我们已经讨论了[如何以 .NET 开发人员的身份编辑文档中的单词](https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/)。该策略以多种方式用于擦除敏感内容、隐藏或删除电子邮件地址或身份证号等私人信息。本文讨论**如何使用 Java 在 Word DOC/DOCX 文档中执行单词搜索。** 我们将分别讨论如何使用 Java API 进行编校，以不同的技术**查找和替换文本、单词或短语**。"
tags: ['how to redact in word', 'how to redact PDF in Java', 'how to redact Word in Java', 'Java Redaction API', 'Redact in Java']
categories: ['GroupDocs.Redaction Product Family']
---

在其中一篇文章中，我们已经讨论了[如何以 .NET 开发人员的身份编辑文档中的单词](https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/)。该策略以多种方式用于擦除敏感内容、隐藏或删除电子邮件地址或身份证号等私人信息。本文讨论**如何使用 Java 在 Word DOC/DOCX 文档中执行单词搜索。** 我们将分别讨论如何使用 Java API 进行编校，以不同的技术**查找和替换文本、单词或短语**。

下面将介绍以下主题：

* [用于单词搜索和替换文本的 Java API](#word-search-java-api)
* [查找和替换单词或短语](#replace-word-or-phrase)
* [区分大小写的单词搜索和替换文本](#case-sensitive-text-redaction)
* [使用正则表达式替换文本 (RegEx)](#replace-text-using-regex)
* [用彩色框替换文本](#hide-text-with-colored-box)

## 用于单词搜索和替换文本的 Java API {#word-search-java-api}

**GroupDocs** 提供 [Java 编校 API](https://products.groupdocs.com/redaction/java/)，允许查找和替换 MS Word 支持的文件和其他各种文件格式的其他文档的内容。除了文本编辑和光栅化之外，API 还支持元数据、注释、电子表格以及图像编辑功能。文档中提供了 Word 文档、电子表格、演示文稿、图像和 PDF 文档的[支持的文件格式](https://docs.groupdocs.com/redaction/java/supported-document-formats/)。

### 下载或配置

您可以从 [下载部分](https://downloads.groupdocs.com/redaction) 下载 **JAR** 文件，或者只获取 **maven- 的 pox.xml 的最新存储库和依赖项配置基于** Java 应用程序。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>

<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-redaction</artifactId>
	<version>21.12</version>
</dependency>
```

编辑过程不需要 MS Word 或任何其他第三方软件。 现在让我们从处理搜索和替换文本的不同方法开始。 以下是以下示例中使用的 Word 文档的屏幕截图。 您也可以对其他文档格式使用相同的方法，只需对源代码进行很少或没有更改。

{{< figure align=center src="images/original-doc.png" alt="Document to redact text">}}

## 使用 Java 查找和替换单词或短语 {#replace-word-or-phrase}

以下步骤说明了如何在 Java 应用程序的 Word 文档中查找并替换出现的单词/短语。

* 使用 [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor) 类加载 DOC/DOCX 文件。
* 使用 [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction) 和 [ReplacementOptions](https://apireference.groupdocs) 查找确切的短语或单词 .com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions) 类。
* 使用 Redactor 的 apply 方法来应用编辑。
* 要在更改后将文件保存在不同的位置，请使用输出流。
* 使用 [save](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#save(java.io.OutputStream,%20com.groupdocs.redaction.options.RasterizationOptions)) 方法。

以下代码使用 Java 查找并替换上述 Word 文档中的单词“John Doe”。 它将所有出现的“John Doe”替换为单词“[censored]”。

```
// 使用 Java 查找确切的短语并将其替换为其他文本
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));

// 如果您想将编辑后的文件以不同的名称保存在不同的位置。
FileOutputStream stream = new FileOutputStream("path/exactPhrase.docx");
RasterizationOptions rasterOptions = new RasterizationOptions();
rasterOptions.setEnabled(false);
redactor.save(stream, rasterOptions);
```

代码的输出如下。

{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="使用精确短语编辑">}}


## Java 中区分大小写的单词搜索和替换文本 {#case-sensitive-text-redaction}

您似乎对单词的确切字母大小写持谨慎态度，只想替换仅与您的区分大小写搜索匹配的单词。 以下代码替换了 Java 中单词“John Doe”的完全大小写匹配的存在。

```
// 查找确切的短语（区分大小写) 并使用 Java 将其替换为其他文本
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
redactor.save();
```

代码的输出如下。

{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="区分大小写的编辑">}}


## 在 Java 中使用正则表达式 (RegEx) 替换文本 {#replace-text-using-regex}

如果您不想更改文档中存在的确切单词但某些模式，则可以使用正则表达式。 以下步骤允许您在 Java 应用程序中使用正则表达式 (RegEx) 查找和替换任何文本模式。

* 使用 [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor) 类加载文档。
* 使用 [RegexRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction) 创建正则表达式。
* 使用 [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions) 提供文本以替换 RegEx 匹配项。
* 使用 apply 方法替换所有正则表达式匹配。
* 使用保存方法获取编辑过的文档。

以下代码显示了如何使用 RegEx 在 Word 文件中执行单词搜索，并使用 Java 将其替换为其他文本。

```
// 使用正则表达式查找文本并使用 Java 将其替换为其他文本
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
redactor.save();
```

以下是上述代码的输出：

{{< figure align=center src="images/Regex-Redaction.png" alt="正则表达式编辑">}}


## 用 Java 中的彩色框替换文本 {#hide-text-with-colored-box}

如果您不想替换您的内容而只想隐藏它，API 允许您通过在其上绘制一个框来覆盖文本匹配。 以下 Java 代码隐藏了带有黑色矩形框的文本。

```
// 查找文本并通过使用 Java 在其上绘制矩形来隐藏它
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new ExactPhraseRedaction("John Doe", true, new ReplacementOptions(java.awt.Color.BLACK)));
redactor.save();
```

上述代码的输出如下。

{{< figure align=center src="images/Colored-Box-Redaction.png" alt="使用框隐藏文本">}}

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## Conclusion

总而言之，您学习了如何使用精确文本短语搜索、区分大小写搜索、使用正则表达式搜索以及最后但并非最不重要的隐藏文本而不是替换它来执行单词搜索以在 Word 文档中查找文本。 您可以使用这些不同的技术以不同方式替换 MS Word 文档中的结果。

有关 API 的更多详细信息和了解，请访问[文档](https://docs.groupdocs.com/redaction)。 如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 与我们联系。

## 也可以看看

* [用Java构建全文搜索解决方案](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)
* [Java 中的图像比较以发现差异](https://blog.groupdocs.com/2021/06/16/compare-images-in-java/)
* [使用 Java 在 Word 中重新排列页面](https://blog.groupdocs.com/2022/03/01/move-word-pages-using-java/)
* [使用 C# 查找和替换 PDF 中的文本](https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/)