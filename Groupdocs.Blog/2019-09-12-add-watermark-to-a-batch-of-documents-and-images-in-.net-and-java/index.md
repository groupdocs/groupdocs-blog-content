---
title: 'Add Watermark to a Batch of Documents and Images in .NET and Java'
date: Thu, 12 Sep 2019 17:41:53 +0000
draft: false
url: /2019/09/12/add-watermark-to-a-batch-of-documents-and-images-in-.net-and-java/
author: 'Usman Aziz'
summary: ''
tags: ['add watermark to images in csharp', 'add watermark to images in java', 'watermark using csharp', 'watermark using java', 'Watermarking API']
categories: ['GroupDocs.Watermark Product Family']
---

Watermarking is a popular technique to indicate that the content or data inside a document is copyrighted. On the other hand, it is also used to place the company's logo or some kind of label in the documents before they are shared within or outside the company. However, it is quite hard to apply the watermark to a bunch of documents one by one. It becomes harder if you have documents of various formats such as PDF, DOCX, PPTX, XLSX, EML, JPG, PNG, etc. So in order to make this process easier, we need some automation.

In this article, I will show you how you can apply a watermark to a batch of documents and images in one go using [GroupDocs.Watermark](https://products.groupdocs.com/watermark) API. So you don't need to add watermark to each document manually. Also, you don't need to worry about if you have or not the software or application that supports adding watermark to the document of a particular format.

Before we proceed, let me tell you the reasons why GroupDocs.Watermark is a suitable API for watermarking. This is because it supports:

*   a wide range of [file formats](https://docs.groupdocs.com/watermark/net),
*   adding text/image watermark,
*   adding watermark to images inside a document,
*   adding watermark to all or selected pages of the document,
*   customizing the size, position, and appearance of the watermark, and
*   much [more](https://docs.groupdocs.com/display/watermarknet/Features+Overview).

## How to Add Watermark to Images and Documents?

Now, let's have a look at how to add watermark to the documents as well as images of various formats at once. For this, we'll follow the below steps:

*   Place the documents in a folder.
*   Load each document from the folder using GroupDocs.Watermark.
*   Create and initialize the watermark.
*   Set watermark properties such as position, size, opacity, font, etc.
*   Add watermark to the document.
*   Save the document to the destination folder.

This is how we would transform these steps into the code.

## C# Example - Add Watermark to Multiple Documents

Example adds the watermark to all the documents present in the provided folder.

{{< gist GroupDocsGists c1c79fe703c632a8082961d28360c6d1 "BatchWatermark.cs" >}}

## Java Example - Add Watermark to Multiple Documents

{{< gist GroupDocsGists c1c79fe703c632a8082961d28360c6d1 "BatchWatermark.java" >}}

And that's it! The following is the screenshot of a PDF document that we have before and after applying the watermark using the above-mentioned code.



{{< figure align=center src="images/Original-2.png" alt="watermark added to PDF document in Java.">}}


Download the complete ready-to-run source code from [GitHub](https://github.com/usmanazizgroupdocs/batch_watermark). Contact us on our [forum](https://forum.groupdocs.com/categories) for any questions or queries.

Cheers!




