---
title: "'在 Java 中搜索和替换 PDF 中的文本'"
date: Tue, 08 Mar 2022 10:10:00 +0000
draft: false
url: /zh/2022/03/08/find-and-replace-text-in-pdf-in-java/
author: 'Shoaib Khan'
summary: "模板被广泛用于通过将模板键替换为相应的值来生成个性化文档。本文介绍了**如何在 Java 中查找和替换 PDF 文档中的文本和单词**。我们将分别讨论如何执行单词和短语搜索、区分大小写的单词搜索、使用正则表达式替换找到的文本。最后，我们将学习如何使用 Java 隐藏搜索到的文本部分。"
tags: ['Blackout Text', 'Blackout Text in PDF', 'Find &amp; Replace Text in PDF', 'Find Text in PDF', 'Hide Text in PDF', 'Redact PDF files', 'Word Search in Java']
categories: ['GroupDocs.Redaction Product Family']
---

模板被广泛用于通过将模板键替换为相应的值来生成个性化文档。本文介绍了**如何在 Java 中查找和替换 PDF 文档中的文本和单词**。我们将分别讨论如何执行单词和短语搜索、区分大小写的单词搜索、使用正则表达式替换找到的文本。最后，我们将学习如何使用 Java 隐藏搜索到的文本部分。

下面将介绍以下主题：

* [用于替换文本的 Java API](#java-redaction-api)
* [查找和替换单词或短语](#replace-word-or-phrase)
* [区分大小写的单词搜索和替换](#case-sensitive-text-redaction)
* [使用正则表达式替换 (RegEx)](#replace-text-using-regex)
* [用彩色框隐藏文本](#hide-text-with-colored-box)

## 用于替换文本的 Java Redaction API {#java-redaction-api}

GroupDocs 提供用于应用各种类型的编辑的 Java API。它允许编辑、隐藏或删除应用程序中文档、演示文稿、电子表格、PDF 文件和图像的内容甚至元数据。有关 API 的更多详细信息，请访问其 [文档](https://docs.groupdocs.com/redaction/java/)。

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

好处之一是无需安装任何 PDF 编辑器或任何其他用于 PDF 编辑的第三方软件。以下是在以下示例中用于编辑的 PDF 文档的内容。相同的方法适用于其他文档格式，源代码几乎没有任何区别。



{{< figure align=center src="images/original-doc.png" alt="">}}


## 在 Java 中查找和替换 PDF 中的单词或短语 {#replace-word-or-phrase}

您可以使用此功能隐藏任何私人数据，也可以从任何模板创建新的自定义文档。以下步骤说明了如何在 PDF 文档中查找任何单词/短语并将其替换为 Java 应用程序中的一些其他文本。

* **使用 [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor) 类加载** PDF 文件。
* 使用 [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction) 和 [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions) 查找确切的短语或单词。
* **使用 apply() 方法应用编辑**。
* **保存**使用 save() 方法更改的新文档。

以下代码使用 Java 查找并替换 PDF 文件中的单词。更准确地说，它通过将“John Doe”替换为单词“\[censored\]”来隐藏所有出现的“John Doe”。

```
// 在 PDF 中查找确切的短语并使用 Java 将其替换为其他文本
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
// 将编辑后的文件以不同的名称保存在不同的位置。
FileOutputStream stream = new FileOutputStream("path/exactPhrase.pdf");
RasterizationOptions rasterOptions = new RasterizationOptions();
rasterOptions.setEnabled(false);
redactor.save(stream, rasterOptions);
```

上述代码的输出如下。



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## 使用 Java 在 PDF 中查找和替换区分大小写的文本或短语 {#case-sensitive-text-redaction}

您可以执行区分大小写的搜索和编辑。以下代码使用 Java 替换 PDF 文档中区分大小写的单词“John Doe”而不是“john doe”。

```
// 在 PDF 中查找确切的短语（区分大小写) 并使用 Java 将其替换为其他文本
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
redactor.save();
```

代码的输出如下。



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## 用 Java 中的正则表达式 (RegEx) 替换 PDF 中的文本 {#replace-text-using-regex}

同样，您可以使用正则表达式替换任何特定的文本模式。以下步骤允许您在 Java 应用程序中使用正则表达式 (RegEx) 搜索后编辑 PDF。

* **使用 [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor) 类加载** PDF 文档。
* 使用带有 [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions) 的 [RegexRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction) 类查找正则表达式匹配。
* 使用 apply() 方法将更改应用于文档。
* **保存**使用适当的 save() 方法编辑的文档。

以下 Java 代码显示了如何使用 RegEx 在 PDF 文档中查找特定文本模式，然后用其他文本替换/隐藏它。

```
// 使用正则表达式在 PDF 中查找文本并使用 Java 将其替换为其他文本
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
redactor.save();
```

上述代码的输出如下。



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## 用Java中的彩色框替换文本 {#hide-text-with-colored-box}

如果您只想在 PDF 文件中隐藏搜索到的机密信息，您可以简单地在其上放置一个封面。 API 允许您隐藏搜索到的文本。以下代码将黑色矩形放置在 Java 中提到的私有文本上。

```
// 在 PDF 中查找文本并通过使用 Java 在其上绘制矩形来隐藏它
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new ExactPhraseRedaction("John Doe", true, new ReplacementOptions(java.awt.Color.BLACK)));
redactor.save();
```

上述代码的输出如下。



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们学习了如何使用不同的搜索技术在 PDF 文件中查找某些文本。后来，我们通过替换或隐藏 Java 应用程序中的文本来编辑 PDF 文件。更准确地说，我们对单词、短语进行了简单的搜索，搜索时区分大小写，并使用 Java 中的 RegEx。最后，我们使用其他文本或简单地用颜色将其隐藏来更改搜索结果。

有关 API 的更多详细信息，请访问 [文档](https://docs.groupdocs.com/redaction)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [用 Java 编辑 PDF 扫描文档](https://blog.groupdocs.com/2021/10/05/redact-text-and-scanned-images-using-java/)
* [使用 Java 在多个文件中搜索同义词](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/)
* [用Java构建全文搜索解决方案](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)





