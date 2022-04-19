---
title: "在 C# 中将 JSON 转换为 XML"
date: Sat, 11 Sep 2021 09:17:00 +0000
draft: false
url: /zh/2021/09/11/convert-json-to-xml-in-csharp/
author: 'Shoaib Khan'
summary: 'JSON and XML, both are the well known structured formats that are vastly used by developers to transmit data. There are many requirement where as a programmer, we need the conversion between JSON and XML data formats. In this article, you will learn how to convert JSON data into XML format using C#.

本文将介绍以下主题：

* 用于 JSON 和 XML 转换的 .NET API
* 以编程方式将 JSON 转换为 XML'
tags: ['Convert JSON to XML', 'Convert JSON to XML in CSharp', 'JSON to XML', 'JSON to XML in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

JSON 和 XML 都是众所周知的结构化格式，开发人员广泛使用它们来传输数据。作为程序员，有很多需求，我们需要在 JSON 和 XML 数据格式之间进行转换。在本文中，您将学习**如何使用 C# 将 JSON 数据转换为 XML 格式**。



{{< figure align=center src="images/convert-json-to-xml-csharp.jpg" alt="在 CSharp 中将 JSON 转换为 XML">}}


以下主题涵盖以下内容：

* [用于 JSON 和 XML 转换的 .NET API][1]
* [以编程方式将 JSON 转换为 XML][2]

## 用于 JSON 和 XML 转换的 .NET API {#json-xml-conversion-dotnet-api}

[GroupDocs.Conversion][3] 提供了一个 .NET API，允许自动将不同的文档、图像和其他文件格式相互转换。我在这里使用相同的 API 使用 C# 将 JSON 文件转换为 XML 格式。除了 JSON 和 XML 转换之外，API 还支持许多其他 [来回转换][4]，例如文字处理文档、演示文稿、电子书、JPG、PNG、WebP 等等。您可以在文档中查看详细信息。

您可以从 [下载部分][5] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 JSON 转换为 XML {#json-to-xml}

JSON 和 XML 格式都常用于基于 Web 的应用程序来传输数据。这些是结构化的、人类可读的、分层的格式，用于存储和交换数据。

以下步骤指导您使用 .NET API 将 JSON 数据转换为 XML 格式。

* 使用 [Converter][7] 类加载 JSON 数据文件。
* 使用 [DataConvertOptions][8] 将转换格式设置为 XML。
* 调用Converter类的[Convert][9]方法将JSON数据转换成XML格式

以下代码使用 C# 将 JSON 数据转换为 XML 格式。

```
// 使用 C# 将 JSON 数据转换为 XML 格式
using (Converter converter = new Converter(@"path/sample.json"))
{
    DataConvertOptions options = new DataConvertOptions
    {
        Format = DataFileType.Xml
    };
    converter.Convert(@"path/jsonToXML.xml", options);
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][10] 使用 API，而不受评估限制。

## 结论

最后，您已经学习了使用 C# 在 .NET 应用程序中将 JSON 数据转换为 XML 格式。您可以使用 [文档][11] 或通过快速体验 [GitHub][12] 上提供的示例来了解有关 .NET 转换自动化 API 的更多信息。如有任何疑问，请通过 [论坛][13] 联系我们。

## 也可以看看

* [使用 C# 转换 JSON 和 CSV][14]
* [使用 C# 转换 Excel 和 CSV][15]







[1]: #json-xml-conversion-dotnet-api
[2]: #json-to-xml
[3]: https://products.groupdocs.com/conversion/
[4]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/conversion
[6]: https://www.nuget.org/packages/groupdocs.conversion
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/conversion/net/
[12]: https://github.com/groupdocs-conversion
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[15]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/


