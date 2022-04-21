---
title: "在 C# 中从 JSON 数据生成报告"
date: Sat, 20 Mar 2021 10:45:45 +0000
draft: false
url: /zh/2021/03/20/generate-reports-from-json-data-in-csharp/
author: 'Shoaib Khan'
summary: "本文解决了在 .NET 应用程序中将原始 JSON 数据格式化为可呈现且易于理解的报告格式的问题。我们将使用简单的模板**将 JSON 数据转换为 C# 中的 PDF 和 DOCX 报告**。"
tags: ['Convert JSON to PDF in CSharp', 'Generate PDF report from JSON', 'Generate PDF Report in CSharp', 'JSON to PDF using Template in CSharp']
categories: ['GroupDocs.Assembly Product Family']
---

本文解决了在 .NET 应用程序中将原始 JSON 数据格式化为可呈现且易于理解的报告格式的问题。我们将使用简单的模板**将 JSON 数据转换为 C# 中的 PDF 和 DOCX 报告**。



{{< figure align=center src="images/json-to-pdf-or-word-report-in-csharp.jpg" alt="在 CSharp 中从 JSON 生成 PDF 或 Word 报告">}}


## 用于生成报告的 .NET API

[GroupDocs.Assembly for .NET][2] 是 .NET 应用程序的报告生成和文档自动化 API。它允许您根据**JSON**、**XML** 或**CSV** 等各种格式的可用数据以及**Word** 文档、**电子表格等多种不同格式的模板生成报告**、**演示文稿**或**文本**格式。它还支持许多报表格式功能，如**项目符号、编号列表、图表、表格、图像、条形码**等。

您可以从 [下载部分][3] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][4] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Assembly
```

## 在 C# 中从 JSON 数据生成 PDF 报告

让我们从引导您将 JSON 数据转换为 C# 格式的 PDF 报告的步骤开始。

* 获取JSON数据源
* 根据JSON数据定义模板
* 为简单的 C# 代码提供 JSON 数据源和模板以生成报告。

### JSON 数据

首先，以下示例 JSON 数据用于显示经理及其各自客户和详细信息的 PDF 报告生成。

```
\[
	{
		"Name":"John Smith","Contract":\[
		{"Client":{"Name":"A Company"},"Price":1200000},
		{"Client":{"Name":"B Ltd."},"Price":750000},
		{"Client":{"Name":"C & D"},"Price":350000}\]
	},
	{
		"Name":"Tony Anderson","Contract":\[
		{"Client":{"Name":"E Corp."},"Price":650000},
		{"Client":{"Name":"F & Partners"},"Price":550000}\]
	},
	{
		"Name":"July James","Contract":\[
		{"Client":{"Name":"G & Co."},"Price":350000},
		{"Client":{"Name":"H Group"},"Price":250000},
		{"Client":{"Name":"I & Sons"},"Price":100000},
		{"Client":{"Name":"J Ent."},"Price":100000}\]
	}
\]
```

＃＃＃ 模板

其次，在 TXT、DOCX 或所需格式中定义以下模板。这允许迭代经理的数据及其各自的客户及其详细信息。之后，您可以跳转到生成报告的代码。

```
<<foreach [in managers]>>Manager: <<[Name]>>
Contracts:
<<foreach [in Contract]>>- <<[Client.Name]>> ($<<[Price]>>)
<</foreach>>
<</foreach>>
```

### C# 步骤将 JSON 转换为 PDF 报告

以下 C# 代码步骤根据定义的模板自动将 JSON 数据转换为 PDF 报告。

* 定义 JSON 数据、模板文件和 PDF 输出报告文件路径。
* 使用 JSON 数据文件实例化 [JsonDataSoure][5]。
* 使用定义的 JsonDataSource 创建 [DataSourceInfo][6]。
* 调用 [DocumentAssembler][7] 类的 _**AssembleDocument**_ 方法，根据提供的 JSON 数据和定义的模板生成 PDF 报告。

```
// 使用 C# 中的 TXT 模板和 GroupDocs.Assembly API 从 JSON 数据生成 PDF 报告
// 定义数据源、模板和输出报告文件。
const string strDataSource = "dataPath/ManagerData.json";
const string strDocumentTemplate = "templatePath/template.txt";
const string strDocumentReport = "reportsPath/reportFromJSON.pdf";
// 实例化 JSON 数据源
JsonDataSource dataSource = new JsonDataSource(CommonUtilities.GetDataSourceDocument(strDataSource));
// 生成报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(CommonUtilities.GetSourceDocument(strDocumentTemplate),
    CommonUtilities.SetDestinationDocument(strDocumentReport),
    new DataSourceInfo(dataSource, "managers"));
```

该代码将生成如上图所示的 PDF 报告。您还可以从 [GitHub 存储库][8] 中测试及以上和类似示例。

## 在 C# 中从 JSON 数据生成 MS Word 报告

同样，就像生成上面的 PDF 报告一样，您可以按照以下步骤创建 DOCX 报告：

* 以 DOCX 格式定义相同的模板。
* 设置输出报表文档格式为DOCX。
* 其余代码将保持不变，以从 JSON 数据生成 MS Word DOCX 报告。

```
// 使用 C# 中的 DOCX 模板和 GroupDocs.Assembly API 从 JSON 数据生成 Word 报告
// 定义数据源、模板和输出报告文件。
const string strDataSource = "dataPath/ManagerData.json";
const string strDocumentTemplate = "templatePath/template.docx";
const string strDocumentReport = "reportsPath/reportFromJSON.docx";
// 实例化 JSON 数据源
JsonDataSource dataSource = new JsonDataSource(CommonUtilities.GetDataSourceDocument(strDataSource));
// 生成报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.AssembleDocument(CommonUtilities.GetSourceDocument(strDocumentTemplate),
    CommonUtilities.SetDestinationDocument(strDocumentReport),
    new DataSourceInfo(dataSource, "managers"));
```

有关更多详细信息、选项和示例，请访问 [文档][9] 和 [GitHub][10] 存储库。如需进一步查询，请联系 [论坛][11] 上的免费支持。

## 结论

在本文中，您学习了使用 C# 在 .NET 应用程序中将 JSON 数据转换为 PDF 报告。此外，您可以使用 CSV 和 XML 等其他数据源生成其他格式的报告，例如 DOCX。我希望您在开始构建您的报告生成器 .NET 应用程序时会感到自在。

## 也可以看看

* [用 Java 从 JSON 数据生成报告][12]







[1]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[2]: https://products.groupdocs.com/assembly/net
[3]: https://downloads.groupdocs.com/assembly/net
[4]: https://www.nuget.org/packages/groupdocs.assembly
[5]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly.data/jsondatasource
[6]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/datasourceinfo
[7]: https://apireference.groupdocs.com/assembly/net/groupdocs.assembly/documentassembler
[8]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET
[9]: https://docs.groupdocs.com/assembly/net
[10]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET
[11]: https://forum.groupdocs.com/c/assembly
[12]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/


