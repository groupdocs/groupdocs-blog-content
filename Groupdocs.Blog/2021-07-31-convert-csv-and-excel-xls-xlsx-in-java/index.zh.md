---
title: "在 Java 中将 CSV 转换为 Excel (XLS XLSX) & Vice Versa"
date: Sat, 31 Jul 2021 04:07:00 +0000
draft: false
url: /zh/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/
author: 'Shoaib Khan'
summary: "**CSV** 包含逗号分隔的值，通常用于存储不带格式的表格数据。这些文件可以在任何文本编辑器中查看，也可以在 MS Excel 中以表格格式查看。另一方面，MS Excel 文件最常用的格式是 XLS 和 XLSX。这些格式支持无数的格式化选项。本文讨论 **XLS/XLSX 格式到 CSV** 格式和 **CSV 到 XLS/XLSX **格式编程**使用 Java** 的 Excel 电子表格的转换。"
tags: ['Convert XLS and CSV in Java', 'CSV to Excel in Java', 'CSV to XLS in Java', 'CSV to XLSX in Java', 'Excel to CSV in Java', 'XLS to CSV in Java', 'XLSX to CSV in Java']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-csv-and-xls-xlsx-in-java.jpg" alt="在 Java 中转换为 CSV 和 XLS XLSX">}}


**CSV** 包含逗号分隔的值，通常用于存储不带格式的表格数据。这些文件可以在任何文本编辑器中查看，也可以在 MS Excel 中以表格格式查看。另一方面，MS Excel 文件最常用的格式是 XLS 和 XLSX。这些格式支持无数的格式化选项。本文讨论 **XLS/XLSX 格式到 CSV** 格式和 **CSV 到 XLS/XLSX **格式编程**使用 Java** 的 Excel 电子表格的转换。

以下主题涵盖以下内容：

* [用于 XLS/XLSX 和 CSV 转换的 Java API][1]
* [Excel 到 CSV 转换][2]
* [CSV 到 Excel 转换][3]

## 用于 Excel 文件和 CSV 转换的 Java API {#excel-csv-java-api}

[GroupDocs.Conversion][4] 提供了允许将电子表格格式相互转换的 Java API。我将使用此 API 将 XLSX 转换为 CSV，以及使用 Java 将 CSV 转换为 XLS 或 XLSX。此外，API 允许 [来回转换许多其他文档和图像格式][5]，如文字处理文档、演示文稿、电子书、JPG、PNG、WebP 等等。

### 下载或配置

您可以从 [下载部分][6] 下载 **JAR** 文件，或者只获取 **基于 maven 的** Java 应用程序的 pox.xml 的存储库和依赖项配置。

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
        <version>21.7</version> 
</dependency>
```

## 在 Java 中将 CSV 转换为 Excel (XLS/XLSX) {#csv-to-excel}

将逗号分隔的数据转换为表格形式以便更好地呈现需要从 CSV 转换为 XLS/XLSX 格式。以下步骤允许在 Java 应用程序中将 CSV 文件转换为 XLS/XLSX 格式。

* 准备加载 CSV 文件的加载选项。
* 使用 [Converter][7] 类加载 CSV。
* 使用 [SpreadsheetConvertOptions][8] 将转换格式设置为 XLSX。
* 调用 **convert** 方法将 CSV 数据转换为 XLSX 格式。

以下代码显示了如何将 CSV 文件转换为 Java 中的 XLSX 格式。

```
// 在 Java 中将 CSV 文件转换为 XLS/XLSX 格式
CsvLoadOptions loadOptions = new CsvLoadOptions();
loadOptions.setSeparator(',');
Converter converter = new Converter("path/comma-sparated-values.csv", loadOptions);

SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
options.setFormat(SpreadsheetFileType.Xlsx);

converter.convert("path/spreadsheet.xlsx", options);
```

对于 XLS 格式，只需相应地设置转换格式并提供适当的文件名和扩展名。

## 在 Java 中将 Excel (XLS/XLSX) 转换为 CSV {#excel-to-csv}

同样，如果不需要格式化，您可以删除样式和视觉效果，并通过将 XLS/XLSX 转换为 CSV 格式并节省空间来简单地保留逗号分隔的数据。

以下步骤允许在 Java 应用程序中将 XLS 或 XLSX 格式转换为 CSV。

* 使用 [Converter][9] 类加载 Excel 文件（XLS 或 XLSX）。
* 使用 [SpreadsheetConvertOptions][10] 将转换格式设置为 CSV。
* 调用**convert** 方法将电子表格数据转换为CSV 格式。

以下代码显示了如何在 Java 中将 XLS 或 XLSX 转换为 CSV 格式。

```
// 在 Java 中将 Excel 电子表格转换为逗号分隔值 CSV 格式
Converter converter = new Converter("path/spreadsheet.xlsx");

SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
options.setFormat(SpreadsheetFileType.Csv); // Specify the conversion format

converter.convert("path/convertedfile.csv", options);
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][11] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您学习了如何使用 Java 应用程序以编程方式将 MS Excel 文件转换为 CSV 格式，以及如何将 CSV 文件转换为 XLS 和 XLSX 格式。您可以使用 [文档][12] 或通过 [GitHub][13] 上提供的示例了解有关 Java 转换 API 的更多信息。如有任何疑问，请在 [论坛][14] 上与我们联系。

## 也可以看看

* [用 Java 从 CSV 数据生成报告][15]
* [用 Java 从 XML 数据创建报告][16]
* [在 Java 中将 Excel 电子表格转换为 PDF][17]
* [在Java中将PDF、Word文档转换为Excel XLS、XLSX][18]







[1]: #excel-csv-java-api
[2]: #excel-to-csv
[3]: #csv-to-excel
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[8]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[9]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[10]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/conversion
[13]: https://github.com/groupdocs-conversion
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[16]: https://blog.groupdocs.com/2021/07/10/generate-reports-from-xml-data-in-java/
[17]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[18]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/


