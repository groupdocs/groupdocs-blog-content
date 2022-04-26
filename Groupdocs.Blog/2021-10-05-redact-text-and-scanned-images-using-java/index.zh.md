---
title: "用 Java 编辑 PDF 扫描文档"
date: Tue, 05 Oct 2021 04:21:00 +0000
draft: false
url: /zh/2021/10/05/redact-text-and-scanned-images-using-java/
author: 'Shoaib Khan'
summary: "想要保护文档中的秘密或敏感信息？即使这是常规的文本信息，或者是带有图像的扫描文档的文本，它也是可行的。之前的文章可能会帮助您优化搜索，我们在其中讨论了[搜索单词的不同策略][1] 和 [在多个文档中搜索同义词][2]。本文将指导您了解**如何使用 Java 编辑 PDF 文本和文档中图像中的文本**。"
tags: ['Blackout Text', 'Blackout Text in PDF', 'redact documents', 'Redact in Java', 'Redact PDF files', 'Redact PDF in Java', 'Redact Text in Image', 'Redact Text in Java', 'Redact Text in PDF']
categories: ['GroupDocs.Redaction Product Family']
---

想要保护文档中的秘密或敏感信息？即使这是常规的文本信息，或者是带有图像的扫描文档的文本，它也是可行的。之前的文章可能会帮助您优化搜索，我们在其中讨论了[搜索单词的不同策略][3] 和 [在多个文档中搜索同义词][4]。本文将指导您了解**如何使用 Java 编辑 PDF 文本和文档中图像中的文本**。

下面将介绍以下主题：

* [文本和图像编辑 - Java API][5]
* [使用 Java 编辑 PDF 文本和扫描信息][6]

## 用于文本和图像编辑的 Java API {#redaction-java-api}

GroupDocs.Redaction 提供了[保护机密信息的编辑解决方案][7]。它的 Java API 允许您从基于 Java 的应用程序中编辑或删除各种文件格式的文档中的机密信息。除了简单的文本编辑和光栅化之外，API 还允许识别图像中的文本，这些文本可能已经在任何文档中，例如最常用的扫描 PDF 文件。文档中提供了 [支持的文件格式][8] 的完整列表。

### 下载或配置

您可以从 [下载部分][9] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-redaction</artifactId>
        <version>21.6</version> 
</dependency>
```

## 使用 Java 编辑 PDF 文本和扫描的图像文本 {#redact-text-and-scanned-text}

我们已经讨论了不同的[在文档中查找和替换文本的方法][10]。但是，我们也可以编辑图像中的文本。我将使用以下 PDF 文档，其中包含一些文本以及带有一些文本的图像。为此，我们需要将 OCR 与编辑过程结合起来。首先，我们将识别文档中的文本以及文档图像中的文本。然后，我们将用黑框覆盖它，以编程方式隐藏任何法律、机密或秘密信息，即使是扫描文档图像中的文本。



{{< figure align=center src="images/PDF-with-text-and-scanned-image.jpg" alt="带有文本和扫描图像的 PDF">}}


以下步骤将检测并替换 PDF 文档中包含常规文本或嵌入图像中的任何文本的文本。

* 使用任何 OCR 连接器准备编辑器设置。
* 使用 [Redactor][11] 类以及是否需要任何特定的加载选项来加载您的 PDF 文件。
* 定义您的 [替换选项][12]。我选择将文本涂黑。
* 准备编辑；使用适当的编辑策略，如 [Phrase Redaction][13] 或 [RegEx redaction][14]。
* 使用 [apply][15] 方法应用编辑。
* 使用 [save][16] 方法保存编辑过的文档。

以下源代码使用 Java 编辑 PDF 文档中的选定文本。

```
// 使用 Java 编辑 PDF 中的文本和图像中的文本，如扫描文档
RedactorSettings settings = new RedactorSettings(new AsposeCloudOcrConnector());
try (Redactor redactor = new Redactor("path/document.pdf", new LoadOptions(), settings))
{
    ReplacementOptions marker = new ReplacementOptions(java.awt.Color.BLACK);
    Redaction redactions[] = new Redaction[] {
            new RegexRedaction("(?<=Dear\\s)([^,]+)", marker), // cardholder name
            new RegexRedaction("\\d{2}/\\d{2}", marker), // valid thru
            new RegexRedaction("\\d{4}", marker)  // card number parts
        };
    RedactorChangeLog result = redactor.apply(redactions);
    if (result.getStatus() != RedactionStatus.Failed)
    {
        redactor.save(new SaveOptions(false, "redacted"));
    }
}
```

上述代码的输出如下所示，其中 PDF 文档的选定文本被涂黑。



{{< figure align=center src="images/Redacted-PDF-with-text-and-scanned-image.jpg" alt="编辑 PDF 文本和扫描的图像文本">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][17] 使用 API 而不受评估限制。

## 结论

最后，您已经学会了如何编辑文档中的文本。此外，我们还讨论了如何使用 Java 编辑 PDF 文档中图像中的文本。同样，您可以使用任何其他格式的文档编辑文本和图像。我们使用了正则表达式编辑，但是，它也可以使用许多不同的方式来完成。后来我们用黑匣子隐藏了搜索结果。

如需了解有关 API 的更多详细信息，请访问 [文档][18]。如有疑问，请通过 [论坛][19] 联系我们。

## 也可以看看

* [使用Java查找和替换文档中的单词][20]
* [在Java文档中查找和删除水印][21]
* [在Java中添加或删除PDF文件的注释][22]







[1]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[2]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[3]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[4]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[5]: #redaction-java-api
[6]: #redact-text-and-scanned-text
[7]: https://products.groupdocs.com/redaction/
[8]: https://docs.groupdocs.com/redaction/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/redaction
[10]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[11]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor
[12]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions
[13]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction
[14]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction
[15]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#apply(com.groupdocs.redaction.Redaction)
[16]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#save()
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/redaction
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[21]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[22]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/


