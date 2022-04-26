---
title: 'Extract Images from EPUB, FB2, CHM eBooks in Java'
date: Mon, 15 Mar 2021 15:01:00 +0000
draft: false
url: /2021/03/15/extract-images-from-ebooks-in-java/
author: 'Shoaib Khan'
summary: "**eBooks** of various formats are very common in everyday use. The eBook can contain text as well as images. If you want to use the images of any eBook elsewhere, you can get these easily extracted programmatically within your Java application. In this article, you will learn to automate, **how to extract images from eBook** files such as **EPUB, PDF, FB2, CHM** in **Java**."
tags: ['Extract Images from CHM in Java', 'Extract Images from eBooks in Java', 'Extract Images from FB2 in Java', 'extract images in Java', 'Parse eBooks in Java', 'Parse eBooks to Extract Images in Java']
categories: ['GroupDocs.Parser Product Family']
---

**eBooks** of various formats are very common in everyday use. The eBook can contain text as well as images. If you want to use the images of any eBook elsewhere, you can get these easily extracted programmatically within your Java application. In this article, you will learn to automate, **how to extract images from eBook** files such as **EPUB, PDF, FB2, CHM** in **Java**.

The following topics will be covered below:

*   [Java API - Image Extraction from eBooks][2]
*   [Extract Images from EPUB eBook in Java][3]
*   [Extract Images from PDF, FB2, CHM eBooks in Java][4]

## Java API to Extract Images from eBooks {#image-extraction-java-api-for-ebooks}

[GroupDocs.Parser for Java][5] API is a feature-rich automation API for extracting images from eBooks and documents in Java. In addition to this, the API supports parsing, and extraction of images, text, and metadata from word-processing documents, spreadsheets, PDF, presentations, emails, ZIP archives, and many other [supported document formats][6].

### Download and Configure

Get the JAR file from the [downloads][7] section, or just add the following pom.xml configuration in your Maven-based Java applications to try the below-mentioned examples. For the details, you may visit the [API Reference][8].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>21.2</version> 
</dependency>
```

## Extract Images from EPUB eBook in Java {#extract-images-from-epub-in-java}

Let's start with the EPUB eBook to parse it for images. The following steps parse the EPUB eBook and extract all the images from it using Java code.

*   Create [Parser][9] class object with the eBook.
*   Use [getImages][10] method to extract all the images of the EPUB eBook.
*   Traverse the extracted images and save them to disk.



{{< figure align=center src="images/alice.png" alt="EPUB eBook with images" caption="EPUB eBook from the Adobe [Sample eBook Library][11]">}}


The following Java code parses the EPUB eBook and saves the images of the eBook one by one to the disk.

{{< gist GroupDocsGists 15bdf5cfa2bf46ef77b659e8cf20dc7e "ExtractImagesFromEBooks.java" >}}



{{< figure align=center src="images/alice-image-from-epub.jpg" alt="Extracted Image from EPUB eBook">}}


As a result, all the images will be saved to the provided location. Here is one of the images shown as a sample.

The images can be saved in any of the following image file formats:

*   JPG
*   PNG
*   WEBP
*   GIF
*   BMP

## Extract Images from PDF, FB2, CHM eBooks in Java {#extract-images-from-pdf-fb2-chm-in-java}

In addition to the EPUB format, if you have your eBook in PDF, FB2, CHM, or with some other format, you can extract their images in the same way. Just pass your eBook to the **Parser** constructor while creating the object. After that, the **getImages** method will be extracting images from your provided eBooks using the same Java code.

```
// Provide different eBook formats to the Parser constructor to extract the images.
// Parser parser = new Parser("ebook.epub");
Parser parser = new Parser("ebook.pdf");
// Parser parser = new Parser("ebook.fb2");
// Parser parser = new Parser("ebook.chm");

Iterable<PageImageArea> images = parser.getImages();
```

## Conclusion

In this article, you learned to programmatically get all the images from PDF, EPUB, FB2, CHM eBooks within your Java applications. Now you can try to build your own image extractor Java application using [GroupDocs.Parser for Java][12] API.

For more about the API, you may visit [documentation][13] or open-source examples at [GitHub][14]. For any further issues, you can contact the quick support at the [forum][15].

## See Also

*   [Extract Images from EPUB, FB2, CHM eBooks in C#][16]
*   [Extract Data from Invoices and Receipts in Java][17]







[1]: https://blog.groupdocs.com/2021/03/15/extract-images-from-ebooks-in-java/
[2]: #image-extraction-java-api-for-ebooks
[3]: #extract-images-from-epub-in-java
[4]: #extract-images-from-pdf-fb2-chm-in-java
[5]: https://products.groupdocs.com/parser/java
[6]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/parser/java
[8]: https://apireference.groupdocs.com/parser/java
[9]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[10]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages()
[11]: https://www.adobe.com/solutions/ebook/digital-editions/sample-ebook-library.html
[12]: https://products.groupdocs.com/parser/net
[13]: https://docs.groupdocs.com/parser/java
[14]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java
[15]: https://forum.groupdocs.com/c/parser/
[16]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[17]: https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/

