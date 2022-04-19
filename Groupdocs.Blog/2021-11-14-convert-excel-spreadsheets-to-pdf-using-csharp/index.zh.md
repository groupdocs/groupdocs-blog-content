---
title: "使用 C# 将 Excel 电子表格转换为 PDF"
date: Sun, 14 Nov 2021 17:48:00 +0000
draft: false
url: /zh/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
author: 'Shoaib Khan'
summary: "Excel（XLS、XLSX）和 PDF 文件是几乎在所有企业中广泛使用的文档格式。对于此类常用文件，有很多场景需要我们将一个文件转换为另一种格式。在本文中，我们将学习如何使用 C# 和 .NET 应用程序将 Excel 电子表格转换为 PDF 格式的不同方法。"
tags: ['Convert Excel in CSharp', 'Convert Excel to PDF', 'Convert Excel to PDF in CSharp', 'Convert to PDF in CSharp', 'Excel to PDF', 'Excel to PDF in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

Excel（[XLS][1]、[XLSX][2]和[PDF][3]文件是几乎在所有业务中广泛使用的文档格式。对于这些常用的文件，我们有很多场景需要将一个文件转换为另一种格式。在本文中，我们将学习如何使用 C# 和 .NET 应用程序将 Excel 电子表格转换为 PDF 格式的不同方法。



{{< figure align=center src="images/excel-to-pdf-in-csharp.jpg" alt="使用 C# 将 Excel 电子表格转换为 PDF">}}


* [.NET API 用于 Excel 文件到 PDF 的转换][4]
* [Excel表格到PDF转换][5]
* [Excel表格转PDF的顺序][6]
* [Excel表格转PDF的具体列表][7]
* [将所选单元格范围从 Excel 工作表转换为 PDF][8]

## .NET API 用于 Excel 文件到 PDF 的转换 {#excel-conversion-dotnet-api}

[GroupDocs.Conversion][9] 提供的 API 允许在 .NET 应用程序中将 Excel 文件转换为 PDF 格式。在本文中，我们将使用 [GroupDocs.Conversion for .NET][10] 将 Excel XLS/XLSX 文件数据转换为 PDF 格式。此外，API 支持许多其他文件格式的转换，如 [文档][11] 中提到的文字处理文档、电子表格、演示文稿、电子书、图像等。

您可以从 [下载部分][12] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][13] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 将 Excel 表格转换为 PDF - C# {#excel-to-pdf}

以下步骤使用 C# 将完整的工作簿（所有工作表）转换为 PDF 格式。

* 使用 [SpreadsheetLoadOptions][14] 准备**加载选项**。
* **使用 [Converter][15] 加载 Excel** 电子表格。
* 使用 [PdfConvertOptions][17] 调用 [Convert()][16] 方法以**转换**所有工作表并保存为 PDF 格式。

以下是有关如何在 .NET 应用程序中将完整的 Excel 工作簿转换为 PDF 的 C# 源代码。

```
/*
 * Convert all the Excel sheets to PDF format using C#
 */
// 为源 XLSX 文件准备加载选项和范围
Func<LoadOptions> loadOptions = () => new SpreadsheetLoadOptions
{
    OnePagePerSheet = true
};
using (var converter = new GroupDocs.Conversion.Converter(@"path/spreadsheet.xlsx", loadOptions))
{
    // Convert and save the spreadsheet in PDF format
    converter.Convert(@"path/all-sheets-converted.pdf", new PdfConvertOptions());
}
```



{{< figure align=center src="images/Converted-Excel-to-PDF.png" alt="从 Excel 数据转换 PDF">}}


## Excel 表格转换为 PDF 的序列 - C# {#sheets-sequence-to-pdf}

并不总是需要转换完整的工作簿。我们还可以转换任意连续数量的工作表。以下是使用 C# 将 Excel 工作簿工作表的任何子序列转换为 PDF 格式的步骤。

* **使用 [转换器][18] 加载** Excel 文件。
* 使用 [PdfConvertOptions][19] 定义**转换选项**。
* 设置**起始页数**和**序列**中的后续页数。
* 使用 **conversion** 选项调用 [Convert()][20] 方法，以按顺序获取以 PDF 格式保存的工作表子集。

以下是在 .NET 应用程序中按顺序将工作表（即工作表编号**2、3 和 4**）转换为 PDF 的 C# 源代码。

```
/*
 * Convert sequence of Excel sheets to PDF format using C#
 */
using (var converter = new GroupDocs.Conversion.Converter(@"path/spreadsheet.xlsx"))
{
    // Set the starting sheet number and consecutive sheet count
    var convertOptions = new PdfConvertOptions()
    {
        PageNumber = 2,
        PagesCount = 3
    };
    // Convert and save the spreadsheet in PDF format
    converter.Convert(@"path/sequential-sheets-converted.pdf", convertOptions);
}
```

## 特定的 Excel 表格到 PDF 的转换 - C# {#list-of-sheets-to-pdf}

我们可以简单地提供用于转换特定图纸的图纸编号列表。以下是如何使用 C# 将任何特定的图纸编号列表转换为 PDF 格式的步骤。

* **使用 [转换器][21] 加载**电子表格文件。
* **选择图纸编号**并使用 [PdfConvertOptions][22] 设置为列表。
* 使用转换选项调用 [Convert()][23] 方法以将列出的工作表**转换**为 PDF 格式。

以下 C# 代码片段在 .NET 应用程序中将工作表编号 **1、3 和 5** 转换为 PDF。

```
/*
 * Convert the specified list of Excel sheets to PDF format using C#
 */
using (var converter = new GroupDocs.Conversion.Converter(@"path/spreadsheet.xlsx"))
{
    // Set the list to sheet numbers on convert
    var convertOptions = new PdfConvertOptions()
    {
        Pages = new System.Collections.Generic.List<int> { 1,3,5}
    };
    // Convert and save the spreadsheet into PDF format
    converter.Convert(@"path/selected-sheets-conversion.pdf", convertOptions);
}
```

## 将 Excel 工作表的选定单元格范围转换为 PDF - C# {#cell-ranges-to-pdf}

最后但并非最不重要的一点，事实上，最棘手的一个，我们还可以转换 Excel 工作表的任何单元格范围，其方式与其他方法几乎相似。以下是使用 C# 将工作簿工作表的任何单元格区域转换为 PDF 格式的步骤。

* 首先，使用 [SpreadsheetLoadOptions][24] 定义要转换的**单元格范围**。
* **使用 [转换器][25] 加载**电子表格文件。
* **使用 [PdfConvertOptions][26] 通过确切的工作表编号或子序列选择工作表**。
* 使用转换选项调用 [Convert()][27] 方法，以**将所选工作表的所选单元格范围**转换为 PDF 格式。

以下代码使用 C# 将工作表编号 2、3 和 4 的单元格区域 (A1:C20) 转换为 PDF 格式。

```
/*
 * Convert the specified Cell Range of specified Excel sheets to PDF format using C#
 */
// 为源 XLSX 文件准备加载选项和范围
Func<LoadOptions> loadOptions = () => new SpreadsheetLoadOptions
{
    ConvertRange = "A1:C20"
};
using (var converter = new Converter(@"path/spreadsheet.xlsx", loadOptions))
{
    var convertOptions = new PdfConvertOptions()
    {
        PageNumber = 2,
        PagesCount = 3
        // Pages = new System.Collections.Generic.List<int> { 2,3,4}
    };
    // Save as PDF after conversion
    converter.Convert(@"path/cell-range-converted.pdf", convertOptions);
}
```

## 结论

最后，我们学习了使用 C# 将 Excel 电子表格转换为 PDF 格式的不同方法。首先，我们希望将完整的工作簿转换为 PDF 格式，然后我们转换工作表的子序列。后来，我们学习了如何通过提供确切的工作表编号列表来转换任何工作表，最后，我们从所选工作表的所选单元格范围中获取了 PDF 文件。

从 [文档][28] 中了解有关 **GroupDocs.Conversion API** 的更多信息。如有疑问，请通过 [论坛][29] 联系我们。

## 也可以看看

* [在 C# 中将 Excel 工作表转换为 CSV，反之亦然][30]
* [使用 C# 给 Excel 表格添加水印][31]
* [使用 C# 为 PDF 文件添加水印][32]
* [在 C# 中将文档转换为 Excel（XLS、XLSX）][33]







[1]: https://docs.fileformat.com/spreadsheet/xls/
[2]: https://docs.fileformat.com/spreadsheet/xlsx/)
[3]: https://docs.fileformat.com/pdf/
[4]: #excel-conversion-dotnet-api
[5]: #excel-to-pdf
[6]: #sheets-sequence-to-pdf
[7]: #list-of-sheets-to-pdf
[8]: #cell-ranges-to-pdf
[9]: https://products.groupdocs.com/conversion/
[10]: https://products.groupdocs.com/conversion/net/
[11]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[12]: https://downloads.groupdocs.com/conversion
[13]: https://www.nuget.org/packages/groupdocs.conversion
[14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/spreadsheetloadoptions
[15]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[16]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[17]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[18]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[19]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[20]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[21]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[22]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[23]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[24]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/spreadsheetloadoptions
[25]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[26]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[27]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[28]: https://docs.groupdocs.com/conversion
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
[31]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[32]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[33]: https://blog.groupdocs.com/2021/04/13/convert-document-to-excel-xls-xlsx-in-csharp/


