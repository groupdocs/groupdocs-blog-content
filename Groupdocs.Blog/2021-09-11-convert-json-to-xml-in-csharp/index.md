---
title: 'Convert JSON to XML in C#'
date: Sat, 11 Sep 2021 09:17:00 +0000
draft: false
url: /2021/09/11/convert-json-to-xml-in-csharp/
author: 'Shoaib Khan'
summary: 'JSON and XML, both are the well known structured formats that are vastly used by developers to transmit data. There are many requirement where as a programmer, we need the conversion between JSON and XML data formats. In this article, you will learn how to convert JSON data into XML format using C#.

The following topics will be covered in this article:

*   .NET API for JSON and XML Conversion
*   Programmatically Convert JSON to XML'
tags: ['Convert JSON to XML', 'Convert JSON to XML in CSharp', 'JSON to XML', 'JSON to XML in CSharp']
categories: ['GroupDocs.Conversion Product Family']
---

JSON and XML, both are well-known structured formats that are vastly used by developers to transmit data. There are many requirements where, as a programmer, we need the conversion between JSON and XML data formats. In this article, you will learn **how to convert JSON data into XML format using C#**.



{{< figure align=center src="images/convert-json-to-xml-csharp.jpg" alt="Convert JSON to XML in CSharp">}}


The following topics are covered below:

*   [.NET API for JSON and XML Conversion][1]
*   [Programmatically Convert JSON to XML][2]

## .NET API for JSON and XML Conversion {#json-xml-conversion-dotnet-api}

[GroupDocs.Conversion][3] provides a .NET API that allows automating the conversion of different documents, images, and other file formats into one another. I am using the same API here to convert JSON files into XML format using C#. Along with the JSON and XML conversion, the API supports many other [back and forth conversions][4] like word-processing documents, presentations, eBooks, JPG, PNG, WebP, and many more. You can see the details on the documentation.

You can download the **DLLs** or **MSI** installer from the [downloads section][5] or install the API in your .NET application via [NuGet][6].

```
PM> Install-Package GroupDocs.Conversion
```

## Convert JSON to XML in C# {#json-to-xml}

Both the JSON and XML formats are commonly used in web-based applications to transmit data. These are structured, human-readable, hierarchical formats to store and exchange data.

The following steps guide you to convert the JSON data into XML format using .NET API.

*   Load the JSON data file using [Converter][7] class.
*   Use the [DataConvertOptions][8] to set the conversion format to XML.
*   Call the [Convert][9] method of Converter class to transform the JSON Data into XML format

The following code converts the JSON data into XML format using C#.

{{< gist GroupDocsGists d7223aa52bb2ff2656761887bd65a9ab "ConvertJsonToXml.cs" >}}

## Get a Free API License

You can [get a free temporary license][10] to use the API without the evaluation limitations.

## Conclusion

To conclude, you have learned the conversion of JSON data to XML format within your .NET applications using C#. You can learn more about the .NET Conversion Automation API using the [documentation][11], or by quickly experiencing the examples available on [GitHub][12]. Contact us for any query via the [forum][13].

## See Also

*   [Convert JSON and CSV using C#][14]
*   [Convert Excel and CSV using C#][15]







[1]: #json-xml-conversion-dotnet-api
[2]: #json-to-xml
[3]: https://products.groupdocs.com/conversion/
[4]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/conversion
[6]: https://www.nuget.org/packages/groupdocs.conversion
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/dataconvertoptions
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/conversion/net/
[12]: https://github.com/groupdocs-conversion
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/06/18/convert-json-and-csv-in-csharp/
[15]: https://blog.groupdocs.com/2021/08/18/convert-excel-xls-xlsx-and-csv-in-csharp/

