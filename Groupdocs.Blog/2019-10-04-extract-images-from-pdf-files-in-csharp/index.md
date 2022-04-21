---
title: 'Extract Images from PDF Documents using C#'
date: Fri, 04 Oct 2019 07:09:26 +0000
draft: false
url: /2019/10/04/extract-images-from-pdf-files-in-csharp/
aliases:
    - /2019/10/04/extract-images-from-pdf-documents-using-c/
author: 'Usman Aziz'
summary: ''
tags: ['extract images', 'extract images from PDF', 'extract images from PDF in csharp', 'extract images in csharp', 'parse PDF and extract images']
categories: ['GroupDocs.Parser Product Family']
---

**Portable Document Format** (PDF) is a popular and widely used document format developed by Adobe. The PDF documents can contain a variety of content including formatted text, images, annotations, form fields, etc. Parsing PDF document programmatically is a popular use case and there are multiple ways of extracting the text. However, extracting images from a PDF document is a complex task. This article demonstrates how easily you can **extract images** from the **PDF** documents **programmatically** in **C#** using [GroupDocs.Parser for .NET](https://products.groupdocs.com/parser) API. So let's begin.

## Steps to extract images from a PDF document

**1.** Create a new project.

**2\.** Download [GroupDocs.Parser for .NET](https://downloads.groupdocs.com/parser/net) or install it using [NuGet](https://www.nuget.org/packages/GroupDocs.Parser).

**3.** Add the following namespaces.

{{< gist GroupDocsGists 29261ce2d647088e60fc3c35eadf1087 "namespaces.cs" >}}

**4.** Load the PDF document.

{{< gist GroupDocsGists 29261ce2d647088e60fc3c35eadf1087 "LoadDocument.cs" >}}

**5.** Extract images from the document.

{{< gist GroupDocsGists 29261ce2d647088e60fc3c35eadf1087 "ExtractImagesFromPDF.cs" >}}

**6.** Access each image from the collection and save it.

{{< gist GroupDocsGists 29261ce2d647088e60fc3c35eadf1087 "SaveImages.cs" >}}

## Complete Code

{{< gist GroupDocsGists 29261ce2d647088e60fc3c35eadf1087 "ExtractImagesFromPDFCode.cs" >}}

## Results

**PDF Document**



{{< figure align=center src="images/PDF.png" alt="PDF document to extract images.">}}


**Extracted Images**



{{< figure align=center src="images/images.png" alt="extracted images from the PDF.">}}


For a complete list of features provided by GroupDocs.Parser for .NET API, visit the [documentation](https://docs.groupdocs.com/display/parsernet/Features+Overview). Cheers!




