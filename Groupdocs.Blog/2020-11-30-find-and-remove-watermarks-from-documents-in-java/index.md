---
seoTitle: "Find and Remove Watermarks from Documents in Java"
title: 'Find and Remove Watermarks from Documents in Java'
date: Mon, 30 Nov 2020 10:55:51 +0000
draft: false
url: /2020/11/30/find-and-remove-watermarks-from-documents-in-java/
aliases:
    - /2019/10/10/find-and-remove-watermarks-from-documents-in-java/
author: 'Shoaib Khan'
description: "Java API to find and remove text and image watermarks from documents like PDF, Word, Excel, PowerPoint, and Visio files programmatically."
summary: 'This article is useful for **Java** developers who are looking for a way to **find and remove text** or **image watermarks** from **PDF, Word, Excel, PowerPoint,** and **Visio** documents. In one of our posts we have learnt [finding and removing watermarks from documents in C#][1]. Let us now jump to quickly see a little about a Java API that allows adding, finding and removing watermarks from various documents in different ways.'
tags: ['find and remove watermarks in Java', 'find watermarks in Java', 'remove watermarks using Java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---

This article is useful for **Java** developers who are looking for a way to **find and remove text** or **image watermarks** from **PDF, Word, Excel, PowerPoint,** and **Visio** documents. In one of our posts we have learnt [finding and removing watermarks from documents in C#][2]. Let's now jump to quickly see a little about a Java API that allows adding, finding and removing watermarks from various documents in different ways.

## Java API for Watermarking and Removal

**[GroupDocs.Watermark for Java][3]** API supports adding text and image watermarks to a wide range of document formats. In addition, it also has the ability to find and remove watermarks from the documents. The API also finds the watermark objects that are added using the third-party tools. So let me demonstrate how you can remove the watermark from a document in a few steps in Java.

You may get the JAR from [downloads][4] section, or add the following configuration in pom.xml of your Maven-based Java application. For API details, visit [API Reference][5].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>20.5</version> 
</dependency>
```

## Steps to Remove Watermarks from a Document in Java

Before we begin, have a look at the following PDF document which contains a text watermark as well as an image watermark. We'll use this document and remove the watermarks from it.



{{< figure align=center src="images/watermarkedpdf.png" alt="PDF file with watermarks - GroupDocs">}}


**1.** Create a new project.

**2.** Add the following imports.

{{< gist GroupDocsGists fab72765f204598394779233a3a96e66 "Imports.java" >}}

**3\.** Create an instance of **Watermarker**  class and load the source document.

{{< gist GroupDocsGists fab72765f204598394779233a3a96e66 "LoadDocument.java" >}}

**4.** Find the watermarks based on the configured search criteria using **search** method.

{{< gist GroupDocsGists fab72765f204598394779233a3a96e66 "FindWatermarks.java" >}}

**5.** Iterate over the watermarks collection and remove watermarks using **removeAt** method.

{{< gist GroupDocsGists fab72765f204598394779233a3a96e66 "RemoveWatermark.java" >}}

**6\.** Save the resultant document using **save** method.

{{< gist GroupDocsGists fab72765f204598394779233a3a96e66 "SaveDocument.java" >}}

There are also some **other ways of finding and removing watermarks** from documents using different methods. If you want to remove all the watermarks of a document, or want to get rid of some selective watermarks of various kind:

*   You can collect all the possible watermarks.
*   Iterate over the watermark collection or directly access the watermark with index.
*   Check for watermark type and data, if required.
*   Remove it, if it meets your requirement.

**remove**, **removeAt**, and **clear** are the methods that can be used accordingly for removing watermarks. For more details, you can visit **documentation** article about [searching and modifying watermarks in Java][6].

### Complete Code

{{< gist GroupDocsGists fab72765f204598394779233a3a96e66 "RemoveWatermarkFromDocuments.java" >}}

### Results

The following is the screenshot of the resultant PDF document that we get after removing the watermarks.



{{< figure align=center src="images/withoutwatermarkpdf.png" alt="Resultant PDF file after removal of watermarks using Watermarking Java API by GroupDocs">}}


## Conclusion

I believe, as a Java developer, you will not be hesitant any more to find and then remove any kind of watermarks from Microsoft and OpenOffice supported **word-processing documents**, **spreadsheets**, **presentations**, **PDF** documents, and **Visio** drawings.

You may explore more about the API from the [documentation][7]. In case of any queries, reach us @ [forum][8].

## See Also

*   [Add watermarks to images in Java][9]
*   [Find and remove watermarks from documents in C#][10]
*   [Add watermarks to images or images in documents using C#][11]







[1]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[2]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[3]: https://products.groupdocs.com/watermark/java
[4]: https://downloads.groupdocs.com/watermark/java
[5]: https://apireference.groupdocs.com/watermark/java
[6]: https://docs.groupdocs.com/watermark/java/searching-and-modifying-watermarks/
[7]: https://docs.groupdocs.com/watermark/java/
[8]: https://forum.groupdocs.com/c/watermark
[9]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[10]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[11]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/

