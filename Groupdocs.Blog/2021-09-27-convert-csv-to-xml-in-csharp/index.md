---
title: "Convert CSV to XML in C#"
seoTitle: "CSV to XML in C# | Convert CSV Data to XML Format"
description: "Convert CSV data to XML format using C#. Automate the CSV to XML conversion within your .NET application using document and file format conversion API."
date: Mon, 27 Sep 2021 12:59:00 +0000
draft: false
url: /2021/09/27/convert-csv-to-xml-in-csharp/
author: 'Shoaib Khan'
summary: "CSV and XML are among the most popular file formats used by developers. These formats are normally used to store and exchange data within and between applications. It is often required to convert one format into another before storing or transmitting the information. In this article, you will find **how to programmatically convert the CSV (comma-separated values) file into XML format using C#**."
tags: ['Convert CSV to XML', 'Convert CSV to XML in CSharp', 'CSV to XML', 'CSV to XML in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

CSV and XML are among the most popular file formats used by developers. These formats are normally used to store and exchange data within and between applications. It is often required to convert one format into another before storing or transmitting the information. In this article, you will find **how to programmatically convert the CSV (comma-separated values) file into XML format using C#**.



{{< figure align=center src="images/convert-csv-to-xml-using-csharp.jpg" alt="Convert CSV to XML using CSharp">}}


The article covers the following topics:

*   [.NET API - CSV to XML Conversion][1]
*   [How to Convert CSV to XML in C#][2]

## .NET API for CSV to XML Conversion {#csv-to-xml-dotnet-api}

[GroupDocs.Conversion][3] provides APIs that allow the CSV and XML files conversions. In this article, we will use the .NET API of GroupDocs.Conversion for converting the CSV format data into XML format using C#. Additionally, the API supports many other file formats for conversion like word-processing documents, spreadsheets, presentations, eBooks, images, etc.

You can download the **DLLs** or **MSI** installer from the [downloads section][4] or install the API in your .NET application via [NuGet][5].

```
PM> Install-Package GroupDocs.Conversion
```

## Convert CSV to XML in C# {#csv-to-xml}

The CSV files can be viewed and visually edited using editors like MS Excel. The image shows the CSV data that I have used for the conversion. There are many CSV to XML converters available online, however, the code mentioned in this section can empower your .NET applications with this simple conversion.



{{< figure align=center src="images/csv-sample-file-opened-in-excel.jpg" alt="CSV Sample file opened in Excel">}}


The following steps guide you to convert the provided data of CSV format into XML format.

*   Load the CSV file using the [Converter][6] class.
*   Set the conversion format as XML using the [DataConvertOptions][7].
*   Call the [Convert][8] method to get the XML format data from the loaded CSV file.

The following source code converts the CSV file to XML format using C#.

{{< gist GroupDocsGists 240c47d8a3ab8debabd13be9a83eac3a "ConvertCsvToXML.cs" >}}

The output of the above code is as follows. I am sharing the part of the XML file for you to get an idea of the XML output.

```
<DocumentElement>
  <Sheet1>
    <Employee>David</Employee>
    <Quarter>1</Quarter>
    <Product>Maxilaku</Product>
    <Continent>Asia</Continent>
    <Country>China</Country>
    <Sale>2000</Sale>
  </Sheet1>
  <Sheet1>
    <Employee>David</Employee>
    ...
  </Sheet1>
  <Sheet1>
    ...
  </Sheet1>
</DocumentElement>
```

## Get a Free API License

You can [get a free temporary license][9] to use the API without the evaluation limitations.

## Conclusion

To sum up, we discussed the conversion of CSV data into XML format within the .NET applications using C#. To build your own conversion app, you may learn more about the Conversion Automation .NET API using the [documentation][10]. The best is to experience the examples available on [GitHub][11]. Contact us for any query via the [forum][12].

## See Also

*   [JSON to XML Conversion in C#][13]
*   [Convert JSON to CSV and CSV to JSON using C#][14]
*   [Convert Excel to CSV and CSV to Excel Formats in C#][15]







[1]: #csv-to-xml-dotnet-api
[2]: #csv-to-xml
[3]: https://products.groupdocs.com/conversion/
[4]: https://downloads.groupdocs.com/conversion
[5]: https://www.nuget.org/packages/groupdocs.conversion
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://docs.groupdocs.com/conversion/net/
[11]: https://github.com/groupdocs-conversion
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/09/11/convert-json-to-xml-in-csharp/
[14]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[15]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/

