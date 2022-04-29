---
seoTitle: "C# Compare Excel, Word, Text Files | .NET Document Comparison API"
title: 'Compare Two Files or More in C#'
date: Tue, 10 Mar 2020 22:25:55 +0000
draft: false
url: /2020/03/10/compare-excel-word-pdf-files-in-csharp/
aliases:
    - /2020/03/10/compare-two-files-or-more-in-csharp-word-document-excel-spreadsheet/
    - /2015/01/14/groupdocs-comparsion-for-dot-net-sample-compare-two-documents-in-csharp-and-display-diffs-on-aps-net-sites/
author: 'Shoaib Khan'
description: "Compare two files or more using C#. .NET SDK allows comparing two Excel spreadsheets, Word documents, PDF files or compare text files in CSharp."
summary: "Document comparison is one of the most common requirements for today's programming world. Whether it is to compare word files, compare excel files, PDF documents or even compare text files or any other document format, accuracy is the key factor while comparing."
tags: ['compare documents', 'compare excel files', 'compare PDF files', 'compare text files', 'compare two documents', 'compare two excel files', 'compare two files', 'compare two word documents', 'compare word documents', 'document comparison', 'file compare']
categories: ['GroupDocs.Comparison Product Family']
---

Document comparison is one of the most common requirements for today's programming world. Whether it is to compare word files, compare excel files, PDF documents or even compare text files or any other document format, accuracy is the key factor while comparing.



{{< figure align=center src="images/groupdocs-comparison-net-90x90-no-border.png" alt="Compare Files with Document Comparison API for .NET Developers">}}


This article will give you the idea, how **[GroupDocs.Comparison][1]** facilitates programmers to compare any two or more documents in many ways. [On-Premise][2] APIs of GroupDocs.Comparison are currently available for [.NET][3] and [Java][4], however, this article is inclined towards C# developers.

## Compare Excel, Word Files or any Document in C#

[GroupDocs.Comparison][5] allows developers to compare two documents ([in fact more than 2][6]. The resulting document shows the changes between the two files in comparison. Below mentioned code shows how you can compare two excel files in just 3 lines of code in C#.

1.  Instantiate the [Comparer][7] object with the source document path.
2.  Call [Add][8] method to specify the target document path.
3.  Call [Compare][9] method.
4.  That's it.

```
using (Comparer comparer = new Comparer(“source.xlsx”))
{
    comparer.Add(“target.xlsx”);
    comparer.Compare(“result.xlsx”);
}
```

Comparing excel spreadsheets or Microsoft Word documents are just among the subset of comparisons that are supported by the .NET API of GroupDocs.Comparison. Below is the list of supported formats. You can visit the [documentation][10] to stay updated.

<figure class="wp-block-table is-style-stripes"><table class=""><tbody><tr><td>**Document Type</strong></td><td><strong>File Formats**</td></tr><tr><td><a href="https://wiki.fileformat.com/word-processing/">Word Processing</a></td><td>DOC, DOCX, DOCM, DOT, DOTX, DOTM, RTF, TXT</td></tr><tr><td><a href="https://wiki.fileformat.com/spreadsheet/">Spreadsheets</a></td><td>XLS, XLSX, XLSM, XLT, XLTM, XLSB, XLSM, CSV</td></tr><tr><td><a href="https://wiki.fileformat.com/presentation/">Presentations</a></td><td>PPT, PPTX, PPS, PPSX, POT, POTX</td></tr><tr><td><a href="https://wiki.fileformat.com/word-processing/">OpenDocument</a></td><td>ODT, ODP, OTP, ODS, OTT</td></tr><tr><td><a href="https://wiki.fileformat.com/view/pdf/">Portable</a></td><td>PDF</td></tr><tr><td><a href="https://docs.fileformat.com/visio/">Microsoft Visio Drawings</a></td><td>VSD, VSDX, VSS, VST, VDX</td></tr><tr><td><a href="https://wiki.fileformat.com/note-taking/">Note Taking</a></td><td>ONE</td></tr><tr><td><a href="https://wiki.fileformat.com/web/">Web</a></td><td>HTM, HTML, MHT, MHTML</td></tr><tr><td><a href="https://wiki.fileformat.com/ebook/">eBooks</a></td><td>MOBI</td></tr><tr><td><a href="https://wiki.fileformat.com/image/">Images</a></td><td>BMP, GIF, JPG, JPEG, PNG, DICOM, DJVU, DWG, DXF</td></tr><tr><td><a href="https://wiki.fileformat.com/email/">Emails</a></td><td>EML, EMLX, MSG</td></tr></tbody></table></figure>

## Compare two or more Spreadsheets or OneNote Documents in C#

After the release of GroupDocs.Comparison for .NET 20.2, the API now supports:

*   Comparison of more than two **Microsoft Excel** and **OpenOffice** **spreadsheets** (XLS, XLSX, ODS, CSV, ...)
*   Compare multiple Microsoft OneNote documents.

The API already supports the comparison of multiple files for various document formats. Following code snippet shows how quickly, multiple excel files can be compared in C#.

```
using (Comparer comparer = new Comparer(“source.xlsx”)
{
    comparer.Add(“target1.xlsx”);
    comparer.Add(“target2.xlsx”);
    comparer.Add(“target3.xlsx”);
    comparer.Compare(“result.xlsx”);
}
```

## Compare Documents from Stream in C#

As a programmer, you are not only allowed to compare documents that are available on local storage, in fact, we can compare documents from the stream.

1.  Just initialize the [Comparer][11] object with the source document stream.
2.  Call [Add][12] method and specify the target stream.
3.  Call [Compare][13] method

```
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”))
{
    comparer.Add(File.OpenRead(“target1.docx”));
    comparer.Add(File.OpenRead(“target2.docx”));
    comparer.Add(File.OpenRead(“target3.docx”));
    comparer.Compare(File.Create(“result.docx”));
}
```

## Compare Password Protected Word Documents / Excel Spreadsheet in C#

Password protection is common in the official documentation. Using the document comparison .NET API, it allows its users/developers to compare password-protected documents.

Just a little change in the code as compared to the code for comparing documents that are not password-protected. While loading the document, use [LoadOptions][14] to specify the document password. Below is the sample comparison code for your assistance.

```
using (Comparer comparer = new Comparer("source.docx", new LoadOptions() { Password = "1234" }))
{
    comparer.Add("target1.docx", new LoadOptions() { Password = "5678" });
    comparer.Add("target2.docx", new LoadOptions() { Password = "5678" });
    comparer.Add("target3.docx", new LoadOptions() { Password = "5678" });
    comparer.Compare("result.docx");
}
```

## Comparison of Documents with Specific Settings

One step ahead of just comparing, using the code similar to the mentioned below, you can compare multiple documents with your customized comparison settings.

[CompareOptions][15] provides you the opportunity to specify your comparison options like font styling for detected changes etc.

```
using (Comparer comparer = new Comparer(“source.docx”)
{
    comparer.Add(“target1.docx”);
    comparer.Add(“target2.docx”);
    comparer.Add(“target3.docx”);
    CompareOptions compareOptions = new CompareOptions()
    {
        InsertedItemStyle = new StyleSettings()
        {
            FontColor = System.Drawing.Color.Yellow
        }
    };
    comparer.Compare(“result.docx”, compareOptions);
}
```

## Compare Programming Language Files in C#

GroupDocs continuously increasing the support to compare more file formats. After the release v 20.2, you can now also compare JSON files using .NET API. Following are the programming language file formats that are recently added to the [supported document formats list][16]:

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td>ActionScript</td><td>Objective C/C++</td></tr><tr><td>Assembler</td><td>Perl</td></tr><tr><td>C-Based</td><td>PHP</td></tr><tr><td>CSharp</td><td>Python</td></tr><tr><td>Groovy</td><td>Ruby</td></tr><tr><td>JavaScript</td><td>Scala</td></tr><tr><td>Java</td><td>Shell/Batch Script, Log, Diff, Config, LESS</td></tr><tr><td>JSON</td><td>SQL</td></tr></tbody></table></figure>

## Let’s Talk

You can build your own application using the above-highlighted features. We will be delighted if you contact us on the [forum][17] to discuss, solving a problem, or share your feedback.







[1]: https://products.groupdocs.com/comparison
[2]: https://products.groupdocs.com/comparison/family
[3]: https://products.groupdocs.com/comparison/net
[4]: https://products.groupdocs.com/comparison/java
[5]: https://products.groupdocs.com/comparison/family
[6]: https://docs.groupdocs.com/display/comparisonnet/Compare+multiple+documents)
[7]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[8]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[9]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[10]: https://docs.groupdocs.com/comparison/net
[11]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[12]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/loadoptions
[15]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/compareoptions
[16]: https://docs.groupdocs.com/comparison/net
[17]: https://forum.groupdocs.com/c/comparison

