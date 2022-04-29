---
title: "How to Split PDF Files using C#"
seoTitle: "Split PDF File into Multiple Files using C# | Split API for .NET"
description: "Different ways to split PDF files using C#. Separate large PDF files and extract specific pages using different splitting options."
date: Mon, 11 Oct 2021 04:14:00 +0000
draft: false
url: /2021/10/11/split-pdf-files-in-csharp/
author: 'Shoaib Khan'
summary: "[PDF][1] is one of the most commonly used file formats which is highly portable. As a developer, you may have faced the scenario to split large PDF files programmatically. Today, this article discusses different ways of **how to split PDF files using C# in .NET applications**."
tags: ['PDF Separator', 'Separate PDF', 'Split API', 'Split PDF', 'Split PDF Files', 'Split PDF using C#']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/split-pdf-into-multiple-files-using-csharp.jpg" alt="Split PDF into Multiple Files using C#">}}


[PDF][2] is one of the most commonly used file formats which is highly portable. As a developer, you may have faced the scenario to split large PDF files programmatically. In one of the articles, we learned to [split the PDF files in Java][3]. Today, this article discusses different ways of **how to split PDF files using C# in .NET applications**.

*   [.NET API to Split PDF Files][4]
*   [Split PDF into Multi-Page Files][5]
*   [Extract Pages from PDF Files by Range][6]
*   [Extract Pages from PDF Files using Even or Odd Filter][7]
*   [Split PDF into Multiple Single Pages Files][8]

## .NET API to Split PDF Files {#split-pdf-dontet-api}

In order to split PDF files, we will use [GroupDocs.Merger for .NET][9]. It is the API that allows rapid development to integrate features with very few lines of code. In addition to splitting, it supports [merging, swapping, or trimming documents of different file formats][10].

You can download the **DLLs** or **MSI** installer from the [downloads section][11] or install the API in your .NET application via [NuGet][12].

```
PM> Install-Package GroupDocs.Merger
```

## Split PDF File into MultiPage Files using C# {#split-pdf-to-multipage}

The following steps guide how you can split PDF files into multipage files using C#:

*   Define the output file(s) format.
*   Define the page intervals using [SplitOptions][13].
*   Load the PDF file using [Merger][14] class.
*   Split the loaded PDF according to defined interval using [Split()][15] method.

The following code sample shows how to split PDF files into multipage files.

{{< gist GroupDocsGists 4a46dd994d515ad491f5bcdcf6ec11d6 "SplitPDFintoMultiPageFiles.cs" >}}

## Extract Pages from PDF Files by Range {#extract-pages-by-range}

The following steps guide how to extract pages from PDF using C# by splitting according to the given range:

*   Define the output file(s) format.
*   Provide the pages range using [SplitOptions][16].
*   Load the PDF file using [Merger][17] class.
*   Use [Split()][18] method to split the loaded PDF according to the defined range.

The following code snippet shows how to split PDF and extract pages by providing the range.

{{< gist GroupDocsGists 4a46dd994d515ad491f5bcdcf6ec11d6 "SplitPdfByRange.cs" >}}

## Extract Even/Odd Pages from PDF Files using C# {#extract-even-or-odd-pages}

The following steps guide how to extract even/odd pages from a PDF file by splitting within the given range by just applying filters in C#:

*   Define the output file(s) format.
*   Provide the pages range using [SplitOptions][19].
*   Apply the filter for even, odd, or all pages using [RangeMode][20].
*   Load the PDF file using [Merger][21] class.
*   Use [Split()][22] method to separate the loaded PDF according to the defined filter.

The following code snippet shows how to extract all the odd/even pages in the defined range of a PDF file.

{{< gist GroupDocsGists 4a46dd994d515ad491f5bcdcf6ec11d6 "SplitPdfByRangeAndFilter.cs" >}}

## Split PDF File into Multiple Single-Page Files {#split-to-single-pages}

The following steps guide how we can split a PDF to extract pages as multiple single-page files in C#:

*   Define the output file(s) format.
*   Define the exact page numbers using [SplitOptions][23].
*   Load the PDF file using [Merger][24] class.
*   Split the loaded PDF according to defined pages using [Split()][25] method.

The following code sample shows how to split PDF files into multiple single-page files.

{{< gist GroupDocsGists 4a46dd994d515ad491f5bcdcf6ec11d6 "SplitPDFToSinglePages.cs" >}}

## Code Change Summary

In all the scenarios, the thing that changes is the way to define **SplitOptions**. Here is the summary of the change in each code snippet for each scenario. You can use the following settings as per your requirements within your code. Here, I used a PDF file having 10 pages.

*   **For Multipage Files - Use Interval**: \[1,2\], \[3,4,5\], \[6,7\], \[8,9,10\].

```
new SplitOptions(outputFile,  new int[] { 3, 6, 8 }, SplitMode.Interval)
```

*   **Extract Pages in Range**: \[3\], \[4\], \[5\], \[6\]

```
new SplitOptions(outputFile, 3, 6);
```

*   **Range with Filter**: \[3\], \[5\], \[7\]

```
new SplitOptions(outputFile, 3, 8, (Integer)RangeMode.OddPages);
```

*   **Individual Pages**: \[3\], \[4\], \[9\]

```
new SplitOptions(outputFile, new int[] { 3, 4, 9 });
```

## Get a Free API License

You can [get a free temporary license][26] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we discussed the ways to split PDF files using C#. First, we split the PDF file into multipage & single-page documents. We also extracted pages from PDF files. First, we extracted all the pages, and then even/odd pages within the given range. You can try building your own PDF splitting .NET App using GroupDocs.Merger API.

To learn more about the API, visit the [documentation][27]. For queries, contact us via the [forum][28].

## See Also

*   [Merge Documents using C#][29]
*   [Merge Multiple File Types into Single Document using C#][30]
*   [Rearrange PDF Pages using C#][31]
*   [Rearrange Pages in Word using C#][32]
*   [How to Split PDF Files in Java][33]







[1]: https://docs.fileformat.com/pdf/
[2]: https://docs.fileformat.com/pdf/
[3]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/
[4]: #split-pdf-dontet-api
[5]: #split-pdf-to-multipage
[6]: #extract-pages-by-range
[7]: #extract-even-or-odd-pages
[8]: https://blog.groupdocs.com/wp-admin/post.php?post=23730&action=edit#split-to-single-pages
[9]: https://products.groupdocs.com/merger/net/
[10]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[11]: https://downloads.groupdocs.com/merger
[12]: https://www.nuget.org/packages/groupdocs.merger
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/rangemode
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/splitoptions
[24]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[25]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/split/index
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/merger
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[30]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[31]: https://blog.groupdocs.com/2022/02/22/move-pdf-pages-using-csharp/
[32]: https://blog.groupdocs.com/2022/02/05/move-word-pages-using-csharp/
[33]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/

