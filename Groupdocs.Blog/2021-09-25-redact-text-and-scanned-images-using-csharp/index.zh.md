---
title: "在 C# 中编辑 PDF 扫描文档"
date: Sat, 25 Sep 2021 09:31:01 +0000
draft: false
url: /zh/2021/09/25/redact-text-and-scanned-images-using-csharp/
author: 'Shoaib Khan'
summary: "我们经常需要在文档中隐藏机密和敏感信息。在其他文章中，我们讨论了在多个文档中搜索单词甚至搜索同义词的不同策略。本文将指导您了解**如何使用 C#** 在文档中编辑 PDF 文本和图像中的文本。"
tags: ['Blackout Text', 'Blackout Text in PDF', 'redact documents', 'Redact in CSharp', 'redact pdf', 'Redact PDF in CSharp', 'Redact Text in CSharp', 'Redact Text in Image', 'Redact Text in PDF']
categories: ['GroupDocs.Redaction Product Family']
---

我们经常需要在文档中隐藏机密和敏感信息。在其他文章中，我们讨论了[搜索单词的不同策略][1]，甚至[在多个文档中搜索同义词][2]。本文将指导您了解**如何使用 C#** 在文档中编辑 PDF 文本和图像中的文本。

下面将介绍以下主题：

* [文本和图像编辑 - .NET API][3]
* [使用 C# 编辑 PDF 文本和扫描的信息][4]

## 用于文本和图像编辑的 .NET API {#redaction-dotnet-api}

[GroupDocs.Redaction][5] 提供了 [document redaction .NET API][6]，允许在各种文件格式的文档中隐藏和删除机密信息。除了简单的文本编辑和光栅化之外，API 还允许识别图像中的文本，这些文本可能已经在任何文档中，例如最常用的扫描 PDF 文件。文档中提供了 [支持的文件格式][7] 的完整列表。

您可以从 [下载部分][8] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][9] 在您的 .NET 应用程序中安装 API。

### 通过包管理器控制台安装```
PM> Install-Package GroupDocs.Redaction
```

### Install via NuGet Package Manager



{{< figure align=center src="images/GroupDocs.Redaction-NuGet-Package-Install-1024x802.jpg" alt="GroupDocs.Redaction - NuGet Package - Install">}}


## Redact PDF Text and Scanned Image Text using C# {#redact-text-and-scanned-text}

There are many different [ways to find and replace text in documents][10] that have already been discussed. You can find specific words in any document, find with case sensitivity, or by using regular expressions. I will be using the following PDF document, that contains some text and also an image with some text in it. Here we will combine the OCR and redaction process using GroupDocs.Redaction for .NET. Firstly, we will identify the text in the document and also the text which is inside the image of the document. Secondly, we will cover it with a black box to demonstrate how to programmatically hide any legal or confidential information even if is as text within a scanned document image.



{{< figure align=center src="images/PDF-with-text-and-scanned-image.jpg" alt="PDF with text and scanned image">}}


The following steps will detect and replace the text in a PDF document, that contains regular text along with some text within an embedded image.

*   Prepare the redactor settings using any OCR Connector.
*   Load the PDF document using [Redactor][11] class with the prepared settings and any specific loading options.
*   Define the [replacement option][12]. I have defined to black out the text.
*   For the text redaction, use the appropriate text selection strategy. I have used [RegEx][13].
*   Apply the redactions using the [Apply][14] method.
*   Save the redacted document using [Save][15] method.

The following source code redacts the selected text within a PDF document using C#.

{{< gist GroupDocsGists f7e22d6719c21108d804756913b2ca3f "RedactTextInImage.cs" >}}

The output of the above code is as follows that black out the selected text of the PDF document.



{{< figure align=center src="images/Redacted-PDF-with-text-and-scanned-image.jpg" alt="Redact PDF text and scanned image text">}}


## Get a Free API License

You can [get a free temporary license][16] to use the API without the evaluation limitations.

## Conclusion

To sum up, you have learned to redact text in documents. More importantly and precisely, we discussed how to redact text in images within a PDF document using C#. We selected the text to redact using regular expressions, however, it can be selected using many different ways as discussed earlier. Later we blackout the search results using a black rectangle box over the searched text.

For more details to learn about the API, visit the [documentation][17]. For queries, contact us via the [forum][18].

## See Also

*   [Find and Replace Words in Documents using C#][19]
*   [Find and Remove Watermarks from Documents in C#][20]
*   [Add or Remove Annotations within Word files using C#][21]







[1]: https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/
[2]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[3]: #redaction-dotnet-api
[4]: #redact-text-and-scanned-text
[5]: https://products.groupdocs.com/redaction/
[6]: https://products.groupdocs.com/redaction/net/
[7]: https://docs.groupdocs.com/redaction/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/redaction
[9]: https://www.nuget.org/packages/groupdocs.redaction
[10]: https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/
[11]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor
[12]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions
[13]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction
[14]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index
[15]: https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/redaction
[18]: https://forum.groupdocs.com/
[19]: https://blog.groupdocs.com/2021/08/04/find-and-replace-text-in-documents-using-csharp/
[20]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[21]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/


