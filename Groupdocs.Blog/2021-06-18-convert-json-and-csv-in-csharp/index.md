---
title: "Convert JSON to CSV and CSV to JSON using C#"
seoTitle: "Convert JSON and CSV Data in C# | JSON to CSV | CSV to JSON"
description: "Convert JSON to CSV and CSV to JSON in C# within .NET applications. Examples convert the structured JSON data into comma-separated values CSV and vice-versa."
date: Fri, 18 Jun 2021 12:25:49 +0000
draft: false
url: /2021/06/18/convert-json-and-csv-in-csharp/
author: 'Shoaib Khan'
summary: "**JSON** (JavaScript Object Notation) is a human-readable structured data format. It is widely used in APIs, applications, and configurations for storing and passing the data. **CSV** contains the comma-separated values, normally used to store tabular data that can be perfectly displayed using spreadsheet applications like MS Excel. To transfer the tabular data or store the received structured data into tabular form, requires converting formats into one another. This article discusses the conversion of **JSON to CSV** format and **CSV to JSON** format programmatically **using C#** for your .NET applications."
tags: ['Convert CSV in CSharp', 'Convert JSON in CSharp', 'CSV to JSON in CSharp', 'JSON to CSV in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-csv-and-json-in-csharp.jpg" alt="Convert to CSV and JSON in CSharp .NET">}}


**JSON** (JavaScript Object Notation) is a human-readable structured data format. It is widely used in APIs, applications, and configurations for storing and passing the data. **CSV** contains the comma-separated values, normally used to store tabular data that can be perfectly displayed using spreadsheet applications like MS Excel. To transfer the tabular data or store the received structured data into tabular form, requires converting formats into one another. This article discusses the conversion of **JSON to CSV** format and **CSV to JSON** format programmatically **using C#** for your .NET applications.

The following topics are covered below:

*   [.NET API for JSON and CSV Conversion][1]
*   [JSON to CSV Conversion][2]
*   [CSV to JSON Conversion][3]

## .NET API for JSON and CSV Conversion {#json-csv-dotnet-api}

[GroupDocs.Conversion][4] has APIs that allow the conversion of JSON and CSV files into each other. In this article, we will use the .NET API of GroupDocs.Conversion for converting JSON into CSV and then CSV into JSON using C#. Additionally, the API allows the [back and forth conversion of various other document formats][5] like word-processing documents, spreadsheets, presentations, eBooks, images, and many more.

You can download the **DLLs** or **MSI** installer from the [downloads section][6] or install the API in your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Conversion
```

## Convert JSON to CSV in C# {#json-to-csv}

The following steps allow converting the JSON files to CSV format within the .NET applications.

*   Load the JSON using the [Converter][8] class.
*   Set the conversion format to CSV using [SpreadsheetConvertOptions][9].
*   Call the [Convert][10] method to transform the JSON data to CSV format.

The following code shows how to convert JSON to CSV format using C#.

{{< gist GroupDocsGists 499489bd99efab8b475e447083d377a6 "ConvertJsonToCSV.cs" >}}

## Convert CSV to JSON in C# {#csv-to-json}

The following steps allow converting the CSV files to JSON format within the .NET application.

*   Prepare the load options for loading the CSV file.
*   Load the CSV using the [Converter][11] class.
*   Set the conversion format to JSON using [DataConvertOptions][12].
*   Call the [Convert][13] method to get the CSV data transformed into JSON format.

The following code shows how to convert your CSV file into JSON format using C#.

{{< gist GroupDocsGists 499489bd99efab8b475e447083d377a6 "ConvertCsvToJSON.cs" >}}

## Get a Free API License

You can [get a free temporary license][14] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you learned how to convert the JSON files to CSV format and also the conversion of CSV files to JSON format programmatically using C#. You can learn more about the .NET Conversion API using the [documentation][15], or by examples available on [GitHub][16]. Get in touch with us at the [forum][17].

## See Also

*   [Convert Excel to CSV and CSV to Excel Formats in C#][18]
*   [Generate Reports from JSON Data in C#][19]
*   [Generate Reports from CSV and XML Data in C#][20]







[1]: #json-csv-dotnet-api
[2]: #json-to-csv
[3]: #csv-to-json
[4]: https://products.groupdocs.com/conversion/
[5]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/conversion
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/spreadsheetconvertoptions
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://docs.groupdocs.com/conversion/net/
[16]: https://github.com/groupdocs-conversion
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/
[19]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/
[20]: https://blog.groupdocs.com/2019/10/21/generate-reports-from-csv-xml-in-csharp/

