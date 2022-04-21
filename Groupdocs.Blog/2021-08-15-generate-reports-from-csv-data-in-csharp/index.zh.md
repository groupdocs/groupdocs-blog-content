---
title: "使用 C# 从 CSV 数据生成报告"
date: Sun, 15 Aug 2021 10:50:32 +0000
draft: false
url: /zh/2021/08/15/generate-reports-from-csv-data-in-csharp/
aliases:
- /2019/10/21/generate-reports-from-csv-xml-in-csharp/
- /2019/10/21/generate-reports-from-csv-json-xml/
- /2019/10/21/generate-reports-from-csv-json-xml-in-csharp/
- /2019/10/21/generate-reports-from-csv-data-source/
- /2019/10/21/generate-reports-from-csv-data-source-in-groupdocs.assembly-for-.net-19.10/
author: 'Shoaib Khan'
summary: "CSV（[逗号分隔值][1] 文件广泛用于在应用程序之间交换数据。当您希望将此数据转换为可呈现且有意义的信息时，您需要将其转换为其他格式。在我们的一篇文章中，我们已经了解了[如何使用 Java 在报告中转换 CSV 数据][2]。本文将指导您使用 C#** 使用简单的模板将 CSV 数据转换为 PDF 和 MS Word DOC/DOCX 报告。"
tags: ['Convert CSV to PDF in CSharp', 'CSV to PDF using template', 'CSV to Word Report in CSharp', 'Generate PDF report from CSV', 'Generate Reports', 'generate reports in csharp']
categories: ['GroupDocs.Assembly Product Family']
---

CSV（[逗号分隔值][3] 文件广泛用于在应用程序之间交换数据。当您希望将此数据转换为可呈现且有意义的信息时，您需要将其转换为其他格式。在我们的一篇文章中，我们已经了解了[如何使用 Java 将 CSV 数据转换为报告中的数据][4]。本文将指导您使用 C#** 使用简单的模板将 CSV 数据转换为 PDF 和 MS Word DOC/DOCX 报告。

以下主题涵盖以下内容：

* [报告生成.NET API][5]
* [从 CSV 数据生成 PDF 报告][6]
* [从 CSV 数据生成 MS Word 报告][7]

## 报告生成 .NET API {#report-generator-dotnet-api}

[GroupDocs.Assembly][8] 提供 .NET 报告 API 来自动生成报告。在本文中，我使用了 [GroupDocs.Assembly for .NET][9] 从选定的 **CSV** 数据和 **TXT** 格式模板生成报告。它还支持多种数据源，如 **JSON、XML** 以及来自 **MS Word**、**Excel** 和 **PowerPoint** 文件的数据文件。

您可以从 [下载部分][10] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][11] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Assembly
```

## 在 C# 中从 CSV 数据生成 PDF 报告 {#csv-to-pdf-report-csharp}

让我们首先将逗号分隔的数据转换为可呈现的 PDF。以下步骤将指导您将 CSV 数据转换为格式化的 PDF 报告。

* 加载 CSV 数据源。
* 根据 CSV 数据定义模板。
* 提供 CSV 数据源和模板，以简单的方法生成 PDF 报告。



{{< figure align=center src="images/csv-to-pdf-word-report-in-csharp.jpg" alt="C# 中的 CSV 到 PDF 报告">}}


### CSV 数据

为了获得 PDF 报告，我将使用不同个体的以下样本 CSV 数据以及他们各自的年龄和出生日期数据。

```
Name,Age,Birth  
John Doe,32,4/1/1989 16:00  
Jane Doe,29,1/31/1992 7:00  
John Smith,53,3/8/1968 13:00
```

＃＃＃ 模板

下一步是以 TXT 或 DOCX 格式定义模板。以下是本示例中使用的模板，允许使用他们的详细信息迭代人员列表。

```
<<foreach \[in persons\]>>Name: <<\[Name\]>>, Age: <<\[Age\]>>, Date of Birth: <<\[Birth\]:"dd.MM.yyyy">>
<</foreach>>
Average age: <<\[persons.Average(p => p.Age)\]>>
```

### 在 C# 中从 CSV 生成 PDF 报告的步骤

以下步骤指导如何根据定义的模板使用 C# 和 .NET Reporting API 将 CSV 数据转换为 PDF 报告。

* 定义 CSV 数据文件、模板文件和 PDF 输出文件路径。
* 使用 CSV 数据文件和加载选项实例化 [CsvDataSoure][12]。
* 使用定义的数据源创建 [DataSourceInfo][13]。
* 使用 [DocumentAssembler][14] 调用 [AssembleDocument][15] 方法，定义模板文件、输出文件和 DataSourceInfo 以获取 PDF 报告作为输出。

以下代码显示了如何在 C# 中将 CSV 数据转换为 PDF 报告。

```
// 使用 C# 中的 TXT 模板和 GroupDocs.Assembly API 从 CSV 数据生成 PDF 报告
// 定义数据源、模板和输出报告文件。
string csvDataSource = @"path/person.csv";
string templateFilePath = @"path/csv-template.txt";
string reportFilePath = @"path/csv-to-pdf-report.pdf";

// 加载 CSV 数据源
CsvDataSource dataSource = new CsvDataSource(csvDataSource, new CsvDataLoadOptions(true));

// 生成 PDF 格式的报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "persons"));
```

## 在 C# 中从 CSV 数据生成 MS Word 报告 {#csv-to-docx-report-java}

如果您想在自动生成的报告中进行任何手动编辑，您还可以将输出作为 MS Word 文档获取。该过程将与上述 PDF 报告生成非常相似。以下步骤将指导从 CSV 数据生成 DOC/DOCX 报告：

* 从文件中加载 CSV 数据。
* 以 TXT 或 DOCX 格式定义模板。
* 设置输出报表文档格式为 DOC/DOCX。
* 调用 [AssembleDocument][16] 方法从 CSV 数据生成 MS Word DOCX 报告。

以下代码展示了如何使用 C# 将 CSV 数据转换为 DOCX 报告。

```
// 使用 C# 中的 TXT 模板和 GroupDocs.Assembly API 从 CSV 数据生成 Word DOCX 报告
// 定义数据源、模板和输出报告文件。
string csvDataSource = @"path/person.csv";
string templateFilePath = @"path/csv-template.txt";
string reportFilePath = @"path/csv-to-pdf-report.docx";

// 加载 CSV 数据源
CsvDataSource dataSource = new CsvDataSource(csvDataSource, new CsvDataLoadOptions(true));

// 生成 DOCX 格式的报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "persons"));
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][17] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您已经学会了使用 C# 将 CSV 数据转换为 PDF 和 MS Word 报告。您现在必须有信心通过将 CSV 数据转换为 PDF 格式来构建自己的 .NET 报告生成器应用程序。同样，您也可以使用 JSON 和 XML 等其他数据源生成报告。

有关 API 的更多信息，您可以访问 [documentation][18] 和 [GitHub][19] 存储库。如果有进一步的疑问和歧义，请联系 [论坛][20] 上的免费支持。

## 也可以看看

* [使用 C# 从 JSON 数据生成报告][21]
* [使用 Java 从 CSV 数据生成报告][22]







[1]: https://docs.fileformat.com/spreadsheet/csv/)
[2]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[3]: https://docs.fileformat.com/spreadsheet/csv/)
[4]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[5]: #report-generator-dotnet-api
[6]: #csv-to-pdf-report-csharp
[7]: #csv-to-docx-report-java
[8]: https://products.groupdocs.com/assembly/java
[9]: https://products.groupdocs.com/assembly/net/
[10]: https://downloads.groupdocs.com/assembly/net
[11]: https://www.nuget.org/packages/groupdocs.assembly
[12]: https://apireference.groupdocs.com/net/assembly/groupdocs.assembly.data/csvdatasource
[13]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/datasourceinfo
[14]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
[15]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler/methods/assembledocument/index
[16]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler/methods/assembledocument/index
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/assembly/net/
[19]: https://github.com/groupdocs-assembly
[20]: https://forum.groupdocs.com/c/assembly
[21]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[22]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/


