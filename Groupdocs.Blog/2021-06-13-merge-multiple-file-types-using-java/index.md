---
title: 'Merge Multiple File Types into One using Java'
date: Sun, 13 Jun 2021 05:49:00 +0000
draft: false
url: /2021/06/13/merge-multiple-file-types-using-java/
author: 'Shoaib Khan'
summary: "Merging different documents is often required when you intend to gather the scattered data of different documents into one single file. In this article, you will learn to automate the documents merging process. This will show how to programmatically merge multiple documents of either the same or different file types into one file using Java. In another post, we discussed [merging multiple files of different formats using C#][1]."
tags: ['Merge Documents in Java', 'Merge Files in Java', 'Merge multiple file types in Java', 'Merge two or more file in Java']
categories: ['GroupDocs.Merger Product Family']
---

Merging different documents is often required when you intend to gather the scattered data of different documents into one single file. In this article, you will learn to automate the documents merging process. This will show how to programmatically merge multiple documents of either the same or different file types into one file using Java. In another post, we discussed [merging multiple files of different formats using C#][2].



{{< figure align=center src="images/merged-pdf-word-excel-files-to-pdf-in-java.jpg" alt="Merged PDF Word Excel Presentations to One PDF in Java">}}


The following topics are covered below:

*   [Java API - Merge Multiple Files][3]
*   [Merge PDF, Word, Excel files into one PDF][4]
*   [Merge Selective Pages of Multiple files into One File][5]

## Java API for Merging Multiple Document Types {#java-api-to-merge-multiple-file-types}

I will be using [GroupDocs.Merger for Java][6] to combine documents of different file formats into one file. The Java API allows joining various documents of the same or different formats into one file. Furthermore, it allows documents to split, trim, swap, move, remove, rotate, or arrange pages accordingly. Additionally, it supports passwords and their removal to manage the security of the [supported document formats][7].

Some of the document types the API supports include; word-processing documents, spreadsheets, presentations, HTML, PDF, eBooks, Visio drawings, CSV, and TSV.

### Download and Configure

Get the document merger library from the downloads section. For Maven-based Java applications, add the following configuration within pom.xml. Afterward, you can try document merging java examples of this article as well as many more from [GitHub][8]. For the details, you may also visit the [API Reference][9].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.3</version> 
</dependency>
```

## Merge PDF, Word, Excel files into one PDF in Java {#merge-multiple-files-into-one-pdf-in-java}

PDF documents can be combined with your Word documents, Excel spreadsheets, PowerPoint presentations, and other PDF documents with just a few lines of code. The following are the steps of how to merge documents of multiple file types into one file.

*   Load the initial document using the [Merger][10] class.
*   Combine the second document using the [join][11] method.
*   Keep merging the other documents (if required) using the same or similar **join** method.
*   Save the final combined document on path or stream using the relevant [save][12] method.

The following source code shows how to merge PDF, Word, and Excel documents into one PDF file in Java.

{{< gist GroupDocsGists bcf021b81840177ce42499faf038e441 "MergeDifferentFiles.java" >}}

Similarly, documents with the same file types can be combined. The below-mentioned is the output obtained by joining a word document, a PDF document. and a spreadsheet using the above-mentioned Java code.



{{< figure align=center src="images/merged-pdf-word-excel-to-one-file.jpg" alt="Merge different file types into one PDF C#">}}


## Merge Selective Pages of Multiple PDF, Word, Excel files into One PDF in Java {#merge-selective-pages-of-multiple-files-into-one-pdf-in-java}



{{< figure align=center src="images/merged-selective-pages-of-pdf-word-excel-to-one-file.jpg" alt="Merge selective page of different file types into one PDF C#">}}


If you want to pick few pages from one document and some other selective pages from the next document, and so on. The API allows you to merge selective pages of multiple file types into one file in different ways.

*   Load the initial document using the [Merger][13] class.
*   Prepare the merging options with [JoinOptions][14] class.
*   Start merging the document using the [join][15] method.
*   Keep joining the documents by setting appropriate joining options for each document.
*   Save the final merged document using the [save][16] method.

The following source code shows how to merge the first page of a Word document and the even sheets of Excel spreadsheet in the provided range in Java with a PDF document. The output will be a single PDF file.

{{< gist GroupDocsGists bcf021b81840177ce42499faf038e441 "MergeSelectivePages.java" >}}

## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][17] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you learned how to merge two or more documents of similar or different file types into one file using Java with your application. Additionally, you learned how to combine selective pages of multiple file types into one file.

You can learn more about GroupDocs.Merger using the [documentation][18]. In case you have queries, contact us via [forum][19].

## See Also

*   [Split Files or Merge Documents in Java][20]
*   [Merge multiple files of different formats into one using C#][21]







[1]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[2]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[3]: #java-api-to-merge-multiple-file-types
[4]: #merge-multiple-files-into-one-pdf-in-java
[5]: #merge-selective-pages-of-multiple-files-into-one-pdf-in-java
[6]: https://products.groupdocs.com/merger/java/
[7]: https://docs.groupdocs.com/merger/java/supported-document-formats/
[8]: https://github.com/groupdocs-merger
[9]: https://apireference.groupdocs.com/merger/java
[10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.io.InputStream)
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.io.InputStream)
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/merger
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[21]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/

