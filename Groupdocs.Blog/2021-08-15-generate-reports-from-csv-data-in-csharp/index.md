---
title: "Generate Reports from CSV Data using C#"
seoTitle: "PDF & Word Reports from CSV Data using C# | .NET Reporting API"
description: "Convert CSV to PDF & Word formats with templates using C#. Automate PDF & DOC/DOCX reports generation using .NET Reporting API by GroupDocs."
date: Sun, 15 Aug 2021 10:50:32 +0000
draft: false
url: /2021/08/15/generate-reports-from-csv-data-in-csharp/
aliases:
    - /2019/10/21/generate-reports-from-csv-xml-in-csharp/
    - /2019/10/21/generate-reports-from-csv-json-xml/
    - /2019/10/21/generate-reports-from-csv-json-xml-in-csharp/
    - /2019/10/21/generate-reports-from-csv-data-source/
    - /2019/10/21/generate-reports-from-csv-data-source-in-groupdocs.assembly-for-.net-19.10/
author: 'Shoaib Khan'
summary: 'CSV ([Comma Separated Values][1] files are widely used for exchanging data among applications. When you want this data to be translated into presentable and meaningful information, you need to convert it into some other format. In one of our posts, we have seen [how to convert CSV data in Reports using Java][2]. This article will guide you to **convert CSV data into PDF and MS Word DOC/DOCX reports using C#** using a simple template.'
tags: ['Convert CSV to PDF in CSharp', 'CSV to PDF using template', 'CSV to Word Report in CSharp', 'Generate PDF report from CSV', 'Generate Reports', 'generate reports in csharp']
categories: ['GroupDocs.Assembly Product Family']
---

CSV ([Comma Separated Values][3] files are widely used for exchanging data among applications. When you want this data to be translated into presentable and meaningful information, you need to convert it into some other format. In one of our posts, we have seen [how to convert CSV data in Reports using Java][4]. This article will guide you to **convert CSV data into PDF and MS Word DOC/DOCX reports using C#** using a simple template.

The following topics are covered below:

*   [Report Generation .NET API][5]
*   [Generate PDF Report from CSV Data][6]
*   [Generate MS Word Report from CSV data][7]

## Report Generation .NET API {#report-generator-dotnet-api}

[GroupDocs.Assembly][8] provides the .NET reporting API to automate the report generation. In this article, I have used this [GroupDocs.Assembly for .NET][9] for generating reports from the selected **CSV** data and a **TXT** format template. It also supports multiple data sources like **JSON, XML**, and also from **MS Word**, **Excel**, and **PowerPoint** files as data files.

You can download the **DLLs** or **MSI** installer from the [downloads section][10] or install the API in your .NET application via [NuGet][11].

```
PM> Install-Package GroupDocs.Assembly
```

## Generate PDF Report from CSV Data in C# {#csv-to-pdf-report-csharp}

Let's begin by transforming the comma-separated data into a presentable PDF. The following steps will guide you to convert the CSV data into a formatted PDF report.

*   Load CSV data source.
*   Define template according to the CSV data.
*   Provide CSV data source and template to simple method to generate PDF report.



{{< figure align=center src="images/csv-to-pdf-word-report-in-csharp.jpg" alt="CSV to PDF Report in C#">}}


### CSV Data

To get the PDF report, I will be using the following sample CSV data of different individuals along with their respective data of ages and date of birth.

```
Name,Age,Birth  
John Doe,32,4/1/1989 16:00  
Jane Doe,29,1/31/1992 7:00  
John Smith,53,3/8/1968 13:00
```

### Template

The next step would be to define the template in TXT or DOCX format. The following is the template that is used in this example and allows iterating the list of persons with their details.

```
<<foreach \[in persons\]>>Name: <<\[Name\]>>, Age: <<\[Age\]>>, Date of Birth: <<\[Birth\]:"dd.MM.yyyy">>
<</foreach>>
Average age: <<\[persons.Average(p => p.Age)\]>>
```

### Steps to Generate PDF Report from CSV in C#

The following steps guide about converting the CSV data into a PDF report according to the defined template using C# with the .NET Reporting API.

*   Define CSV data file, template file, and the PDF output file paths.
*   Instantiate [CsvDataSoure][12] with CSV data file and loading options.
*   Create [DataSourceInfo][13] with the defined data source.
*   Using the [DocumentAssembler][14], call the [AssembleDocument][15] method with defined template file, output file and DataSourceInfo to get the PDF report as output.

The following code shows how to convert CSV data to PDF report in C#.

{{< gist GroupDocsGists 39a6cdabd9133f9b8349b78e95b56a4b "GeneratePdfReportFromCSV.cs" >}}

## Generate MS Word Report from CSV data in C# {#csv-to-docx-report-java}

If you want any manual editing in the automated generated report, you can also get the output as an MS Word document. The process will be very similar to the above PDF report generation. The following steps will guide to generate the DOC/DOCX report from the CSV data:

*   Load the CSV data from file.
*   Defining the template in TXT or DOCX format.
*   Set the output report document format as DOC/DOCX.
*   Call the [AssembleDocument][16] method to generate MS Word DOCX report from the CSV data.

The following code shows how to convert CSV data into a DOCX report using C#.

{{< gist GroupDocsGists 39a6cdabd9133f9b8349b78e95b56a4b "GenerateWordReportFromCSV.cs" >}}

## Get a Free API License

You can [get a free temporary license][17] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you have learned to convert the CSV data into PDF and MS Word reports using C#. You must now be confident building your own .NET report generator application by converting CSV data into PDF format. Similarly, you can also generate reports using other data sources like JSON and XML.

For more about the API, you can visit [documentation][18] and the [GitHub][19] repository. In case of further queries and ambiguities, contact the free support on the [forum][20].

## See Also

*   [Generate Reports from JSON Data using C#][21]
*   [Generate Reports from CSV Data using Java][22]







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

