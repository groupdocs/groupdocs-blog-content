---
title: "Generate Reports from XML Data in C#"
seoTitle: "PDF & Word Reports from XML in C# | XML to PDF and DOCX"
description: "Automate reports generation in C# by converting XML data into PDF & DOC/DOCX via text-based templates using .NET API by GroupDocs."
date: Sat, 04 Sep 2021 17:18:55 +0000
draft: false
url: /2021/09/04/generate-reports-from-xml-data-in-csharp/
author: 'Shoaib Khan'
summary: "**XML** is a W3C Recommended, self-descriptive language that is designed to store and transport data. A developer can change the XML format into any other better human-readable format like PDF or MS Word document within the .NET application. This article will discuss how to convert XML data into PDF and MS Word reports using C# using simple templates."
tags: ['Convert XML to DOCX in CSharp', 'Convert XML to PDF in CSharp', 'Generate PDF Report from XML', 'generate reports in csharp', 'XML to DOCX in CSharp', 'XML to PDF in CSharp']
categories: ['GroupDocs.Assembly Product Family']
---

**XML** is a W3C Recommended, self-descriptive language that is designed to store and transport data. A developer can change the XML format into any other better human-readable format like PDF or MS Word document within the .NET application. This article will discuss **how to convert XML data into PDF and MS Word reports using C#** via simple templates.



{{< figure align=center src="images/xml-to-pdf-word-report-in-csharp.jpg" alt="XML to PDF Report in C#">}}


The following topics are discussed below:

*   [.NET API for Generating Reports][1]
*   [Generate PDF Report from XML Data using C#][2]
*   [Generate MS Word DOC/DOCX Report from XML Data using C#][3]

## Report Generation .NET API – XML to PDF and WORD {#generate-report-dotnet-api}

[GroupDocs.Assembly for .NET][4] is the API to automate the report generation from the **XML** data using **DOCX** or **TXT** template. Additionally, it supports the **JSON, CSV,** and other data sources to convert the data into reports of different file formats.

You can download the **DLLs** or **MSI** installer from the [downloads section][5] or install the API in your .NET application via [NuGet][6].

```
PM> Install-Package GroupDocs.Assembly
```

## Generate PDF Report from XML Data in C# {#xml-to-pdf-report-in-csharp}

3 simple steps will lead you to convert XML data into the formatted PDF report.

1.  Load your XML data source.
2.  Define the template according to the loaded XML data.
3.  Finally, provide XML data source and template to a report generation method.

### XML Data

The following XML sample data is used to get it converted to the PDF report. It contains the data of managers and their respective clients with some more details.

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

### Template

Define the template in TXT or DOCX format according to your source XML data. I am using the below mentioned template that is created according to the above mentioned XML data of managers. This will make the report generator to iterate over Managers and their respective Clients. After the completion of template, you are almost done. You can use the code below for your report generation.

```
<<foreach \[in managers\]>>Manager: <<\[Name\]>>
Contracts:
<<foreach \[in Contract\]>>- <<\[Client.Name\]>> ($<<\[Price\]>>)
<</foreach>>
<</foreach>>
```

### C# Steps to Generate PDF Report from XML

The following steps allow you to automate the generation of PDF reports from your XML data according to your defined template.

*   Define XML data file, text template file, and PDF output report files.
*   Instantiate [XMLDataSoure][7] with XML data file.
*   Create [DataSourceInfo][8] with defined XML data source.
*   Call the [AssembleDocument][9] method to generate the PDF report.

The following code implements the above steps and generates a PDF from the XML data source using C#.

{{< gist GroupDocsGists ea7405ab3694830098c08589057c385c "XmlToPdfReport.cs" >}}

## Generate MS Word Report from XML data in C# {#xml-to-word-report-in-csharp}

In the same vein, you can also create the report in MS Word DOC/DOCX format using the same XML data. There will be no difference in the code from the one we discussed above, except that you have to change the output file name.

*   Load the XML data file.
*   Defining the template in TXT or DOCX format.
*   Set the output report document format as DOCX.
*   Provide the XML data file, template, and output file path to [DocumentAssembler][10] to convert the XML to DOCX.

The following code converts the XML and generates the DOCX file using the defined template using C#.

{{< gist GroupDocsGists ea7405ab3694830098c08589057c385c "XmlToWordReport.cs" >}}

## Get a Free API License

You can [get a free temporary license][11] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you have learned to convert the XML data into PDF format as a report using C# with the .NET application. Additionally, we discussed the report generation in DOC/DOCX format from the same XML using the template. After reading this series of report generation posts; Generate PDF and MS Word Reports from **[JSON][12]**, **[CSV][13]**, **XML**, you can develop your own report building .NET application.

For more about GroupDocs.Assembly, options, and examples, visit [documentation][14] and the [GitHub][15] repository. For further queries, contact us via the [forum][16].

## See Also

*   [Convert JSON Data to PDF or Word Report using C#][17]
*   [Transform CSV Data into PDF or Word Report using C#][18]







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

