---
title: "Extract ZIP Files Data in C#"
seoTitle: "Extract Archive Files Data using C# | ZIP, RAR, TAR, GZIP, BZIP2"
description: "Extract data of compressed archives like ZIP, RAR, TAR, GZIP, BZIP2 files using C# in .NET application. Parse archives and extract whole text within files."
date: Wed, 25 Aug 2021 12:43:51 +0000
draft: false
url: /2021/08/25/extract-zip-files-data-in-csharp/
author: 'Shoaib Khan'
summary: "Archives like **ZIP, RAR, TAR, GZIP, BZIP2** are commonly used to store more than one file and folder in a single container. Another main reason for archive files is to reduce the total file size using compression algorithms. Just like parsing and extracting data from documents of various file formats, you can treat the archive files in the same way. You can extract the text, images, and even metadata from the files that are compressed within the archives. In this article, we will discuss **how to extract the ZIP archives data using C#** with your .NET applications."
tags: ['Extract Archives in CSharp', 'Extract from ZIP in C#', 'unzip data in C#']
categories: ['GroupDocs.Parser Product Family']
---

Archives like **ZIP, RAR, TAR, GZIP, BZIP2** are commonly used to store more than one file and folder in a single container. Another main reason for archive files is to reduce the total file size using compression algorithms. Just like parsing and extracting data from documents of various file formats, you can treat the archive files in the same way. You can extract the text, images, and even metadata from the files that are compressed within the archives. In this article, we will discuss **how to extract the ZIP archives data using C#** with your .NET applications.

The following topics are covered below:

*   [.NET API for ZIP files data extraction][1]
*   [How to extract ZIP files data][2]

## .NET API to Extract ZIP files Data {#dotnet-zip-files-extraction-api}

[GroupDocs.Parser][3] provides the document parsing solution for developers. I will be using its [.NET API to extract ZIP files data][4] within the C# examples of this article. The API further allows extraction of text, images, and metadata from a long list of [supported document formats][5] like word-processing documents, presentations, spreadsheets, emails, databases, eBooks, and many others.

You can download the **DLLs** or **MSI** installer from the [downloads section][6] or install the API by adding its package to your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Parser
```

## How to Extract ZIP Files Data in C# {#how-to-extract-zip-data}

The [GroupDocs.Parser for .NET][8] supports data extraction from various compression file formats like ZIP, RAR, TAR, BZIP2, & GZIP. After retrieving the collection of files from the compressed file, you can further extract any kind of data from each file.

The following steps show how to extract ZIP files data and retrieve text from each enclosed file in C#.

*   Load the ZIP archive using **[Parser][9]** class.
*   Obtain the attachments using **_[GetContainer][10]_** method
*   Traverse the collection of attachments.
*   For each attachment, you can get its different kind of data using respective methods of the **Parser** class.

The source code shows how to extract the ZIP files data using C#. In this example, I will be extracting the whole text from all the files within the ZIP archive.

{{< gist GroupDocsGists 184c6265993d61b5f7a8f106835337dc "ExtractDataFromZipArchive.cs" >}}

The output of the above source code shows the text retrieved from one of the PDF files within the ZIP file.

```
 -----------------------------------
 Name: sample.pdf
 File Size: 33370 Bytes
 -----------------------------------

 Heading

 This is the first paragraph of the sample document that contains some sample
 text, bulleted list, numbered list and more.

    •  Bullet Item 1
    •  Bullet Item 2
    •  Bullet Item 3
 
 This is the second paragraph of the sample document and after this, there is a
 numbered list: 

    1. Numbered Item 1
    2. Numbered Item 2
    3. Numbered Item 3 
```

## Get a Free API License

You can [get a free temporary license][11] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you learned how to extract ZIP archives data using C# within your .NET application. More specifically you can now extract data from ZIP, RAR, TAR, GZIP, and BZIP files. You can even build your own data extraction .NET application for compressed files. For more details or learning about the API, visit the [documentation][12]. For queries, contact us via the [forum][13].

## See Also

*   [Extract Images from Documents using C#][14]
*   [Extract Images from EPUB, FB2, CHM eBooks in C#][15]
*   [Read PDF Form Fields using C#][16]







[1]: #dotnet-zip-files-extraction-api
[2]: #how-to-extract-zip-data
[3]: https://products.groupdocs.com/parser/
[4]: https://products.groupdocs.com/parser/net/
[5]: https://docs.groupdocs.com/parser/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/parser
[7]: https://www.nuget.org/packages/groupdocs.parser
[8]: https://products.groupdocs.com/parser/net/
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[10]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getcontainer
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/parser/
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[15]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[16]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/

