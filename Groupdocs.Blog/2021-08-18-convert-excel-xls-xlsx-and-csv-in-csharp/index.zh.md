---
title: "在 C# 中将 Excel 转换为 CSV 和 CSV 到 Excel 格式"
date: Wed, 18 Aug 2021 03:39:00 +0000
draft: false
url: /zh/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
author: 'Shoaib Khan'
summary: "XLS 和 XLSX 是最常用和众所周知的 MS Excel 电子表格格式。您必须清楚了解本世纪 Microsoft Office 对这些格式的增强功能和无数格式选项。另一方面，**CSV** 文件是逗号分隔值，通常用于存储表格数据而无需格式化。这些文件可以在任何文本编辑器中查看，也可以在 MS Excel 中以表格格式查看。本文讨论了将**XLS/XLSX格式的Excel电子表格转换为CSV**格式和**CSV到XLS/XLSX**格式编程**使用C#**。"
tags: ['Convert XLS and CSV in C#', 'CSV to Excel', 'CSV to Excel in C#', 'CSV to XLSX in C#', 'Excel to CSV', 'Excel to CSV in C#', 'XLSX to CSV in C#']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-xlsx-to-csv-and-csv-to-excel-in-csharp.jpg" alt="在 C# 中将 XLS XLSX 转换为 CSV">}}


XLS 和 XLSX 是最常用和知名的 MS Excel 电子表格格式。您必须清楚了解本世纪 Microsoft Office 对这些格式的增强功能和无数格式选项。另一方面，**CSV** 文件是逗号分隔的值，通常用于存储表格数据而无需格式化。这些文件可以在任何文本编辑器中查看，也可以在 MS Excel 中以表格格式查看。本文指导将 **XLS/XLSX 格式的 Excel 电子表格转换为 CSV** 格式和 **CSV 到 XLS/XLSX **格式以编程方式**使用 C#**。

以下主题涵盖以下内容：

* [用于 XLS/XLSX 和 CSV 转换的 .NET API][1]
* [Excel 到 CSV 转换][2]
* [CSV 到 Excel 转换][3]

## 用于 Excel 文件和 CSV 转换的 .NET API {#excel-csv-dotnet-api}

[GroupDocs.Conversion][4] 提供了一个 .NET API，允许自动将各种文档和图像文件格式相互转换。我将使用此 API 将 XLSX 转换为 CSV，然后使用 C# 将 CSV 转换为 XLS 或 XLSX。除了电子表格格式，API 还支持 [许多其他文档和图像格式的来回转换][5]，如文字处理文档、演示文稿、电子书、JPG、PNG、WebP 等等。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 Excel (XLS/XLSX) 转换为 CSV {#excel-to-csv}

让我们从 XLS 或 XLSX 格式的表格和格式良好的数据开始，并将其转换为无格式的逗号分隔 CSV 格式。以下步骤允许在 .NET 应用程序中将 XLS 或 XLSX 格式转换为 CSV。

* 使用 [Converter][8] 类加载 Excel 文件（XLS 或 XLSX）。
* 设置起始工作表编号和工作表计数。 （选修的）
* 使用 [SpreadsheetConvertOptions][9] 将输出文件的转换格式设置为 CSV。
* 调用 [Convert][10] 方法将电子表格数据或特定页面转换为 CSV 格式。

以下代码显示了如何在 C# 中将 XLS 或 XLSX 转换为 CSV 格式。

```
// 在 C# 中将 Excel 电子表格转换为逗号分隔值 CSV 格式
string inputFile = @"path/spreadsheet.xlsx";
string outputFile = @"path/comma-sparated-values.csv";

using (Converter converter = new Converter(inputFile))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions
    {
        PageNumber = 2,
        PagesCount = 1,
        Format = SpreadsheetFileType.Csv // Specify the conversion format
    };
    converter.Convert(outputFile, options);
}
```

## 在 C# 中将 CSV 转换为 Excel (XLS/XLSX) {#csv-to-excel}

相反，如果您有逗号分隔的数据并且想要将其转换为格式良好的表格格式，则需要将该 CSV 数据转换为 XLS 或 XLSX 格式。以下步骤显示如何使用 C# 将 CSV 文件转换为 MS Excel XLSX 格式。

* 准备 CSV 文件的加载选项并定义分隔符。
* 使用 [Converter][11] 类加载 CSV。
* 使用 [SpreadsheetConvertOptions][12] 将转换格式设置为 XLSX。
* 使用 [Convert][13] 方法将 CSV 数据转换为 XLSX 格式。

以下代码显示了如何在 C# 中将 CSV 文件转换为 XLSX 格式。

```
// 在 C# 中将 CSV 文件转换为 XLS/XLSX 格式
string inputFile = @"path/comma-sparated-values.csv";
string outputFile = @"path/spreadsheet.xlsx";

Contracts.Func<LoadOptions> getLoadOptions = () => new CsvLoadOptions
{
    Separator = ','
};

using (Converter converter = new Converter(inputFile))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
    converter.Convert(outputFile, options);
}
```

只需相应地设置转换格式并提供适当的文件名以及 XLS 或任何其他文件格式的扩展名。

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][14] 以便在没有评估限制的情况下使用 API。

## 结论

总结这篇文章，您学习了使用 C# 来回转换 MS Excel 电子表格 XLS/XLSX 和 CSV 文件。您可以使用文档或通过体验 GitHub 上提供的示例来了解有关 .NET 转换自动化 API 的更多信息。通过 [论坛][15] 联系我们进行任何查询。

## 相关文章

* [将 CSV 转换为 Excel，以及（XLS 或 XLSX）在 Java 中转换为 CSV][16]

## 也可以看看

* [使用 C# 从 CSV 数据生成报告][17]
* [使用 C# 将 Excel 电子表格转换为 PDF][18]
* [使用 C# 将 JSON 转换为 CSV 和 CSV 到 JSON][19]
* [使用 C# 在 Word、Excel、PowerPoint 中插入 OLE 对象][20]







[1]: #excel-csv-dotnet-api
[2]: #excel-to-csv
[3]: #csv-to-excel
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/
[17]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[19]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[20]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/


