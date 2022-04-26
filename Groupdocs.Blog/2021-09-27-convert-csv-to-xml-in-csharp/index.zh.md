---
title: "在 C# 中将 CSV 转换为 XML"
date: Mon, 27 Sep 2021 12:59:00 +0000
draft: false
url: /zh/2021/09/27/convert-csv-to-xml-in-csharp/
author: 'Shoaib Khan'
summary: "CSV 和 XML 是开发人员使用的最流行的文件格式之一。这些格式通常用于在应用程序内部和应用程序之间存储和交换数据。在存储或传输信息之前，通常需要将一种格式转换为另一种格式。在本文中，您将了解**如何使用 C# 以编程方式将 CSV（逗号分隔值）文件转换为 XML 格式**。"
tags: ['Convert CSV to XML', 'Convert CSV to XML in CSharp', 'CSV to XML', 'CSV to XML in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

CSV 和 XML 是开发人员使用的最流行的文件格式之一。这些格式通常用于在应用程序内部和应用程序之间存储和交换数据。在存储或传输信息之前，通常需要将一种格式转换为另一种格式。在本文中，您将了解**如何使用 C# 以编程方式将 CSV（逗号分隔值）文件转换为 XML 格式**。



{{< figure align=center src="images/convert-csv-to-xml-using-csharp.jpg" alt="使用 CSharp 将 CSV 转换为 XML">}}


本文涵盖以下主题：

* [.NET API - CSV 到 XML 的转换][1]
* [如何在 C# 中将 CSV 转换为 XML][2]

## .NET API 用于 CSV 到 XML 的转换 {#csv-to-xml-dotnet-api}

[GroupDocs.Conversion][3] 提供允许 CSV 和 XML 文件转换的 API。在本文中，我们将使用 GroupDocs.Conversion 的 .NET API 使用 C# 将 CSV 格式数据转换为 XML 格式。此外，API 支持许多其他文件格式进行转换，如文字处理文档、电子表格、演示文稿、电子书、图像等。

您可以从 [下载部分][4] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][5] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 CSV 转换为 XML {#csv-to-xml}

可以使用 MS Excel 等编辑器查看和可视化编辑 CSV 文件。该图像显示了我用于转换的 CSV 数据。网上有许多 CSV 到 XML 转换器，但是，本节中提到的代码可以通过这种简单的转换为您的 .NET 应用程序提供支持。



{{< figure align=center src="images/csv-sample-file-opened-in-excel.jpg" alt="在 Excel 中打开的 CSV 示例文件">}}


以下步骤将指导您将提供的 CSV 格式的数据转换为 XML 格式。

* 使用 [Converter][6] 类加载 CSV 文件。
* 使用 [DataConvertOptions][7] 将转换格式设置为 XML。
* 调用[Convert][8]方法从加载的CSV文件中获取XML格式数据。

以下源代码使用 C# 将 CSV 文件转换为 XML 格式。

```
// 使用 C# 将 CSV 数据转换为 XML 格式
using (Converter converter = new Converter(@"path/sample.csv"))
{
    DataConvertOptions options = new DataConvertOptions
    {
        Format = DataFileType.Xml
    };
    converter.Convert(@"path/CSV-to-XML.xml", options);
}
```

上述代码的输出如下。我正在分享 XML 文件的一部分，以便您了解 XML 输出。

```
<DocumentElement>
  <Sheet1>
    <Employee>David</Employee>
    <Quarter>1</Quarter>
    <Product>Maxilaku</Product>
    <Continent>Asia</Continent>
    <Country>China</Country>
    <Sale>2000</Sale>
  </Sheet1>
  <Sheet1>
    <Employee>David</Employee>
    ...
  </Sheet1>
  <Sheet1>
    ...
  </Sheet1>
</DocumentElement>
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][9] 使用 API 而不受评估限制。

## 结论

总而言之，我们讨论了使用 C# 在 .NET 应用程序中将 CSV 数据转换为 XML 格式。要构建您自己的转换应用程序，您可以使用 [文档][10] 了解有关转换自动化 .NET API 的更多信息。最好的方法是体验 [GitHub][11] 上提供的示例。如有任何疑问，请通过 [论坛][12] 联系我们。

## 也可以看看

* [C# 中 JSON 到 XML 的转换][13]
* [使用 C# 将 JSON 转换为 CSV 和 CSV 到 JSON][14]
* [在 C# 中将 Excel 转换为 CSV 和 CSV 到 Excel 格式][15]







[1]: #csv-to-xml-dotnet-api
[2]: #csv-to-xml
[3]: https://products.groupdocs.com/conversion/
[4]: https://downloads.groupdocs.com/conversion
[5]: https://www.nuget.org/packages/groupdocs.conversion
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://docs.groupdocs.com/conversion/net/
[11]: https://github.com/groupdocs-conversion
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/09/11/convert-json-to-xml-in-csharp/
[14]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[15]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/


