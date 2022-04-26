---
title: "在 C# 中将文档转换为 Excel XLS、XLSX"
date: Tue, 13 Apr 2021 23:17:00 +0000
draft: false
url: /zh/2021/04/13/convert-document-to-excel-xls-xlsx-in-csharp/
aliases:
- /2019/10/23/convert-document-to-excel-xls-xlsx-with-csharp-api/
- /2019/10/23/convert-document-to-excel-xls-xlsx-in-csharp/
- /2019/10/23/convert-a-document-to-excel-in-c/
author: 'Shoaib Khan'
summary: "If you have tabular data in PDF or Word documents format, you definitely need to convert it to Excel spreadsheets. This scenario becomes complex when there are many spreadsheets or multiple workbooks. You surely need to automate this procedure. In this article, we will see how to convert PDF to Excel and also how to convert Word documents to Excel spreadsheet programmatically in C# using .NET API."
tags: ['convert PDF to Excel in csharp', 'Convert Word to Excel in CSharp', 'document conversion', 'PDF to Excel in C#', 'Word to Excel in C#']
categories: ['GroupDocs.Conversion Product Family']
---

如果您有 PDF 或 Word 文档格式的表格数据，您肯定需要将其转换为 Excel 电子表格。当有许多电子表格或多个工作簿时，这种情况会变得复杂。你肯定需要自动化这个过程。在本文中，我们将了解如何将 PDF 转换为 Excel，以及如何使用 .NET API 在 C# 中以编程方式将 Word 文档转换为 Excel 电子表格。



{{< figure align=center src="images/pdf-word-to-xls-in-csharp.jpg" alt="在 C# 中将 Word 和 PDF 转换为 Excel">}}


以下是本文简要讨论的主题：

* .NET API – 将文档转换为电子表格
* 将 PDF 转换为 Excel
* 将 Word 转换为 Excel
* PDF 或 Word 到电子表格的转换具有更多选项

## .NET API - 转换为电子表格格式

在本文中，我将使用 [GroupDocs.Conversion for .NET][2] 使用 C# 将 PDF 和 Word 文档转换为电子表格。它是功能丰富的 API，允许以多种文件格式进行文档和图像转换。为了突出某些格式，API 支持文字处理文档、电子表格、演示文稿、AutoCAD 绘图、电子书、PDF、电子邮件文件、网页、图像、photoshop 文件和许多其他文档格式。

从 [下载部分][3] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][4] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 PDF 转换为 Excel

以下是将 PDF 文档转换为 Excel 电子表格的步骤。

* 使用 [Converter][5] 类加载 PDF 文件。
* 使用 [SpreadsheetConvertOptions][6] 类初始化转换选项。
* 使用选项调用Converter类的[Convert][7]方法。

以下代码示例展示了如何使用 C# 将 PDF 文件转换为 Excel XLSX 格式。

```
// 在 C# 中将 PDF 文档转换为 Excel 电子表格
using (Converter converter = new Converter("document.pdf"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
    converter.Convert("outputpath/convertedSpreadsheet.xlsx", options);
}
```

## 在 C# 中将 Word 转换为 Excel

您可以使用与我们在上面转换 PDF 文件相同的方式将任何 Word 文档转换为 Excel 电子表格。我们只需提供正确的源文件即可转换为 XLS 或 XLSX。

以下是将 DOC DOCX 格式的 Word 文档转换为 Excel 电子表格的步骤。

* 使用 [Converter][8] 类加载 Word 文件。
* 使用 [SpreadsheetConvertOptions][9] 类初始化转换选项。
* 调用带有选项的Converter类的[Convert][10]方法。

以下代码示例展示了如何使用 C# 将 DOC 或 DOCX 文件转换为 Excel XLSX 格式。

```
// 在 C# 中将 Word 文档转换为 Excel 电子表格
using (Converter converter = new Converter("document.docx"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions();
    converter.Convert("outputpath/convertedSpreadsheet.xlsx", options);
}
```

## PDF 或 Word 到电子表格的转换，使用 C# 提供更多选项

您只能转换文档的某些选定页面。 API 让您可以使用不同的选项转换文档，包括：

* 开始**页码**。
* **页数**要转换。
* **特定页面**用于转换。
* **格式**要转换成。
* **密码** 用于使文件受到保护。
* **缩放**使其变大或变小。
* **水印**在转换器文件上。

以下是如何使用 C# 将 PDF 文件的某些页面转换为具有不同缩放比例的 XLSX 格式的步骤。

```
// 使用一些选项在 C# 中将 PDF 文件的第二页转换为 Excel
using (Converter converter = new Converter("document.pdf"))
{
    SpreadsheetConvertOptions options = new SpreadsheetConvertOptions
    {
        PageNumber = 2,
        PagesCount = 1,
        Format = SpreadsheetFileType.Xlsx,
        Zoom = 150
    };
    converter.Convert("outputpath/convertedSpreadsheet.xlsx", options);
}
```

这是使用上述代码输出的 PDF 文件和转换后的电子表格。它将 PDF 文件的第二页转换为 XLSX 格式。



{{< figure align=center src="images/pdf-to-xls-in-csharp.jpg" alt="以编程方式将 PDF 转换为 Excel XLS XLSX">}}


## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][11] 以便在没有评估限制的情况下使用 API。

## 结论

在本文中，您学习了如何使用 C# 在 Excel 电子表格中转换 PDF 和 Word 文档。此外，您还看到了我们如何使用缩放、水印等选项转换文档的任何部分，并使其受密码保护。您现在可以开始构建您自己的基于 .NET 的文档转换应用程序或将这些功能集成到您现有的应用程序中。

有关更多详细信息、选项和示例，您可以访问 [文档][12] 和 [GitHub][13] 存储库。如需进一步查询，请联系 [论坛][14] 上的支持人员。

## 也可以看看

* [在 C# 中将 CAD 绘图转换为 PDF][15]
* [在 C# 中将演示文稿转换为 PDF][16]
* [使用 C# 将 Excel 电子表格转换为 PDF][17]







[1]: https://blog.groupdocs.com/2021/04/13/convert-document-to-excel-xls-xlsx-in-csharp/
[2]: https://products.groupdocs.com/conversion/net
[3]: https://downloads.groupdocs.com/conversion/net
[4]: https://www.nuget.org/packages/groupdocs.conversion
[5]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/conversion/net
[13]: https://github.com/groupdocs-conversion
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[16]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[17]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/


