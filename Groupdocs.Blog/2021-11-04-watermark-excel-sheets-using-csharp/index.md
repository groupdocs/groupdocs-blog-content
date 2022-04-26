---
title: 'Watermark Excel Sheets using C#'
date: Thu, 04 Nov 2021 18:46:00 +0000
draft: false
url: /2021/11/04/watermark-excel-sheets-using-csharp/
author: 'Shoaib Khan'
summary: "We have already discussed ways to watermark different [documents][1], [images][2], and [presentations][3]. Today, we will be discussing how to add watermark to an Excel workbook in different ways using C# with the .NET application."
tags: ['add watermark in csharp', 'how to add watermark in csharp', 'watermark dotnet api', 'watermark excel', 'watermark excel sheets in csharp']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermark-to-excel-using-csharp.jpg" alt="Add Watermark to Excel Sheet using C#">}}


We have already discussed ways to watermark different [documents][4], [images][5], and [presentations][6]. Today, we will be discussing how to add watermark to an Excel workbook in different ways using C# with the .NET application.

The following topics are covered below:

*   [Watermarking API for .NET][7]
*   [Add **Text Watermark** to Excel Sheets][8]
*   [Apply Watermark to **Specific Excel Sheet**][9]
*   [Add Watermark to Excel Sheet **as Background**][10]

## .NET API to Watermark Excel Sheets {#watermarking-dotnet-api}

[GroupDocs.Watermark][11] provides the .NET API for documents and images of various file formats. We will use [GroupDocs.Watermark for .NET][12] to apply watermarks in spreadsheets in different ways using C#.

You can download the DLLs or MSI installer from the [downloads section][13] or get it from [NuGet][14].

```
Install-Package GroupDocs.Watermark
```

## Watermark Excel Sheets using C# {#watermark-all-sheets}

The API allows you to insert text to the spreadsheets as a watermark with different customizations. The following are the steps to add a watermark to Excel workbooks using C# with the .NET applications.

*   Prepare the loading options for spreadsheet.
*   Load the spreadsheet using [Watermarker][15].
*   Define the watermark text and appearance using [TextWatermark][16].
*   Add the text watermark to the Excel worksheet using [Add][17] mehtod.
*   Save the resultant spreadsheet with watermark using the [Save][18] method.

The following C# code sample applies the text watermark to all the sheets of the Excel workbook with rotation and opacity.

{{< gist GroupDocsGists 9d8b16b89e156aa787fe6c19c4db8ef4 "AddWatermarkToAllSheets.cs" >}}

## Watermark Specific Excel Sheet using C# {#watermark-any-sheet}

Similarly, you can apply watermarks to any specific sheet only instead of applying them to all the sheets of the workbook. The following steps guide on how to insert text watermark to the specific sheet of the Excel workbook using C#.

*   Prepare the loading options.
*   Load the spreadsheet using the [Watermarker][19] class.
*   Define the watermark appearance and text using the [TextWatermark][20] class.
*   Set the worksheet index so that watermark is applied to the mentioned sheet only.
*   Add the text watermark to the Excel worksheet using [Add][21] mehtod with watermarking options.
*   Save the output spreadsheet having the watermark using the [Save][22] method.

The following code snippet applies the text watermark to only the mentioned sheet of the Excel workbook.

{{< gist GroupDocsGists 9d8b16b89e156aa787fe6c19c4db8ef4 "AddWatermarkToSpecificSheet.cs" >}}

## Watermark Excel Sheets as Background using C# {#watermark-sheet-as-background}

Likewise, we can also add watermarks as the background of the spreadsheet. There will be a little change from the above techniques of applying watermarks. The following are the steps that allow inserting background text watermark to Excel spreadsheet using C#.

*   Prepare the loading options for loading spreadsheet.
*   Load the spreadsheet using [Watermarker][23].
*   Define the watermark text and appearance (rotation, position, dimensions, opacity, color, and more) using [TextWatermark][24].
*   Set the background watermarking options by getting content and setting dimensions.
*   Set the index of worksheet to apply watermark. (Optional)
*   Add the watermark to the spreadsheet using [Add][25] mehtod.
*   Save the spreadsheet with watermark using the [Save][26] method.

The following code sample shows how to add a background watermark to an Excel spreadsheet using C# within the .NET application.

{{< gist GroupDocsGists 9d8b16b89e156aa787fe6c19c4db8ef4 "AddWatermarkToExcelAsBackground.cs" >}}



{{< figure align=center src="images/watermark-excel-sheets-programmatically.png" alt="Watermark Excel Sheets Programmatically">}}


## Get a Free API License

You can [get a free temporary license][27] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we discussed different ways to add watermark to excel sheets using C#. First, we added text watermarks to all the sheets of the Excel workbook. Then we applied the watermark to the specific sheet only. Lastly, we inserted the text-based watermark into the Excel workbook as a background.

Visit the product [documentation][28] to learn more about the API. For queries, contact us via the [forum][29].

## See Also

*   [Watermark Excel Sheets in Java][30]
*   [Watermark PDF Files using C#][31]
*   [Add Watermark to Presentation Slides using C#][32]
*   [Watermark Images using C#][33]







[1]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[2]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[3]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[4]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[5]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[6]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[7]: #watermarking-dotnet-api
[8]: #watermark-all-sheets
[9]: #watermark-any-sheet
[10]: #watermark-sheet-as-background
[11]: https://products.groupdocs.com/watermark/
[12]: https://products.groupdocs.com/watermark/net/
[13]: https://downloads.groupdocs.com/watermark/net
[14]: https://www.nuget.org/packages/GroupDocs.Watermark/
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[19]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[20]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[21]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[22]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[23]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[24]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[25]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[26]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[27]: https://purchase.groupdocs.com/temporary-license
[28]: https://docs.groupdocs.com/watermark
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[31]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[32]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[33]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/

