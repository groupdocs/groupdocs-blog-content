---
title: 'Watermark Excel Sheets in Java'
seoTitle: "Add Watermark to Excel Workbooks in Java | Text Watermarks"
description: "Insert watermarks into Excel workbooks using Java. Watermark all sheets or apply it to just specific sheet even as background using watermark Java API."
date: Wed, 10 Nov 2021 14:04:00 +0000
draft: false
url: /2021/11/10/watermark-excel-sheets-in-java/
author: 'Shoaib Khan'
summary: 'Watermarks can be added to the documents either to protect the document from piracy, or to show any sumbol or message. In other posts, we discussed ways to watermark different [documents][1], [images][2], and [presentations][3]. In this article, you will learn **how to add watermark to Excel workbooks in different ways in Java**. We will be applyling watermarks separately using each approach.

The following topics are covered in this article:

*   Watermarking API for Java
*   Add **Text Watermark** to Excel Sheets
*   Apply Watermark to **Specific Excel Sheet**
*   Add Watermark to Excel Sheet **as Background**'
tags: ['add watermark in java', 'how to add watermark in Java', 'watermark excel', 'watermark excel sheets in Java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermark-to-excel-java.jpg" alt="Add Watermark to Excel Sheet in Java">}}


Watermarks can be added to the documents either to protect the document from piracy or to show any symbol or message. In other posts, we discussed ways to watermark different documents, images, and presentations. In this article, you will learn how to add watermark to Excel workbooks in different ways in Java. We will be applying watermarks separately using each approach.

The following topics are covered below:

*   [Watermarking API for Java][4]
*   [Add **Text Watermark** to Excel Sheets][5]
*   [Apply Watermark to **Specific Excel Sheet**][6]
*   [Add Watermark to Excel Sheet **as Background**][7]

## Java API to Watermark Excel Sheets {#watermarking-java-api}

[GroupDocs.Watermark for Java][8] is the API to automate the watermarks for documents, presentations, images, and many other file formats. The complete list of supported document formats is available in the [documentation][9].

You can download the **JAR** file from the [downloads section][10] or use the latest repository and dependency [Maven][11] configurations within your Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## Watermark Excel Sheets using Java {#watermark-all-sheets}

The watermarking API provides customization while inserting the watermark to the spreadsheets as a text. The following are the steps to add watermarks to Excel workbooks in Java.

*   Load the source spreadsheet using [Watermarker][12] and the [SpreadsheetLoadOptions][13].
*   Define the watermark text and appearance properties using [TextWatermark][14].
*   Add the defined watermark to the Excel worksheet using [add()][15] mehtod.
*   Save the resultant spreadsheet with watermark using the [save()][16] method.

The following Java code sample adds the text watermark to all the sheets of the Excel workbook with rotation and opacity and the set alignment.

{{< gist GroupDocsGists a8ff600a6d3b7460f52abe2836bffe0a "AddWatermarkToAllSheets.java" >}}

## Watermark Specific Excel Sheet using Java {#watermark-any-sheet}

Likewise, you can also insert watermarks into any single sheet of the workbook. The following steps guide on how to apply text watermark to the specific sheet of the Excel workbook in Java.

*   Load the spreadsheet using the [Watermarker][17].
*   Set the watermark appearance and text using the [TextWatermark][18].
*   Set the worksheet index so that watermark is applied to the mentioned sheet only.
*   Add the text watermark to the Excel worksheet using [add()][19] mehtod with watermarking options.
*   Save the output spreadsheet having the watermark using the [save()][20] method.

The following Java code snippet applies the text watermark to only the mentioned sheet of the Excel workbook.

{{< gist GroupDocsGists a8ff600a6d3b7460f52abe2836bffe0a "AddWatermarkToSpecificSheet.java" >}}

## Watermark Excel Sheets as Background using Java {#watermark-sheet-as-background}

Likewise, we can also add watermarks as the background of the spreadsheet. There will be some modification to the above approach to applying watermarks. The following are the steps that insert background text watermark to Excel spreadsheet in Java.

*   Load the spreadsheet using [Watermarker][21].
*   Prepare the watermark text and its appearance using [TextWatermark][22].
*   Set the watermark settings to make it as background using watermarking options by getting content and setting dimensions.
*   Add the watermark to the workbook sheets using the [add()][23] mehtod.
*   Lastly, save the watermarked spreadsheet using the [save()][24] method.

The following code sample can be used to add a background text watermark to an Excel spreadsheet in Java.

{{< gist GroupDocsGists a8ff600a6d3b7460f52abe2836bffe0a "AddWatermarkToExcelAsBackground.java" >}}



{{< figure align=center src="images/watermark-excel-sheets-programmatically.png" alt="Watermark Excel Sheets Programmatically">}}


## Get a Free API License

You can [get a free temporary license][25] in order to use the API without the evaluation limitations.

## Conclusion

In this article, we discussed that how we can add watermarks to the excel sheets in different ways within the Java application. We learned to insert text watermark to all the sheets of the Excel workbook, and then we applied the watermark to the specific sheet only. Later, we applied the watermark as a background. You can now use this feature and build your own application to watermark spreadsheets.

Learn more about the API from the [documentation][26]. For queries, contact us via the [forum][27].

## See Also

*   [Watermark Excel Sheets using C#][28]
*   [Watermark PDF Files in Java][29]
*   [Add Watermark to Images in Java][30]
*   [Watermark Presentation Slides using Java][31]
*   [Find and Remove Watermarks from Documents in Java][32]







[1]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[3]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[4]: #watermarking-java-api
[5]: #watermark-all-sheets
[6]: #watermark-any-sheet
[7]: #watermark-sheet-as-background
[8]: https://products.groupdocs.com/watermark/
[9]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[10]: https://downloads.groupdocs.com/watermark
[11]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-watermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/SpreadsheetLoadOptions
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[16]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[19]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[20]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[21]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[22]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[23]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[24]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[25]: https://purchase.groupdocs.com/temporary-license
[26]: https://docs.groupdocs.com/watermark
[27]: https://forum.groupdocs.com/
[28]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[29]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[30]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[31]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[32]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/

