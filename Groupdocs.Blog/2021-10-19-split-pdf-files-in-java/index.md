---
title: 'Different Ways to Split PDF Files in Java'
date: Tue, 19 Oct 2021 14:41:58 +0000
draft: false
url: /2021/10/19/split-pdf-files-in-java/
aliases:
    - /2021/10/19/split-pdf-files-in-java-2/
author: 'Shoaib Khan'
summary: "PDF is among the most famous file formats that support textual, graphical, and many other elements. One of the reasons for its popularity is its portability. In certain cases, you may need to split a large PDF file into multiple files. To address this programmatically, this article discusses different ways of **how to split PDF files in Java**."
tags: ['PDF Separator', 'Separate PDF', 'Split API', 'Split PDF', 'Split PDF Files', 'Split PDF in Java']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/split-pdf-into-multiple-files-in-java.jpg" alt="Split PDF into Multiple Files in Java">}}


[PDF][1] is among the most famous file formats that support textual, graphical, and many other elements. One of the reasons for its popularity is its portability. In certain cases, you may need to split a large PDF file into multiple files. To address this programmatically, this article discusses different ways of **how to split PDF files in Java**.

*   [Java API to Split PDF Files][2]
*   [Split PDF into Multi-Page Files][3]
*   [Split PDF into Multiple Single Pages Files][4]
*   [Extract Pages from PDF Files by Range in Java][5]
*   [Extract Pages from PDF Files using Even or Odd Filter in Java][6]

## Java API to Split PDF Files {#split-pdf-java-api}

[GroupDocs.Merger][7] provides the solution to merge and split files of many different file formats. We will use its [Java API][8] to split PDF files in different ways. Download the **JAR** file from the [downloads section][9], or just use the latest repository and dependency [Maven][10] configurations within your Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.9</version> 
</dependency>
```

## Split PDF File into MultiPage Files in Java {#split-pdf-to-multipage}

The following steps guide how you can split a PDF file into multipage files:

*   Load the PDF file using [Merger][11] class.
*   Define the output file(s) format.
*   Define the page intervals using [SplitOptions][12].
*   Split the loaded PDF according to defined interval using [split()][13] method.

The following code sample shows how to split PDF files into multipage files in Java.

{{< gist GroupDocsGists 0d92d118ccada913307231fbf3f741d2 "SplitPDFintoMultiPageFiles.java" >}}

## Split PDF File into Multiple Single-Page Files in Java {#split-to-single-pages}

The following steps guide how you can split a PDF to extract pages into multiple single-page files:

*   Load the PDF file using [Merger][14] class.
*   Define the output file(s) format.
*   Define the exact page numbers using [SplitOptions][15].
*   Split the loaded PDF according to defined pages using [split()][16] method.

The following code sample shows how to split PDF files into multiple single-page files in Java.

{{< gist GroupDocsGists 0d92d118ccada913307231fbf3f741d2 "SplitPDFToSinglePages.java" >}}

## Extract Pages from PDF Files by Range in Java {#extract-pages-by-range}

The following steps guide how to extract pages from PDF by splitting according to the given range:

*   Load the PDF file using [Merger][17] class.
*   Define the output file(s) format.
*   Provide the pages range using [SplitOptions][18].
*   Use [split()][19] method to split the loaded PDF according to the defined range.

The following code snippet shows how to split PDF and extract pages by providing range in Java.

{{< gist GroupDocsGists 0d92d118ccada913307231fbf3f741d2 "SplitPdfByRange.java" >}}

## Extract Pages from PDF Files using Even/Odd Filter in Java {#extract-even-or-odd-pages}

The following steps guide how to extract even/odd pages in the given range from PDF file by splitting:

*   Load the PDF file using [Merger][20] class.
*   Define the output file(s) format.
*   Provide the pages range using [SplitOptions][21].
*   Apply the even, odd, or all pages filter using [RangeMode][22].
*   Use [split()][23] method to split the loaded PDF according to the defined filter.

The following code snippet shows how to extract all the odd/even pages in the defined range of a PDF file using Java.

{{< gist GroupDocsGists 0d92d118ccada913307231fbf3f741d2 "SplitPdfByRangeAndFilter.java" >}}

## Code Change Summary

The only thing that differs in the above scenarios is the way to create **SplitOptions**. You can use the following configurations as per your requirements within your code.

*   **For Multipage Files - Use Interval**: \[1,2\], \[3,4,5\], \[6,7\], \[8,9,10\].

```
new SplitOptions(outputFile,  new int[] { 3, 6, 8 }, SplitMode.Interval)
```

*   **Individual Pages**: \[3\], \[6\], \[8\]

```
new SplitOptions(outputFile, new int[] { 3, 6, 8 });
```

*   **To Extract Pages in Range**: \[3\], \[4\], \[5\]

```
new SplitOptions(outputFile, 3, 5);
```

*   **Range with Filter**: \[3\], \[5\], \[7\]

```
new SplitOptions(outputFile, 3, 7, (Integer)RangeMode.OddPages);
```

## Get a Free API License

You can [get a free temporary license][24] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you have learned different ways to split PDF files in Java. First, we split the PDF file into multipage documents as well as in several single-page documents. Then one by one we extracted all the pages, and even/odd pages of the PDF file within the given range. Now you should be confident to build your own PDF splitter Java App using the GroupDocs.Merger API.

To learn more about the API, visit the [documentation][25]. For queries, contact us via the [forum][26].

## See Also

*   [Merge Multiple File Types into One using Java][27]
*   [Merge PDF, Word, Excel Documents in Java][28]
*   [Different Ways to Split PDF Files using C#][29]







[1]: https://docs.fileformat.com/pdf/
[2]: #split-pdf-java-api
[3]: #split-pdf-to-multipage
[4]: #split-to-single-pages
[5]: #extract-pages-by-range
[6]: #extract-even-or-odd-pages
[7]: https://products.groupdocs.com/merger/
[8]: https://products.groupdocs.com/merger/java/
[9]: https://downloads.groupdocs.com/merger
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-merger
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[20]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[21]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[22]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/RangeMode
[23]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/merger
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/
[28]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[29]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/

