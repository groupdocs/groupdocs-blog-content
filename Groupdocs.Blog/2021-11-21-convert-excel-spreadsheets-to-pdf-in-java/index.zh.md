---
title: "在 Java 中将 Excel 电子表格转换为 PDF"
date: Sun, 21 Nov 2021 07:32:11 +0000
draft: false
url: /zh/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "当我们想要共享不需要编辑的工作表中的数据时，我们经常将此类 Excel 工作簿或特定工作表转换为 PDF 格式。在本文中，我们将学习**使用文档转换 API 将 Excel 电子表格转换为 Java 中的 PDF 格式的 4 种不同方法**。"
tags: ['Convert Excel in Java', 'Convert Excel to PDF', 'Convert Excel to PDF in Java', 'convert to PDF in java', 'Excel to PDF', 'Excel to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/excel-to-pdf-in-java.jpg" alt="在 Java 中将 Excel 电子表格转换为 PDF">}}


当我们想要共享不需要编辑的工作表中的数据时，我们经常将此类 Excel 工作簿或特定工作表转换为 PDF 格式。在本文中，我们将学习**使用文档转换 API 将 Excel 电子表格转换为 Java 中的 PDF 格式的 4 种不同方法**。

每种转换方法都可以在加载电子表格时对代码稍作更改或对 PDF 格式的转换选项进行一些调整来采用。本文中转换电子表格的一些可能方法如下。

* [Java API 用于 Excel 文件到 PDF 的转换][1]
* [将所有工作表转换为 PDF][2]
* [连续数Excel表格转PDF][3]
* [Excel表格转PDF的具体列表][4]
* [将所选单元格范围从 Excel 工作表转换为 PDF][5]

## 用于将 Excel 文件转换为 PDF 的 Java API {#excel-conversion-java-api}

[GroupDocs.Conversion][6] 提供 Java API，允许将包括 XLS、XLSX 在内的多种 Excel 文件格式转换为 PDF 格式。在本文中，我们将使用它的 [GroupDocs.Conversion for Java][7]。除了电子表格，API 还支持 [documentation][8] 中提到的文字处理文档、演示文稿、电子书、图像等的转换。

您可以从 [下载部分][9] 下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][10] 配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.10</version> 
</dependency>
```

## 将所有 Excel 文件转换为 PDF - Java {#excel-to-pdf}

最简单的方法是将所有工作表转换为 PDF 格式。以下步骤将完整的工作簿（所有工作表）转换为 Java 中的 PDF 格式。

* **使用 [Converter][11] 加载 Excel**（XLS、XLSX）工作簿。
* 使用 [PdfConvertOptions][13] 使用任何重载的 [convert()][12] 方法将其转换为 PDF 格式。

以下是将完整的 Excel 工作簿转换为 PDF 的 2 行 Java 源代码。

```
/*
 * Convert all the Excel sheets to PDF format in Java
 */
Converter converter = new Converter("path/spreadsheet.xlsx");
converter.convert("path/all-sheets-converted.pdf", new PdfConvertOptions());
```



{{< figure align=center src="images/Converted-Excel-to-PDF.png" alt="从 Excel 数据转换 PDF">}}


## 将 Excel 表格连续转换为 PDF - Java {#successive-sheets-to-pdf}

如果您有兴趣按顺序提取电子表格的子集，您可以通过提供起始工作表编号和连续工作表的数量来轻松完成。以下是将 Excel 工作簿工作表的任何子序列转换为 Java 中的 PDF 格式的步骤。

* **使用 [转换器][14] 加载**电子表格。
* 使用 [PdfConvertOptions][15] 定义**PDF 转换选项**。
* 设置**起始张数**和**后续张数**。
* **根据使用 [convert()][16] 方法的设置将选定的工作表转换为 PDF。

以下是将前两张表转换为 PDF 的 Java 代码片段。 （工作表编号**1 和 2**）

```
/*
 * Convert sequence of Excel sheets to PDF format in Java
 */
Converter converter = new Converter("path/spreadsheet.xlsx");

PdfConvertOptions convertOptions = new PdfConvertOptions();
convertOptions.setPageNumber(1);
convertOptions.setPagesCount(2);

converter.convert("path/sequential-conversion.pdf", convertOptions);
```

## 特定的 Excel 表格到 PDF 的转换 - Java {#list-of-sheets-to-pdf}

如果您正在考虑转换随机工作表（如工作表编号 1、2、4、7，...），您可以在转换时简单地提供确切的工作表编号作为列表。以下是将任何特定的图纸编号列表转换为 Java 中的 PDF 格式的步骤。

* **使用 [转换器][17] 加载** Excel 文件。
* **使用 [PdfConvertOptions][18] 以列表形式提供准确的工作表编号**。
* **使用 [convert()][19] 方法将列出的工作表转换为 PDF 格式。

以下代码片段将工作表编号 **1 和 3** 转换为 PDF 格式。

```
/*
 * Convert the specified list of Excel sheets to PDF format in Java
 */
Converter converter = new Converter("path/spreadsheet.xlsx");

PdfConvertOptions convertOptions = new PdfConvertOptions();
convertOptions.setPages(Arrays.asList(1,3));

converter.convert("path/specific-sheets-conversion.pdf", convertOptions);
```

## 将 Excel 工作表的单元格范围转换为 PDF - Java {#cell-ranges-to-pdf}

这是转换电子表格任何部分的不寻常方法。我们可以以与上面讨论的其他方法几乎相似的方式转换 Excel 工作表的任何单元格范围。以下是在 Java 中将工作簿工作表的单元格范围转换为 PDF 格式的步骤。

* 定义工作表的**单元格范围**。
* **加载**电子表格文件。
* **通过提供连续的工作表范围或确切的工作表编号来选择工作表**。
* **根据设置将工作表转换为 PDF 格式。

以下代码将工作表编号 1 的单元格区域 (A1:C20) 转换为 Java 中的 PDF 格式。

```
/*
 * Convert the specified Cell Range of specified Excel sheets to PDF format in Java
 */
// 为源 XLSX 文件准备加载选项和范围
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
loadOptions.setConvertRange("A1:C20");
Converter converter = new Converter("path/spreadsheet.xlsx", loadOptions);

PdfConvertOptions convertOptions = new PdfConvertOptions();
convertOptions.setPageNumber(1);
convertOptions.setPagesCount(1);

converter.convert("path/convert-cell-range.pdf", convertOptions);
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][20] 以便在没有评估限制的情况下使用 API。

## 结论

让我们总结一下我们今天学到的东西。我们学习了使用 GroupDocs.Conversion 将 Excel 电子表格转换为 Java 中的 PDF 格式的四种不同方法。最初，我们将完整的工作簿转换为 PDF 格式，然后是连续的工作表。接下来，通过列出确切的图纸编号，将多张图纸更改为 PDF。最后，我们从选定工作表的选定单元格范围中获取 PDF 文件。

从 [文档][21] 中了解有关 **GroupDocs.Conversion API** 的更多信息。如有疑问，请通过 [论坛][22] 联系我们。

## 也可以看看

* [在 Java 中转换 CSV 和 Excel (XLS XLSX)][23]
* [在Java中将文档转换为Excel（XLS，XLSX）][24]
* [Java 中的水印 Excel 工作表][25]
* [Java 中的水印 PDF 文件][26]


[1]: #excel-conversion-java-api
[2]: #excel-to-pdf
[3]: #successive-sheets-to-pdf
[4]: #list-of-sheets-to-pdf
[5]: #cell-ranges-to-pdf
[6]: https://products.groupdocs.com/conversion/
[7]: https://products.groupdocs.com/conversion/java/
[8]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/conversion
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-conversion
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[19]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[20]: https://purchase.groupdocs.com/temporary-license
[21]: https://docs.groupdocs.com/conversion
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/
[24]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/
[25]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[26]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/