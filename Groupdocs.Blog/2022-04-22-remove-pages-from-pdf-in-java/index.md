---
title: "Remove Pages from PDF in Java"
seoTitle: "Remove Pages from PDF in Java | Even, Odd, List & Range"
description: "Remove any set of pages from the PDF files in Java. Delete list of pages, any given range, even or odd pages from PDF files within applications."
date: Fri, 22 Apr 2022 11:00:00 +0000
draft: false
url: /2022/04/22/remove-pages-from-pdf-in-java/
author: 'Shoaib Khan'
summary: 'When an old document is updated; the outdated, obsolete, or even highly confidential pages are required to be removed from the latest version of the document. In this article, we will learn **how to programmatically remove such pages from the PDF documents in Java**. Further, we will discuss different ways to remove list of pages, pages range, even and odd pages of PDF document.'
tags: ['delete pages', 'delete pages in java', 'remove pages', 'remove pages in java', 'delete pages from pdf in java']
categories: ['GroupDocs.Merger Product Family']
---

When an old document is updated; the outdated, obsolete, or even highly confidential pages are required to be removed from the latest version of the document. In this article, we will learn **how to programmatically remove such pages from the PDF documents in Java**. Further, we will discuss different ways to remove list of pages, pages range, even and odd pages of PDF document.

The following topics are discussed below:

- [PDF Page Removal Java API](#pdf-page-removal-java-api)
- [Remove List of Pages](#remove-pdf-pages-list-in-java)
- [Delete Pages Range](#remove-pdf-pages-range-in-java)
- [Remove Odd or Even Pages in Range](#remove-even-odd-pdf-pages-in-java)

## Java API to Remove Pages from PDF {#pdf-page-removal-java-api}

GroupDocs.Merger privides the Java API that allows programmatically removing of pages from the PDF document. Furthermore, it allow changing pages orientation, moving pages location, splitting of documents, extraction, and rotation of document pages. I will use this [GroupDocs.Merger for Java][1] to delete various pages of PDF files in Java. For the details and other features of the API, you can visit its [documentation][2].

### Download and Configure

Get the library from the [downloads section][3]. For your Maven-based Java application, just add the following pom.xml configuration. After this, you can try the examples of this article as well the many more example available on [GitHub][4]. For the details, you may visit the [API Reference][5].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>

<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>22.2</version> 
</dependency>
```

## Remove Selected Pages from PDF in Java {#remove-pdf-pages-list-in-java}

To remove any set of pages, you only need to provide the list of pages numbers from the loaded PDF document. The below steps allow removing the provided list of selective pages from a PDF document in Java.

- Initialize [RemoveOptions][6] class with the **page numbers** to remove.
- Instantiate [Merger][7] object with source document path or stream.
- Call removePages() method to delete the listed pages.
- Call the appropriate save() method to save the resultant document.

The following Java code example removes the selected 2nd and 4th page from the PDF document.

{{< gist GroupDocsGists 272531e62ef852e8984bf6fde2763c51 "RemoveListedPdfPages.java" >}}

## Remove Pages Range from PDF in Java {#remove-pdf-pages-range-in-java}

Similarly, you can remove any range of pages within your PDF document. The following steps allow removing any range of pages from the PDF files in Java.

- Initialize [RemoveOptions][6].
- Provide the **page range** by setting **starting** and **ending** page number.
- Instantiate [Merger][7] object with source document path or stream.
- Call removePages() method with the range.
- Call the appropriate save() method to save the resultant document.

The following Java sample code removes all the pages from the PDF document within the provided range i.e. 3 to 5.

{{< gist GroupDocsGists 272531e62ef852e8984bf6fde2763c51 "RemovePdfPagesRange.java" >}}

## Remove Even or Odd Pages from PDF in Java {#remove-even-odd-pdf-pages-in-java}

You can also remove any even/odd pages of the document. The following steps show how to remove even or odd pages of the PDF file within the given range in Java.

- Initialize [RemoveOptions][6] class with the page range.
- Set the mode to **even** or **odd**.
- Instantiate [Merger][7] object with source document path or stream.
- Call removePages() method with the removal options.
- Call the appropriate save() method to save the resultant document.

The following Java code snippet removes all the odd pages from the whole PDF document.

{{< gist GroupDocsGists 272531e62ef852e8984bf6fde2763c51 "RemovePdfOddPages.java" >}}

The following Java code sample removes all the even pages from the PDF document within the provided range i.e. 1-5.

{{< gist GroupDocsGists 272531e62ef852e8984bf6fde2763c51 "RemovePdfEvenPages.java" >}}

## Get a Free API License

You can [get a free temporary license][8] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to delete different set of pages from PDF documents within Java applications. Specifically, we have seen how to delete pages by providing page numbers and page ranges. Additionally, we saw how to remove odd or even pages from any PDF document in Java. You can try building your own application to eliminate any set of pages from your PDF files.

For more details about the API, visit the documentation. For queries, contact us via the [forum][14].

## See Also
- [Watermark PDF Files in Java][9]
- [Rearrange PDF Pages in Java][10]
- [Word Search and Replace Text in PDF in Java][11]
- [Convert PDF to Grayscale in Java][12]
- [Password Protection of PDF Files in Java][13]

[1]: https://products.groupdocs.com/merger/java
[2]: https://docs.groupdocs.com/merger/java/
[3]: https://downloads.groupdocs.com/merger/java
[4]: https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java
[5]: https://apireference.groupdocs.com/merger/java
[6]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/RemoveOptions
[7]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[8]: https://purchase.groupdocs.com/temporary-license
[9]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[10]: https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/
[11]: https://blog.groupdocs.com/2022/03/08/find-and-replace-text-in-pdf-in-java/
[12]: https://blog.groupdocs.com/2022/03/02/convert-pdf-to-grayscale-jpg-png-images-in-java/
[13]: https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/
[14]: https://forum.groupdocs.com/