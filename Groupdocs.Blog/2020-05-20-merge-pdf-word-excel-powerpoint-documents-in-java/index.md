---
seoTitle: "Split or Merge PDF, PowerPoint, Excel, Word, Documents in Java"
title: 'Split or Merge PDF, Word, Excel Documents in Java'
date: Wed, 20 May 2020 08:22:00 +0000
draft: false
url: /2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
aliases:
    - /2020/02/20/split-or-merge-pdf-word-excel-documents-in-dotnet-or-java/
    - /2020/02/20/split-or-merge-pdf-word-excel-documents-in-csharp-or-java/
    - /2020/02/20/split-or-merge-pdf-word-excel-documents-in-c-or-java/
author: 'Shoaib Khan'
description: "Split or Merge PDF, Word DOC/DOCX, XLS/XLSX Excel spreadsheets, PPT/PPTX presentations, Visio Drawings, eBooks, & more documents in Java. Steps & examples."
summary: 'Worried about merge or split documents of various types in multiple platforms? There could be many statements in your mind: * How to merge PDF documents together in Java? * Want to split word documents, or merge excel spreadsheets. * What to do if I need to merge PPT/PPTX presentations. * Many more questions, the list may not end.'
tags: ['Merge Documents in Java', 'Merge PDF in Java', 'Merge Word in Java', 'Split Documents in Java', 'Split PDF in Java', 'Split PPT in Java']
categories: ['GroupDocs.Merger Product Family']
---

Worried about merge or split documents of various types in multiple platforms? There could be many statements in your mind:

*   How to merge PDF documents together in Java?
*   Want to split word documents, or merge excel spreadsheets.
*   What to do if I need to merge PPT/PPTX presentations.
*   Many more questions, the list may not end.



{{< figure align=center src="images/merge-split-documents-in-java-1.png" alt="Split or Merge PDF, Word, Excel documents in Java">}}




{{< figure align=center src="images/groupdocs-merger-java-90x90-no-reply.png" alt="GroupDocs.Merger for Java">}}


GroupDocs provides a [document merging solution][1] for all such requirements. It's [Java API][2] allows you to **merge documents** and manipulate document structure in Java across a wide range of supported document formats. It further allows manipulating document pages, page transformations, information extraction from the documents, generating previews, and much more.

In this article, we will look a bit about the following topics :

*   [How to merge PDF files in Java][3].
*   [Merge Word documents, Excel Spreadsheets, and PowerPoint presentations][4].
*   [Merge certain document pages][5].
*   [Split any document into multiple documents][6].

The code sample and steps explained below are using [GroupDocs.Merger for Java][7] so you may [download][8] or integrate it into your maven-based applications with pom.xml configurations.

## Merge PDF files in Java {#merge-pdf-files-in-java}

We can combine two or more PDF files in just a few lines of code. Below is the code snippet from the [examples][9], that is self-explanatory and needs no further clarification, hence shows how to merge multiple PDF documents in Java. Steps are very simple if you have done deciding the documents to join together:

*   Instantiate [Merger][10] object, with the first document with which other documents are to be merged.
*   Call [join][11] method, passing the document to merge.
*   Recall join method to merge more documents.
*   Call [save][12] method to save the final output.
*   That's it.

```
// Set paths for the documents to join together in a single file.
String filePath1 = "document-1.pdf";
String filePath2 = "document-2.pdf";
String filePath3 = "document-3.pdf";
// Merger multiple PDF documents into a single PDF file.
Merger merger = new Merger(filePath1 );
merger.join(filePath2 ); // Joining 2nd Document
merger.join(filePath3 ); // Joining 3rd Document
// Save the merged document.
String filePathOutput = "mergedDocument.pdf";
merger.save(filePathOutput);
```

## Merge Excel, Word, PowerPoint Documents in Java {#merge-excel-ppt-and-word-docs-in-java}

You can combine multiple Word documents, Excel Spreadsheets, PowerPoint presentations, in fact, almost any documents of the **same format**. The above code of joining PDF documents can be used to merge a wide variety of documents. At the bottom of the article, I will mention the list of file formats that can be merged with the same code. Here for an example, I am showing how similarly, more than two Word documents can be combined together into a single Word file in just a few lines of Java code.

```
// Merger multiple Word documents into a single DOCX file.
Merger merger = new Merger("document1.docx" );
merger.join("document2.docx" ); // Joining 2nd Document
merger.join("document3.docx" ); // Joining 3rd Document
// Save the merged document.
merger.save("mergedDocument.pdf");
```

## Merge Document Pages in Java {#merge-document-pages-in-java}

Multiple documents can be merged by selective pages and also by specifying the desired page range. Your code will remain similar to the mentioned above, just a little change while setting your merging options using [JoinOptions][13] class.

Below is the source code snippet that shows how to merge documents by specifying certain pages.

```
// Set the start and end page number in JoinOptions class.
JoinOptions joinOptions = new JoinOptions(1, 2);
// Merge two files with selective pages using join method.
Merger merger = new Merger("document-1.docx");
merger.join("document-2.docx" , joinOptions);
merger.save("merged-Document.docx");
```

## Split Documents into Multiple Documents in Java {#split-documents-in-java}

Just like we have merged documents above, we can also split Word documents, Excel spreadsheets, presentations, PDF files, and many other documents quickly in different ways.

*   Split by exact page numbers
*   Split a document to several multi-page documents
*   Split by page range
*   Split by Even and Odd pages

### Split by Exact Page Numbers

We can split a document by providing the exact number of pages in Java. The following code will split a PDF file into 3 documents, each having the mentioned single page.

*   Initialize the [SplitOptions][14] object with output file and mode to split.
*   Instantiate the [Merger][15] object with the source file or stream to split.
*   Call the [split][16] method to split the provided document and get it saved.

```
String filePath = "document.pdf";
String filePathOut = "document\_{0}.{1}";
// Split the document into multiple single page documents.
SplitOptions splitOptions = new SplitOptions(filePathOut, new int\[\] { 3, 6, 8 });
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

### Split Document into Multipage Documents

If you have a document with 6 pages, the below mentioned little modification in the above code will split your document into 3 separate documents in the following manner:

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Document Name</strong></td><td><strong>Page Numbers**</td></tr><tr><td>document_1</td><td>1, 2</td></tr><tr><td>document_2</td><td>3, 4, 5</td></tr><tr><td>document_3</td><td>6</td></tr></tbody></table></figure>

```
SplitOptions splitOptions = new SplitOptions(filePathOut,  SplitMode.Interval, new int\[\] { 3, 6 },);
```

### Split by Start & End Page Range

If you want to split any document by just providing the page range, here is how a Powerpoint presentation can be split into 3 single page presentations.

```
String filePath = "presentation.ppt";
String filePathOut = "presentation\_{0}.{1}";
// Split the presentation into multiple single page presentations.
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 5);
Merger merger = new Merger(filePath);
merger.split(splitOptions)
```

### Split by Even or Odd Page Ranges

You can set the even and odd page ranges to split. Following SplitOptions will allow splitting the provided document into multiple one-page documents for odd pages in the range of 3 to 8.

```
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 8, RangeMode.OddPages);
```

## Supported Document Formats

As promised, here is the list of document formats that can be merged or split with the above examples. You may visit [docs][17] anytime to check the updated list.

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**Document Type</strong></td><td><strong>File Formats**</td></tr><tr><td>Word Processing</td><td>DOC, DOCX, DOCM, DOT, DOTX, DOTM, ODT, OTT, RTF, TXT</td></tr><tr><td>Spreadsheets</td><td>XLS, XLSX, XLSM, XLSB, XLT, XLTX, XLTM, ODS, CSV, TSV</td></tr><tr><td>Presentations</td><td>PPT, PPTX, PPS, PPSX, ODP, OTP</td></tr><tr><td>Drawings</td><td>VSDX, VSDM, VSSX, VSSM, VSTX, VSTM, VDX, VSX, VTX</td></tr><tr><td>Web</td><td>HTML, MHT</td></tr><tr><td>Page Description Languages</td><td>TEX, XPS</td></tr><tr><td>eBooks &amp; Others</td><td>PDF, EPUB, ONE</td></tr></tbody></table></figure>

Good to see you here, you can freely contact us on the [forum][18] in case you feel any difficulty or have some confusion or want to give some good suggestions.







[1]: https://products.groupdocs.com/merger
[2]: https://products.groupdocs.com/merger/java
[3]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-pdf-files-in-java
[4]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-excel-ppt-and-word-docs-in-java
[5]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-document-pages-in-java
[6]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#split-documents-in-java
[7]: https://products.groupdocs.com/merger/java
[8]: https://downloads.groupdocs.com/merger/java
[9]: https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java
[10]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger
[11]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#join(java.lang.String)
[12]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#save(java.lang.String)
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
[14]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger.domain.options/SplitOptions
[15]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger
[16]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.IPageSplitOptions)
[17]: https://docs.groupdocs.com/merger/java
[18]: https://forum.groupdocs.com/c/merger

