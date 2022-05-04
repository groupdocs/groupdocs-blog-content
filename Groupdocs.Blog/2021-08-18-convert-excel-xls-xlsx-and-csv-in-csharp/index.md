---
title: "Convert Excel to CSV and CSV to Excel Formats in C#"
seoTitle: "Convert Excel and CSV Data in C# | XLSX to CSV - CSV to XLS"
description: "Convert XLS & XLSX to CSV and CSV to Excel formats within Java applications. Automate your files conversion using Java API for document conversion."
date: Wed, 18 Aug 2021 03:39:00 +0000
draft: false
url: /2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
author: 'Shoaib Khan'
summary: "XLS and XLSX are the most used and well-known formats of MS Excel spreadsheets. You must be well aware of the enhanced capabilities and countless formatting options of Microsoft Office for these formats during this century. On the other hand, **CSV** files are the comma-separated-values, normally used to store tabular data without formatting. These files can be viewed in any text editor and also in MS Excel for tabular format. This article discusses the conversion of the Excel spreadsheets of **XLS/XLSX format into CSV** format and **CSV to XLS/XLSX **format programmatically **using C#**."
tags: ['Convert XLS and CSV in C#', 'CSV to Excel', 'CSV to Excel in C#', 'CSV to XLSX in C#', 'Excel to CSV', 'Excel to CSV in C#', 'XLSX to CSV in C#']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-xlsx-to-csv-and-csv-to-excel-in-csharp.jpg" alt="Convert XLS XLSX to CSV in C#">}}


XLS and XLSX are the most used and well-known formats of MS Excel spreadsheets. You must be well aware of the enhanced capabilities and countless formatting options of Microsoft Office for these formats during this century. On the other hand, **CSV** files are the comma-separated values, normally used to store tabular data without formatting. These files can be viewed in any text editor and also in MS Excel for tabular format. This article guides to convert Excel spreadsheets of **XLS/XLSX format into CSV** format and **CSV to XLS/XLSX **format programmatically **using C#**.

The following topics are covered below:

*   [.NET API for XLS/XLSX and CSV Conversion][1]
*   [Excel to CSV Conversion][2]
*   [CSV to Excel Conversion][3]

## .NET API for Excel Files and CSV Conversion {#excel-csv-dotnet-api}

[GroupDocs.Conversion][4] provides a .NET API that allows automating the conversion of various documents and image file formats into one another. I will be using this API to convert XLSX into CSV and then CSV into XLS or XLSX using C#. Along with the spreadsheet formats, the API supports [back and forth conversion of many other document and image formats][5] like word-processing documents, presentations, eBooks, JPG, PNG, WebP, and many more.

You can download the **DLLs** or **MSI** installer from the [downloads section][6] or install the API in your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Conversion
```

## Convert Excel (XLS/XLSX) to CSV in C# {#excel-to-csv}

Let's start with the tabular and well-formatted data in XLS or XLSX format, and convert it into unformatted comma-separated CSV format. The following steps allow converting the XLS or XLSX format to CSV within the .NET applications.

*   Load the Excel file (XLS or XLSX) using the [Converter][8] class.
*   Set the starting worksheet number and sheet count. (Optional)
*   Set the conversion format of the output file as CSV using [SpreadsheetConvertOptions][9].
*   Call the [Convert][10] method to transform the spreadsheet data or and specific pages into CSV format.

The following code shows how to convert XLS or XLSX into CSV format in C#.

{{< gist GroupDocsGists 53e4d00e8195ad3eb4ba03fffc4e9315 "ConvertExcelToCSV.cs" >}}

## Convert CSV to Excel (XLS/XLSX) in C# {#csv-to-excel}

On the contrary, if you have the comma-separated data and you want to convert it into a well-formatted tabular format, you need to convert that CSV data into XLS or XLSX format. The following steps show how to convert the CSV file into MS Excel XLSX format using C#.

*   Prepare the loading options for CSV file and define separator.
*   Load the CSV using the [Converter][11] class.
*   Set the conversion format to XLSX using [SpreadsheetConvertOptions][12].
*   Use the [Convert][13] method to get the CSV data transformed into XLSX format.

The following code shows how to convert your CSV file into XLSX format in C#.

{{< gist GroupDocsGists 53e4d00e8195ad3eb4ba03fffc4e9315 "ConvertCsvToExcel.cs" >}}

Just set the conversion format accordingly and provide the appropriate file name with the extension for the XLS or any other file format.

## Get a Free API License

You can [get a free temporary license][14] in order to use the API without the evaluation limitations.

## Conclusion

To sum up the article, you learned back and forth conversion of MS Excel spreadsheets XLS/XLSX and CSV files using C#. You can learn more about the .NET Conversion Automation API using the documentation, or by experiencing the examples available on GitHub. Reach us for any query via the [forum][15].

## Related Article

*   [Convert CSV to Excel, and (XLS or XLSX) to CSV in Java][16]

## See Also

*   [Generate Reports from CSV Data using C#][17]
*   [Convert Excel Spreadsheets to PDF using C#][18]
*   [Convert JSON to CSV and CSV to JSON using C#][19]
*   [Insert OLE Objects in Word, Excel, PowerPoint with C#][20]







[1]: #excel-csv-dotnet-api
[2]: #excel-to-csv
[3]: #csv-to-excel
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/
[17]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[19]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[20]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/

