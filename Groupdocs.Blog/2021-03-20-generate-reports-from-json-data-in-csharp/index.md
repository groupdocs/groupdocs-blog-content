---
title: 'Generate Reports from JSON Data in C#'
date: Sat, 20 Mar 2021 10:45:45 +0000
draft: false
url: /2021/03/20/generate-reports-from-json-data-in-csharp/
author: 'Shoaib Khan'
summary: "This article addresses the problem of formatting raw JSON data into a presentable and easily understandable report format within the .NET application. We will be **converting the JSON data into PDF and DOCX reports in C#** using simple templates."
tags: ['Convert JSON to PDF in CSharp', 'Generate PDF report from JSON', 'Generate PDF Report in CSharp', 'JSON to PDF using Template in CSharp']
categories: ['GroupDocs.Assembly Product Family']
---

This article addresses the problem of formatting raw JSON data into a presentable and easily understandable report format within the .NET application. We will be **converting the JSON data into PDF and DOCX reports in C#** using simple templates.



{{< figure align=center src="images/json-to-pdf-or-word-report-in-csharp.jpg" alt="Generate PDF or Word Report from JSON in CSharp">}}


## .NET API for Report Generation

[GroupDocs.Assembly for .NET][2] is the report generation and document automation API for .NET applications. It allows you to generate reports from the data available in various formats like **JSON**, **XML**, or **CSV** and the template in many different formats like **Word** document, **spreadsheet**, **presentation**, or **text** format. It also supports many report formatting features such as **bullets, numbered lists, charts, tables, images, barcodes**, etc.

You can download the DLLs or MSI installer from the [downloads section][3] or install the API in your .NET application via [NuGet][4].

```
PM> Install-Package GroupDocs.Assembly
```

## Generate PDF Report from JSON Data in C#

Let's start with the steps that will lead you to convert JSON data into the formatted PDF report in C#.

*   Get JSON data source
*   Define template according to JSON data
*   Provide JSON data source and template to simple C# code for report generation.

### JSON Data

Firstly, the following sample JSON data is used for the PDF report generation that shows managers and their respective clients and details.

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

### Template

Secondly, define the following template in TXT, DOCX, or in the required format. This allows iterating Managers' data and their respective Clients and their details. After that, you can jump to code for report generation.

```
<<foreach [in managers]>>Manager: <<[Name]>>
Contracts:
<<foreach [in Contract]>>- <<[Client.Name]>> ($<<[Price]>>)
<</foreach>>
<</foreach>>
```

### C# Steps to Convert JSON to PDF Report

The following steps of C# code automate the conversion of JSON data to PDF report according to the defined template.

*   Define JSON data, the template file, and PDF output report file paths.
*   Instantiate [JsonDataSoure][5] with JSON data file.
*   Create [DataSourceInfo][6] with defined JsonDataSource.
*   Call the _**AssembleDocument**_ method of the [DocumentAssembler][7] class to generate the PDF report from the provided JSON data and defined template.

{{< gist GroupDocsGists 25951e2128f390c6ba1980c1bdaaa9c9 "GeneratePdfReportFromJSON.cs" >}}

The code will produce the PDF report as shown in the figure above. You may also test and above and similar examples from the [GitHub repository][8].

## Generate MS Word Report from JSON data in C#

Similarly, like generating the PDF report above, you can create the DOCX report by following these steps:

*   Defining the same template in DOCX format.
*   Set the output report document format as DOCX.
*   The rest of the code will remain the same to generate MS Word DOCX report from the JSON data.

{{< gist GroupDocsGists 25951e2128f390c6ba1980c1bdaaa9c9 "GenerateWordReportFromJSON.cs" >}}

For more details, options, and examples, visit the [documentation][9] and the [GitHub][10] repository. For further queries, contact the free support on the [forum][11].

## Conclusion

In this article, you learned to convert your JSON data into the PDF report within your .NET application using C#. Further, you can generate reports in other formats like DOCX using other data sources like CSV and XML. I hope you will feel comfortable starting building your report generator .NET application.

## See Also

*   [Generate Reports from JSON Data in Java][12]







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

