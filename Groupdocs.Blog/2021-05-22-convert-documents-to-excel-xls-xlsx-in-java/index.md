---
title: "Convert Documents to Excel XLS, XLSX in Java"
seoTitle: "Convert to Spreadsheet in Java | PDF to Excel | Word to XLS XLSX"
description: "Convert DOC, DOCX to Excel (XLS, XLSX) or convert PDF to Excel spreadsheet in Java using document conversion Java API. Build your own Conversion App."
date: Sat, 22 May 2021 18:39:23 +0000
draft: false
url: /2021/05/22/convert-documents-to-excel-xls-xlsx-in-java/
author: 'Shoaib Khan'
summary: "For the data in tabular form of your PDF and Word documents, you sometimes need to convert it to Excel spreadsheets. We need to automate this conversion of as many documents to spreadsheets or multiple workbooks. This article will discuss how to programmatically convert Word documents to Excel and also how to convert PDF files to Excel spreadsheets in Java."
tags: ['Convert to Excel in Java', 'DOC to XLS in Java', 'DOCX to XLSX in Java', 'PDF to Excel in Java', 'Word to Excel in Java']
categories: ['GroupDocs.Conversion Product Family']
---

For the data in tabular form of your PDF and Word documents, you sometimes need to convert it to Excel spreadsheets. We need to automate this conversion of as many documents to spreadsheets or multiple workbooks. This article will discuss how to programmatically convert Word documents to Excel and also how to convert PDF files to Excel spreadsheets in Java.



{{< figure align=center src="images/pdf-word-to-xls-in-java.jpg" alt="Convert Word and PDF to Excel in Java">}}


The following topics are discussed briefly here:

*   [Java API - Documents to Spreadsheets Conversion][2]
*   [Convert PDF to Excel Spreadsheet][3]
*   [Convert Word to Excel Spreadsheet][4]
*   [PDF or Word to Spreadsheet conversion with more options][5]

## Java API for Conversion to Spreadsheet {#convert-to-spreadsheet-java-api}

[GroupDocs.Conversion for Java][6] is the API that allows you to convert PDF and Word documents to spreadsheets within your Java applications. The API allows document and image conversions in many file formats. Some of the supported document formats include word-processing documents, spreadsheets, presentations, eBooks, AutoCAD formats, PDF, email messages, Web pages, images.

### Download and Configure

You can get the conversion library from the downloads section or add the following pom.xml configuration in your Maven-based Java application. Afterward, you can try examples of this article as well as many more examples available on [GitHub][7]. For the details, you may visit the [API Reference][8].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.4</version> 
</dependency>
```

## Convert PDF to Excel in Java {#pdf-to-excel-csharp}

The following steps can be followed to convert any PDF document to an Excel spreadsheet.

*   Load the PDF file using [Converter][9] class.
*   Prepare convert options using [SpreadsheetConvertOptions][10].
*   Call the [convert][11] method with the created options.

The following code sample shows how to convert a PDF file into an Excel XLSX spreadsheet in Java.

{{< gist GroupDocsGists c54011c23506f561da98126b8307f13c "ConvertPdfToExcel.java" >}}

## Convert Word to Excel in Java {#word-to-excel-csharp}

Similarly, any Word document can be converted to an Excel spreadsheet in the same manner as we just converted the PDF document. Provide the right source file and get it converted into XLS or XLSX.

The following are the step to convert any DOC DOCX file to an Excel spreadsheet.

*   Load the DOC, DOCX file using Converter class.
*   Prepare the convert options using SpreadsheetConvertOptions.
*   Call the convert method of the Converter class with options.

The following source code shows how to convert a DOC or DOCX file into Excel XLSX format in Java.

{{< gist GroupDocsGists c54011c23506f561da98126b8307f13c "ConvertWordToExcel.java" >}}

## PDF or Word to Spreadsheet Conversion with more options using Java {#pdf-word-to-excel-adv}

You are not bound to get the whole document converted every time. You can convert just the selected pages of your document. The API gives you the privilege to convert the document with various options that include:

*   Starting **Page Number**.
*   **Page Count**.
*   **Specific Pages** for conversion.
*   **Format** to convert into.
*   **Password** for make the file protected.
*   **Zoom** to make it large or smaller.
*   **Watermark** on the converter file.

The following are the steps for how to convert some of the pages of a PDF file into XLSX format with different zoom in Java.

{{< gist GroupDocsGists c54011c23506f561da98126b8307f13c "ConvertPdfToExcelAdv.java" >}}

The PDF file and the converted spreadsheet as output are shown here. It converted the second page of the PDF file into XLSX format.



{{< figure align=center src="images/pdf-to-xls-in-csharp.jpg" alt="Convert PDF to Excel XLS XLSX Programmatically">}}


## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][12] in order to use the API without evaluation limitations.

## Conclusion

In this article, we discussed the conversion of PDF and Word documents to an Excel spreadsheet in Java. Additionally, we learned how to convert any part of the document with options like watermark, zoom, and make it protected using password protection.

For more options and examples, visit the [documentation][13] and the [GitHub][14] repository. For queries, reach us via the [forum][15].

## See Also

*   [Images to PDF in Java][16]
*   [Spreadsheets to PDF in Java][17]
*   [Presentations to PDF in Java][18]
*   [CAD Drawings to PDF in Java][19]







[1]: https://blog.groupdocs.com/2021/05/22/convert-documents-to-excel-xls-xlsx-in-java
[2]: #convert-to-spreadsheet-java-api
[3]: #pdf-to-excel-csharp
[4]: #word-to-excel-csharp
[5]: #pdf-word-to-excel-adv
[6]: https://products.groupdocs.com/conversion/net
[7]: https://github.com/groupdocs-conversion
[8]: https://apireference.groupdocs.com/conversion/java
[9]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[10]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/conversion
[14]: https://github.com/groupdocs-conversion
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[17]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[18]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
[19]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/

