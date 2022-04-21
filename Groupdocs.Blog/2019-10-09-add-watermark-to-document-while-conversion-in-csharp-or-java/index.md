---
title: 'Add Watermark to Documents while Conversion in C# or Java'
date: Wed, 09 Oct 2019 13:01:05 +0000
draft: false
url: /2019/10/09/add-watermark-to-document-while-conversion-in-csharp-or-java/
aliases:
    - /2019/10/09/add-watermark-to-the-converted-document-in-c-or-java/
    - /2019/10/09/add-watermark-to-document-while-conversion-in-c-sharp-or-java/
author: 'Atir Tahir'
summary: ''
tags: ['add watermark in csharp', 'add watermark in java', 'convert and watermark', 'watermark in csharp and java']
categories: ['GroupDocs.Conversion Product Family']
---

Document conversion is one of the most frequent processes that endures across a lot of industries. Sometimes, it is the business need to put a watermark on the resultant document after conversion. For example, you want to convert a Word document to PDF or PowerPoint PPT/PPTX to PDF with a watermark (text or image) in all the PDF pages.

[GroupDocs.Conversion](https://products.groupdocs.com/conversion) for [.NET](https://products.groupdocs.com/conversion/net) and [Java](https://products.groupdocs.com/conversion/java) gives you such an option. It possesses a class _WatermarkOptions_ with rich properties such as:

*   Text/Font
*   Color
*   Width
*   Height
*   Background
*   Transparency
*   Rotation angle

## Convert Word to PDF and Add Watermark - C# Example

Let's have a look at the C# implementation of how to convert a word DOCX document to PDF and add a watermark to the resultant PDF document.  
{{< gist GroupDocsGists 329a1a434791a202bd325f5440dad206 "convertandaddwatermark.cs" >}}

## Convert PPTX to PDF and Add Watermark - Java Example

Below is the Java code example shows how to convert a PowerPoint PPTX presentation to PDF and add a watermark to the resultant PDF document.  
{{< gist GroupDocsGists ed031f8a9feec37aaddf5da82085555f "convertandaddwatermark.java" >}}

Below is the screenshot, you can see the conversion of a PPTX to PDF along with watermark text.



{{< figure align=center src="images/watermark-1024x330.jpg" alt="Watermark on Image while conversion using GroupDocs.">}}


*   Download API from [here](https://downloads.groupdocs.com/conversion/).
*   If there's an issue, you can post on the [forum](https://forum.groupdocs.com/c/conversion).
*   [Documentation](https://docs.groupdocs.com/display/conversionproductfamily/Home) is always there for your help.




