---
title: "在 Java 中将文档转换为 Excel XLS、XLSX"
date: Sat, 22 May 2021 18:39:23 +0000
draft: false
url: /zh/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/
author: 'Shoaib Khan'
summary: "对于 PDF 和 Word 文档的表格形式的数据，您有时需要将其转换为 Excel 电子表格。我们需要将尽可能多的文档自动转换为电子表格或多个工作簿。本文将讨论如何以编程方式将 Word 文档转换为 Excel，以及如何将 PDF 文件转换为 Java 中的 Excel 电子表格。"
tags: ['Convert to Excel in Java', 'DOC to XLS in Java', 'DOCX to XLSX in Java', 'PDF to Excel in Java', 'Word to Excel in Java']
categories: ['GroupDocs.Conversion Product Family']
---

对于 PDF 和 Word 文档的表格形式的数据，您有时需要将其转换为 Excel 电子表格。我们需要将尽可能多的文档自动转换为电子表格或多个工作簿。本文将讨论如何以编程方式将 Word 文档转换为 Excel，以及如何将 PDF 文件转换为 Java 中的 Excel 电子表格。



{{< figure align=center src="images/pdf-word-to-xls-in-java.jpg" alt="在 Java 中将 Word 和 PDF 转换为 Excel">}}


此处简要讨论以下主题：

* [Java API - 文档到电子表格的转换][2]
* [将 PDF 转换为 Excel 电子表格][3]
* [将Word转换为Excel电子表格][4]
* [PDF 或 Word 到电子表格的转换具有更多选项][5]

## 用于转换为电子表格的 Java API {#convert-to-spreadsheet-java-api}

[GroupDocs.Conversion for Java][6] 是允许您在 Java 应用程序中将 PDF 和 Word 文档转换为电子表格的 API。 API 允许以多种文件格式进行文档和图像转换。一些受支持的文档格式包括文字处理文档、电子表格、演示文稿、电子书、AutoCAD 格式、PDF、电子邮件、网页、图像。

### 下载并配置

您可以从下载部分获取转换库，或在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置。之后，您可以尝试本文的示例以及 [GitHub][7] 上提供的更多示例。有关详细信息，您可以访问 [API 参考][8]。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.4</version> 
</dependency>
```

## 在 Java 中将 PDF 转换为 Excel {#pdf-to-excel-csharp}

可以按照以下步骤将任何 PDF 文档转换为 Excel 电子表格。

* 使用 [Converter][9] 类加载 PDF 文件。
* 使用 [SpreadsheetConvertOptions][10] 准备转换选项。
* 使用创建的选项调用 [convert][11] 方法。

以下代码示例展示了如何将 PDF 文件转换为 Java 中的 Excel XLSX 电子表格。

```
// 在 Java 中将 PDF 文档转换为 Excel 电子表格
Converter converter = new Converter("document.pdf");
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
converter.convert("pdfToExcel.xlsx", options);
```

## 在 Java 中将 Word 转换为 Excel {#word-to-excel-csharp}

同样，任何 Word 文档都可以转换为 Excel 电子表格，方法与我们刚刚转换 PDF 文档的方式相同。提供正确的源文件并将其转换为 XLS 或 XLSX。

以下是将任何 DOC DOCX 文件转换为 Excel 电子表格的步骤。

* 使用 Converter 类加载 DOC、DOCX 文件。
* 使用 SpreadsheetConvertOptions 准备转换选项。
* 使用选项调用Converter 类的convert 方法。

以下源代码显示了如何将 DOC 或 DOCX 文件转换为 Java 中的 Excel XLSX 格式。

```
// 在 Java 中将 Word 文档转换为 Excel 电子表格
Converter converter = new Converter("document.docx");
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
converter.convert("wordToExcel.xlsx", options);
```

## 使用 Java 提供更多选项的 PDF 或 Word 到电子表格的转换 {#pdf-word-to-excel-adv}

您不必每次都转换整个文档。您可以只转换文档的选定页面。 API 让您有权使用各种选项转换文档，其中包括：

* 开始**页码**。
* **页数**。
* **特定页面**用于转换。
* **格式**要转换成。
* **密码** 用于使文件受到保护。
* **缩放**使其变大或变小。
* **水印**在转换器文件上。

以下是如何在 Java 中将 PDF 文件的某些页面转换为具有不同缩放比例的 XLSX 格式的步骤。

```
// 使用一些选项将 PDF 文件的第二页转换为 Java 中的 Excel
Converter converter = new Converter("document.pdf");
SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
options.setPageNumber(2);
options.setPagesCount(1);
options.setFormat(SpreadsheetFileType.Xlsx);
options.setZoom(120);

converter.convert("pdfToExcelAdv.xlsx", options);
```

PDF 文件和转换后的电子表格作为输出显示在这里。它将 PDF 文件的第二页转换为 XLSX 格式。



{{< figure align=center src="images/pdf-to-xls-in-csharp.jpg" alt="以编程方式将 PDF 转换为 Excel XLS XLSX">}}


## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][12] 以便在没有评估限制的情况下使用 API。

## 结论

在本文中，我们讨论了将 PDF 和 Word 文档转换为 Java 中的 Excel 电子表格。此外，我们还学习了如何使用水印、缩放等选项转换文档的任何部分，并使用密码保护对其进行保护。

有关更多选项和示例，请访问 [文档][13] 和 [GitHub][14] 存储库。如需查询，请通过 [论坛][15] 联系我们。

## 也可以看看

* [Java 中的图像到 PDF][16]
* [Java 中的电子表格到 PDF][17]
* [Java 中的 PDF 演示文稿][18]
* [Java 中的 CAD 图纸到 PDF][19]







[1]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java
[2]: #convert-to-spreadsheet-java-api
[3]: #pdf-to-excel-csharp
[4]: #word-to-excel-csharp
[5]: #pdf-word-to-excel-adv
[6]: https://products.groupdocs.com/conversion/net
[7]: https://github.com/groupdocs-conversion
[8]: https://apireference.groupdocs.com/conversion/java
[9]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[10]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/conversion
[14]: https://github.com/groupdocs-conversion
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[17]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[18]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
[19]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/


