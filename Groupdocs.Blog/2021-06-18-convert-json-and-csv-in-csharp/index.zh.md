---
title: "使用 C# 将 JSON 转换为 CSV 和 CSV 到 JSON"
date: Fri, 18 Jun 2021 12:25:49 +0000
draft: false
url: /zh/2021/06/18/convert-json-and-csv-in-csharp/
author: 'Shoaib Khan'
summary: "**JSON**（JavaScript Object Notation）是一种人类可读的结构化数据格式。它广泛用于存储和传递数据的 API、应用程序和配置。 **CSV** 包含逗号分隔值，通常用于存储可以使用 MS Excel 等电子表格应用程序完美显示的表格数据。为了传输表格数据或将接收到的结构化数据存储为表格形式，需要将格式相互转换。本文讨论 **JSON 到 CSV** 格式和 **CSV 到 JSON** 格式的转换**使用 C#** 为您的 .NET 应用程序编程。"
tags: ['Convert CSV in CSharp', 'Convert JSON in CSharp', 'CSV to JSON in CSharp', 'JSON to CSV in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-csv-and-json-in-csharp.jpg" alt="在 CSharp .NET 中转换为 CSV 和 JSON">}}


**JSON**（JavaScript Object Notation）是一种人类可读的结构化数据格式。它广泛用于存储和传递数据的 API、应用程序和配置。 **CSV** 包含逗号分隔值，通常用于存储可以使用 MS Excel 等电子表格应用程序完美显示的表格数据。为了传输表格数据或将接收到的结构化数据存储为表格形式，需要将格式相互转换。本文讨论 **JSON 到 CSV** 格式和 **CSV 到 JSON** 格式的转换**使用 C#** 为您的 .NET 应用程序编程。

以下主题涵盖以下内容：

* [用于 JSON 和 CSV 转换的 .NET API][1]
* [JSON 到 CSV 转换][2]
* [CSV 到 JSON 转换][3]

## 用于 JSON 和 CSV 转换的 .NET API {#json-csv-dotnet-api}

[GroupDocs.Conversion][4] 具有允许将 JSON 和 CSV 文件相互转换的 API。在本文中，我们将使用 GroupDocs.Conversion 的 .NET API 将 JSON 转换为 CSV，然后使用 C# 将 CSV 转换为 JSON。此外，API 允许 [来回转换各种其他文档格式][5]，如文字处理文档、电子表格、演示文稿、电子书、图像等等。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 JSON 转换为 CSV {#json-to-csv}

以下步骤允许在 .NET 应用程序中将 JSON 文件转换为 CSV 格式。

* 使用 [Converter][8] 类加载 JSON。
* 使用 [SpreadsheetConvertOptions][9] 将转换格式设置为 CSV。
* 调用 [Convert][10] 方法将 JSON 数据转换为 CSV 格式。

以下代码展示了如何使用 C# 将 JSON 转换为 CSV 格式。

```
// 在 C# 中将 JSON 文件转换为 CSV 格式
using (Converter converter = new Converter(@"path/sample.json"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions()
    {
        Format = SpreadsheetFileType.Csv
    };
                
    converter.Convert(@"path/JsonToCSV.csv", options);
}
```

## 在 C# 中将 CSV 转换为 JSON {#csv-to-json}

以下步骤允许在 .NET 应用程序中将 CSV 文件转换为 JSON 格式。

* 准备加载 CSV 文件的加载选项。
* 使用 [Converter][11] 类加载 CSV。
* 使用 [DataConvertOptions][12] 将转换格式设置为 JSON。
* 调用[Convert][13]方法将CSV数据转换成JSON格式。

以下代码显示了如何使用 C# 将 CSV 文件转换为 JSON 格式。

```
// 在 C# 中将 CSV 文件转换为 JSON 格式
var loadOptions = new CsvLoadOptions
{
    Separator = ','
};

using (Converter converter = new Converter(@"path/sample.csv", ()=> loadOptions))
{
    DataConvertOptions options = new DataConvertOptions
    {
        Format = DataFileType.Json
    };
    converter.Convert(@"path/CsvToJSON.json", options);
}
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][14] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您学习了如何使用 C# 以编程方式将 JSON 文件转换为 CSV 格式以及将 CSV 文件转换为 JSON 格式。您可以使用 [文档][15] 或通过 [GitHub][16] 上提供的示例了解有关 .NET 转换 API 的更多信息。在 [论坛][17] 上与我们联系。

## 也可以看看

* [在 C# 中将 Excel 转换为 CSV 和 CSV 到 Excel 格式][18]
* [在 C# 中从 JSON 数据生成报告][19]
* [在 C# 中从 CSV 和 XML 数据生成报告][20]







[1]: #json-csv-dotnet-api
[2]: #json-to-csv
[3]: #csv-to-json
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://docs.groupdocs.com/conversion/net/
[16]: https://github.com/groupdocs-conversion
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
[19]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[20]: https://blog.groupdocs.com/2019/10/21/generate-reports-from-csv-xml-in-csharp/


