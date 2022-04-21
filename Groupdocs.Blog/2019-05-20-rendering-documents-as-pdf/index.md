---
title: 'Rendering Documents as PDF'
date: Mon, 20 May 2019 08:22:21 +0000
draft: false
url: /2019/05/20/rendering-documents-as-pdf/
author: 'Muhammad Umar'
summary: ''
tags: []
categories: ['GroupDocs.Viewer Product Family']
---

The Portable Document Format (PDF) is a file format to present documents, including text formatting and images, in a manner independent of the application software, hardware, and operating systems. Based on the PostScript language, each PDF file encapsulates a complete description of a fixed-layout flat document, including the text, fonts, vector graphics, raster images and other information needed to display it.

This post demonstrates the usage of the GroupDocs.Viewer APIs (GroupDocs.Viewer for .NET and GroupDocs.Viewer for Java) to render the [supported file formats](https://docs.groupdocs.com/display/viewernet/Supported+Document+Formats) as PDF documents.

## How to Render Using GroupDocs.Viewer

Both the viewer handlers (**ViewerHtmlHandler**,**ViewerImageHandler**) provide an overloaded method **GetPdfFile()** which accepts the document name as parameter and returns **FileContainer**. The File stream can be fetched from the **Stream** property of the **FileContainer** in order to save the resultant document on the disk.

The following code snippet shows the way to render a word document as PDF:

{{< gist GroupDocsGists f95e18499b9c834a184841200633b8b7 "RenderAsPdf.cs" >}}

Java lovers can write the code like following:

{{< gist GroupDocsGists 20eebc512cab967a8bae7fb909fa04b4 "renderdocaspdf.java" >}}

## Add Print Action while Rendering as PDF

A Print Action is an option to appear the print popup when open the PDF document in Adobe reader. The popup will appear like below screenshot:



{{< figure align=center src="images/Reader.png" alt="">}}


The below given steps can be followed, in order to add print action in the resultant PDF document.

*   Create/initialize **PdfFileOptions** object
*   Set **Transformations** property of **PdfFileOptions** to **Transformation.AddPrintAction**
*   Call **htmlHandler.GetPdfFile** method

The .NET code snippet will look like:

{{< gist GroupDocsGists 08d76444ef53e5e946845e8e85c18a12 "RenderDocumentAsPDFWithPrintAction.cs" >}}

The Java code can be written as:

{{< gist GroupDocsGists 9789ce7039096afd57b9b0e49408f4e3 "getOriginalFileAsPdfWithPrintAction.java" >}}

The complete ready to run code sample is available on [GitHub](https://github.com/groupdocs-viewer/).

*   The .NET guys can visit [here](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET/)
*   The code sample for Java lovers is available [here](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java/)




