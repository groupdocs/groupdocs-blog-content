---
title: "在 C# 中从 XML 数据生成报告"
date: Sat, 04 Sep 2021 17:18:55 +0000
draft: false
url: /zh/2021/09/04/generate-reports-from-xml-data-in-csharp/
author: 'Shoaib Khan'
summary: "**XML** 是一种 W3C 推荐的自描述语言，旨在存储和传输数据。开发人员可以在 .NET 应用程序中将 XML 格式更改为任何其他更好的人类可读格式，例如 PDF 或 MS Word 文档。本文将讨论如何使用 C# 使用简单的模板将 XML 数据转换为 PDF 和 MS Word 报告。"
tags: ['Convert XML to DOCX in CSharp', 'Convert XML to PDF in CSharp', 'Generate PDF Report from XML', 'generate reports in csharp', 'XML to DOCX in CSharp', 'XML to PDF in CSharp']
categories: ['GroupDocs.Assembly Product Family']
---

**XML** 是一种 W3C 推荐的自描述语言，旨在存储和传输数据。开发人员可以在 .NET 应用程序中将 XML 格式更改为任何其他更好的人类可读格式，例如 PDF 或 MS Word 文档。本文将讨论**如何通过简单的模板使用 C#** 将 XML 数据转换为 PDF 和 MS Word 报告。



{{< figure align=center src="images/xml-to-pdf-word-report-in-csharp.jpg" alt="C# 中的 XML 到 PDF 报告">}}


下面讨论以下主题：

* [用于生成报告的.NET API][1]
* [使用 C# 从 XML 数据生成 PDF 报告][2]
* [使用 C# 从 XML 数据生成 MS Word DOC/DOCX 报告][3]

## 报告生成 .NET API – XML 到 PDF 和 WORD {#generate-report-dotnet-api}

[GroupDocs.Assembly for .NET][4] 是使用 **DOCX** 或 **TXT** 模板从 **XML** 数据自动生成报告的 API。此外，它还支持**JSON、CSV、**等数据源，将数据转换为不同文件格式的报表。

您可以从 [下载部分][5] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Assembly
```

## 在 C# 中从 XML 数据生成 PDF 报告 {#xml-to-pdf-report-in-csharp}

3 个简单的步骤将引导您将 XML 数据转换为格式化的 PDF 报告。

1. 加载您的 XML 数据源。
2. 根据加载的 XML 数据定义模板。
3. 最后，为报表生成方法提供 XML 数据源和模板。

### XML 数据

以下 XML 示例数据用于将其转换为 PDF 报告。它包含经理及其各自客户的数据以及更多详细信息。

```
<Managers>
	<Manager>
		<Name>John Smith</Name>
		<Contract>
			<Client>
				<Name>A Company</Name>
			</Client>
			<Price>1200000</Price>
		</Contract>
		<Contract>
		...
		</Contract>
		...
	</Manager>
	<Manager>
		<Name>Tony Anderson</Name>
		...
	</Manager>
	...
</Managers>
```

＃＃＃ 模板

根据您的源 XML 数据定义 TXT 或 DOCX 格式的模板。我正在使用下面提到的模板，它是根据上面提到的经理的 XML 数据创建的。这将使报告生成器迭代经理及其各自的客户。模板完成后，您就差不多完成了。您可以使用以下代码生成报告。

```
<<foreach \[in managers\]>>Manager: <<\[Name\]>>
Contracts:
<<foreach \[in Contract\]>>- <<\[Client.Name\]>> ($<<\[Price\]>>)
<</foreach>>
<</foreach>>
```

### C# 步骤从 XML 生成 PDF 报告

以下步骤允许您根据定义的模板自动从 XML 数据生成 PDF 报告。

* 定义 XML 数据文件、文本模板文件和 PDF 输出报告文件。
* 用 XML 数据文件实例化 [XMLDataSoure][7]。
* 使用已定义的 XML 数据源创建 [DataSourceInfo][8]。
* 调用[AssembleDocument][9]方法生成PDF报告。

以下代码实现了上述步骤并使用 C# 从 XML 数据源生成 PDF。

```
// 在 CSharp 中使用 TXT 模板从 XML 数据生成 PDF 报告
// 定义数据源、模板和输出报告文件。
string xmlDataSource = @"dataPath/Managers.xml";
string templateFilePath = @"templatePath/xml-template.txt";
string reportFilePath = @"reportsPath/xml-to-pdf-report.pdf";
// 加载 XML 数据源
XmlDataSource dataSource = new XmlDataSource(xmlDataSource);
// 组装文档以生成 PDF
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "managers"));
```

## 在 C# 中从 XML 数据生成 MS Word 报告 {#xml-to-word-report-in-csharp}

同样，您还可以使用相同的 XML 数据创建 MS Word DOC/DOCX 格式的报告。与我们上面讨论的代码没有区别，只是您必须更改输出文件名。

* 加载 XML 数据文件。
* 以 TXT 或 DOCX 格式定义模板。
* 设置输出报表文档格式为DOCX。
* 将 XML 数据文件、模板和输出文件路径提供给 [DocumentAssembler][10] 以将 XML 转换为 DOCX。

以下代码使用 C# 定义的模板转换 XML 并生成 DOCX 文件。

```
// 使用 CSharp 中的文本模板从 XML 数据生成 MS Word 报告
// 定义数据源、模板和输出报告文件。
string xmlDataSource = @"dataPath/Managers.xml";
string templateFilePath = @"templatePath/xml-template.txt";
string reportFilePath = @"reportsPath/xml-to-word-report.docx";
// 加载 XML 数据源
XmlDataSource dataSource = new XmlDataSource(xmlDataSource);
// 组装文档以生成 Word 报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(templateFilePath, reportFilePath, new DataSourceInfo(dataSource, "managers"));
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][11] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，您已经学会了使用 C# 和 .NET 应用程序将 XML 数据转换为 PDF 格式作为报告。此外，我们还讨论了使用模板从同一 XML 生成 DOC/DOCX 格式的报告。在阅读了这一系列报告生成帖子之后；从 **[JSON][12]**、**[CSV][13]**、**XML** 生成 PDF 和 MS Word 报告，您可以开发自己的报告构建 .NET 应用程序。

有关 GroupDocs.Assembly、选项和示例的更多信息，请访问 [文档][14] 和 [GitHub][15] 存储库。如需进一步查询，请通过 [论坛][16] 联系我们。

## 也可以看看

* [使用 C# 将 JSON 数据转换为 PDF 或 Word 报告][17]
* [使用 C# 将 CSV 数据转换为 PDF 或 Word 报告][18]







[1]: #generate-report-dotnet-api
[2]: #xml-to-pdf-report-in-csharp
[3]: #xml-to-word-report-in-csharp
[4]: https://products.groupdocs.com/assembly/net/
[5]: https://downloads.groupdocs.com/assembly
[6]: https://www.nuget.org/packages/groupdocs.assembly
[7]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.data/xmldatasource
[8]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/datasourceinfo
[9]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler/methods/assembledocument/index
[10]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[13]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[14]: https://docs.groupdocs.com/assembly/net/
[15]: https://github.com/groupdocs-assembly
[16]: https://forum.groupdocs.com/c/assembly
[17]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/


