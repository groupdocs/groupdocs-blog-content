---
title: 'C# Diff Library for Comparing Text Files'
date: Thu, 30 Apr 2020 14:41:00 +0000
draft: false
url: /2020/04/30/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
aliases:
    - /2014/07/04/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
author: 'Muhammad Sohail'
summary: 'The [GroupDocs.Comparison for .NET][1] is a C# library which allows you to compare documents and find differences. Compare and merge Microsoft Word, Excel, PowerPoint, OpenDocument, PDF, Text, HTML and [many other documents][2], retrieve a list of changes between source and target document(s), apply or reject changes and save results with GroupDocs.Comparison API. In addition to this, GroupDocs.Comparison can identify styling and formatting changes - like bold, italic, underlines, strikethroughs, font types, etc.'
tags: ['compare text files', 'diff view library', 'GroupDocs Comparison']
categories: ['GroupDocs.Comparison Product Family']
---



{{< figure align=center src="images/groupdocs-comparison-128x128-1.png" alt="">}}


The [GroupDocs.Comparison for .NET][3] is a C# library which allows you to compare documents and find differences. Compare and merge Microsoft Word, Excel, PowerPoint, OpenDocument, PDF, Text, HTML and [many other documents][4], retrieve a list of changes between source and target document(s), apply or reject changes and save results with GroupDocs.Comparison API. In addition to this, GroupDocs.Comparison can identify styling and formatting changes - like bold, italic, underlines, strikethroughs, font types, etc.

Changes detection algorithms used by [GroupDocs.Comparison][5] allows to detect differences in different document parts and blocks:

*   Text blocks - paragraphs, words and characters;
*   Tables;
*   Images;
*   Shapes etc.

Here are simple steps to compare two text files and show differences: 

*   Instantiate [Comparer][6] object with source document path or stream;
*   Call [Add][7] method and specify the target document path or stream;
*   Call [Compare][8] method.

The following code snippet demonstrates the simplest case of documents comparison using a couple lines of code. 

### Compare documents from local file

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare(“result.docx”);
}
```

### Compare documents from the stream
```
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”)))
{
    comparer.Add(File.OpenRead(“target.docx”));
    comparer.Compare(File.Create(“result.docx”));
}
```

Let's say you have two contracts in DOCX format that were concluded in different years. If you use the above code to compare these contracts, you get a DOCX file where the deleted elements are marked in red, the added in blue, and the modified in green as shown below:



{{< figure align=center src="images/FreelanceContract.png" alt="">}}


## Accept or Reject detected differences

[GroupDocs.Comparison][9] provides an ability to apply or discard specific changes between source and target documents and save the resultant document with (or without) selected changes.

The following are the steps to apply/reject changes to the resultant document.

*   Instantiate [Comparer][10] object with source document path or stream;
*   Call _[A][11]_[dd][12] method and specify path target document path or stream;
*   Call [Compare][13] method;
*   Call [GetChanges][14] method and obtain detected changes list;
*   Set [ComparisonAction][15] of needed change object to [ComparisonAction.Accept][16] or [ComparisonAction.Reject][17] value;
*   Call [ApplyChanges][18] method and pass collection of changes to it.

The following code sample shows how to accept/reject detected differences.

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges(File.Create(“result.docx”), new SaveOptions(), new ApplyChangeOptions() { Changes = changes });
}
```

## Generate document pages preview

[GroupDocs.Comparison][19] allows to generate page previews for source, target and resultant document(s) using [GeneratePreview][20] method of a [Document][21] class.

[PreviewOptions][22] class is used to manage preview generation process - specify desired page numbers, image format etc.

The following are the steps to generate a document preview with GroupDocs.Comparison API:

*   Create a new instance of [Comparer][23] class and pass the source document path as a constructor parameter;
*   Add target document(s) to comparison using [Add][24] method;
*   [Source][25] and [Targets][26] properties of [Comparer][27] object allows to access source and target documents and provides [GeneratePreview][28] method;
*   Instantiate the [PreviewOptions][29] object with:
    *   delegate for each page stream creation (see event handler CreatePageStream); 
    *   image preview format - PNG / JPG / BMP;
    *   page numbers to process;
    *   custom size of preview images (if needed).
*   Call [GeneratePreview][30] method of [Source][31] and [Targets][32] document and pass [PreviewOptions][33] to it.

### Get page previews for resultant document

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare(“result.docx”);
    Document document = new Document(File.OpenRead(“result.docx”));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(“C:\\”, $"result\_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    document.GeneratePreview(previewOptions);
}
```

## Compare multiple documents

[GroupDocs.Comparison][34] allows comparing more than two documents. The following code sample shows how to compare multiple documents programmatically.

```
using (Comparer comparer = new Comparer(“source.docx”)
{
    comparer.Add(“target1.docx”);
    comparer.Add(“target2.docx”);
    comparer.Add(“target3.docx”);
    comparer.Compare(“result.docx”);
}
```

## Installation

[NuGet][35] is the easiest way to download and install GroupDocs.Comparison for .NET. Please [get a temporary license][36] to test the library without any functional restrictions.

Please check the [documentation][37] to learn more about the library. We also offer free technical support so please feel free to [contact us][38] - we will be happy to help.


[1]: https://products.groupdocs.com/comparison/net
[2]: https://docs.groupdocs.com/comparison/net
[3]: https://products.groupdocs.com/comparison/net
[4]: https://docs.groupdocs.com/comparison/net
[5]: https://apireference.groupdocs.com/comparison/net
[6]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[7]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[8]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[9]: https://products.groupdocs.com/comparison/net
[10]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[11]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[12]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/getchanges/index
[15]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/changeinfo/properties/comparisonaction
[16]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/comparisonaction
[17]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/comparisonaction
[18]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/applychanges/index
[19]: https://products.groupdocs.com/comparison/net
[20]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[21]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document
[22]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[23]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[24]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[25]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/source
[26]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/targets
[27]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[28]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[29]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[30]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[31]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/source
[32]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/targets
[33]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[34]: https://products.groupdocs.com/comparison/net
[35]: https://www.nuget.org/packages/GroupDocs.Comparison/
[36]: https://purchase.groupdocs.com/temporary-license
[37]: https://docs.groupdocs.com/display/comparisonnet/Home
[38]: https://forum.groupdocs.com/

