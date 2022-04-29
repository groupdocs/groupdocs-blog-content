---
title: 'Remove Watermarks from PDF Documents in C#'
seoTitle: "Remove Watermark from PDF Documents using C# | .NET Watermark API"
description: "Delete or remove watermarks from PDF and other documents using C#. An overview of .NET API for C# developers to create a watermark remover application."

date: Fri, 25 Mar 2022 19:29:00 +0000
draft: false
url: /2022/03/25/remove-watermark-from-pdf-in-csharp/
aliases:
    - /2019/11/06/remove-watermark-from-pdf/
author: 'Shoaib Khan'
summary: 'Watermarks are normally used to avoid any illegal use of confidential documents. When confidentiality is no more needed, you better remove the watermarks from such documents. There can be text and image-based watermarks in a document. Today, we will have a look at **how to remove watermarks from PDF documents using C#**.'
tags: ['delete watermark', 'how to remove watermark in c sharp', 'remove watermark', 'remove watermark from pdf', 'remove watermark using csharp', 'Watermark Remover', 'watermark remover application']
categories: ['GroupDocs.Watermark Product Family']
---

Watermarks are normally used to avoid any illegal use of confidential documents. When confidentiality is no more needed, you better remove the watermarks from such documents. There can be text and image-based watermarks in a document. Today, we will have a look at **how to remove watermarks from PDF documents using C#**.



{{< figure align=center src="images/removing-watermark-from-pdf.jpg" alt="Remove Watermark from PDF documents">}}


## .NET API to Remove PDF Watermarks

[GroupDocs.Watermark](https://products.groupdocs.com/watermark) showcases .NET API to deal with watermarks within documents and images of different [file formats](https://docs.groupdocs.com/conversion/net/supported-document-formats/). If you are making a _watermark removal app_, It provides you some useful ways to:

*   Remove all watermarks from PDF
*   Delete watermarks with particular text formatting
*   Remove hyperlink watermarks

Let's learn how a C# developer can remove watermarks from PDF using [GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net/) API in different ways.

## Remove All Watermarks from PDF document using C# {#RemovingFoundWatermarks-RemoveWatermark}

The API gives you the power to easily find and then remove a particular watermark and all the watermarks from a document. The following code removes all the watermarks from a PDF document using C#.

*   Load the PDF file using [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker).
*   Fetch all the [possible watermarks](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) as a collection using search.
*   Traverse the whole collection and remove every watermark or the one that meets your criterion.
*   Save the updated PDF with no more watermarks on it.

The following C# code removes all the watermarks from a PDF document.

{{< gist GroupDocsGists 4fa618502d15fc884614db7d7601ec53 "RemoveAllWatermark.cs" >}}

## Remove Watermark from PDF with particular Text Formatting using C# {#RemovingFoundWatermarks-RemoveWatermarkwithParticularTextFormatting}

Using API you can search and remove the watermarks on the basis of text formatting. You can provide a search criterion containing name, font, size, color, etc and the API will find the watermarks with matching properties. The following code snippet demonstrates how to search and remove watermarks from a PDF file with a specific text formatting using C#.

*   Load the PDF file using [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker).
*   Define the search criterion using [TextFormattingSearchCriteria](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search.searchcriteria/textformattingsearchcriteria).
*   Mention all the required formatting properties.
*   Perform **Search()** and get all the [possible watermarks](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) as a collection by providing the defined criteria.
*   Remove all the searched watermarks using the **Clear()** method.
*   Save the updated PDF having no watermark with the defined properties.

The following C# code removes the watermarks in a PDF document having the specified text formatting.

{{< gist GroupDocsGists 4fa618502d15fc884614db7d7601ec53 "RemoveWatermarkWithFormatting.cs" >}}

## Hyperlink Watermark Remover in .NET

The document watermarking .NET API allows you to search and remove hyperlinks in a document of any supported document format. The following steps allow removing hyperlink watermarks from a PDF document within the .NET application using C#.

*   Load the PDF file using [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker).
*   Fetch all the [possible watermarks](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) as a collection using search.
*   Traverse the whole collection and remove every watermark or the one that meets your criterion.
*   Save the updated PDF with no more watermarks on it.

The following C# code sample shows how to find and remove hyperlink watermarks with a particular URL from a PDF document.

{{< gist GroupDocsGists 4fa618502d15fc884614db7d7601ec53 "RemoveHyperlinkWatermarks.cs" >}}

## Conclusion

To conclude, today we learned to remove different watermarks from the PDF documents using C#. I believe that you will now be more confident to build your own .NET application for finding and removing text watermarks as well as image watermarks from PDF documents. Additionally, you can add features of removing watermarks with specified formatting and hyperlink watermarks.

Besides, you can learn more about [GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net/) from its [documentation](https://docs.groupdocs.com/watermark/). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Watermark Password Protected Documents using C#](https://blog.groupdocs.com/2021/12/25/watermark-password-protected-documents-using-csharp/)
*   [Watermark PDF Files using C#](https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/)
*   [Add Watermark to Images using C#](https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/)
*   [Find and Remove Watermarks from Documents in Java](https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/)




