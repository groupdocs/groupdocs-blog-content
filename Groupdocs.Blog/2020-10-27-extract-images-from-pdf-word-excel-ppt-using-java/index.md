---
seoTitle: "Extract Images from PDF, Word, Excel, PPT using Java"
title: 'Extract Images from Documents using Java'
date: Tue, 27 Oct 2020 05:04:09 +0000
draft: false
url: /2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
author: 'Shoaib Khan'
description: "Extract images from the whole document, and specific pages of word processing documents, Excel spreadsheets, PPT presentations, and PDF using Java."
summary: "Today, we will learn to **programmatically extract images from PDF, Excel, PowerPoint, and Word documents using Java**. For the extraction of images, we will use [GroupDocs.Parser for Java][1]. This Java API supports the parsing of documents and extraction of images, text, and metadata from word-processing documents, spreadsheets, presentations, archives, and email documents. Extracted images can be saved in **BMP**, **GIF**, **JPEG**, **PNG**, and **WebP** formats."
tags: ['extract images from documents in java', 'extract images from PDF in Java', 'extract images from word in java', 'extract images in Java']
categories: ['GroupDocs.Parser Product Family']
---

If you have a document and you want to use the images inside that document in some other documents, here is one of the solutions. In this article, we will be learning to **programmatically extract images from PDF, Excel, PowerPoint, and Word documents using Java**.

*   [Image Extraction Java API][2]
*   [Image Extraction from PDF documents in Java][3]
*   [Extract Images from Word, Excel, PowerPoint documents in Java][4]
*   [Extract Image from Specific Page in Java][5]



{{< figure align=center src="images/extract-images-from-documents-in-java-1.png" alt="Extract Images from Documents in Java">}}


## Image Extraction Java API {#image-extraction-java-api}



{{< figure align=center src="images/groupdocs-parser-java.png" alt="Parse Documents and Extract Data in Java">}}


For the extraction of images, we will use [GroupDocs.Parser for Java][6]. This Java API supports the **parsing of documents** and **extraction of images, text,** and **metadata** from **word-processing documents**, **spreadsheets**, **presentations, archives,** and **email** documents. The following are the document formats supported by the Java API for image extraction.

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Word Processing Documents</strong></td><td>DOC, DOCX, DOCM, DOT, DOTX, DOTM, ODT, OTT, RTF</td></tr><tr><td><strong>Spreadsheets</strong></td><td>XLS, XLSX, XLSM, XLSB, XLT, XLTX, XLTM, ODS, OTS, XLA, XLAM, NUMBERS</td></tr><tr><td><strong>Presentations</strong></td><td>PPT, PPTX, PPTM, PPS, PPSX, PPSM, POT, POTX, POTM, ODP, OTP</td></tr><tr><td><strong>Portable Documents</strong></td><td>PDF</td></tr><tr><td><strong>Emails</strong></td><td>EML, EMLX, MSG</td></tr><tr><td><strong>Archives**</td><td>ZIP</td></tr></tbody></table></figure>

Before you start with the examples below, I would recommend to set up the environment by downloading the latest version of document parsing Java API from the [downloads section][7] or you may set the following configurations in your **maven-based** java applications:

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>20.8</version> 
</dependency>
```

## Extract Images from PDF Documents in Java {#extract-images-from-pdf-in-java}



{{< figure align=center src="images/PDF-with-Images.png" alt="PDF Document to Extract Images">}}


Follow these simple steps to get all images from the PDF document.

1.  Instantiate [**Parser**][8] class object.
2.  Call **[getImages][9]** method of Parser class to get all the images.
3.  Iterate over images using **[PageImageArea][10]**.
4.  Save images using the save method of PageImageArea.

It's done. See the full code below. Extracted images can be saved in **BMP**, **GIF**, **JPEG**, **PNG**, and **WebP** formats.

{{< gist GroupDocsGists 3bc831b64a139c428dffdb138332128a "ExtractImagesFromDocument.java" >}}

These are the images retrieved from the PDF document using the above code.



{{< figure align=center src="images/Extracted-Images-from-PDF-using-GroupDocs.Parser-for-Java.png" alt="Extracted Images from Document using Java">}}


## Extract Images from Word, Excel, PowerPoint Files in Java {#extract-images-from-word-excel-ppt-in-java}

Similarly, all the images can be taken out from the word-processing files, spreadsheets, presentations, with the unchanged code base. What you have to change? Just the source document path and the right file extension.

```
Parser parser = new Parser("path/document.docx") // Word Document
// Parser parser = new Parser("path/document.xlsx") // Excel Spreadsheet
// Parser parser = new Parser("path/document.pptx") // PowerPoint Presentation
// Parser parser = new Parser("path/document.pdf") // PDF Document

```

## Image Extraction from Specific Document Page in Java {#extract-images-from-specific-page-in-java}

If you do not want to extract all the images from the whole document but from some specific page. Below code demonstrates how we can extract images from a particular page of the document in Java.

{{< gist GroupDocsGists 3bc831b64a139c428dffdb138332128a "ExtractImagesFromDocumentPage.java" >}}

## Conclusion

Today, we learned **how to extract images from the whole document, and the specific page of word-processing documents, spreadsheets, presentations, and PDF in Java**. There is no difference in the code if we have to extract images from the files of different file formats. We just have to pass the right path and name. That's it.

## See Also

*   [Extract Images from Documents in C#][11]
*   [Extract Images from Documents on the Cloud using Python][12]







[1]: https://products.groupdocs.com/parser/java
[2]: #image-extraction-java-api
[3]: #extract-images-from-pdf-in-java
[4]: #extract-images-from-word-excel-ppt-in-java
[5]: #extract-images-from-specific-page-in-java
[6]: https://products.groupdocs.com/parser/java
[7]: https://downloads.groupdocs.com/parser/java
[8]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser
[9]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser#getImages()
[10]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser.data/PageImageArea
[11]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[12]: https://blog.groupdocs.cloud/2020/10/25/extract-images-from-word-excel-ppt-pdf-using-python/

