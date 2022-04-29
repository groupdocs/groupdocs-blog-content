---
title: 'Compare PDF Documents using C# - Highlight, Accept or Reject Changes'
seoTitle: "Compare PDF Files using C# | Highlight, Accept or Reject Changes"
description: "Compare two or more PDF files in C# using document Comparison API for .NET. Highlight the differences and accept/reject changes even if password-protected."
date: Fri, 10 Dec 2021 10:20:37 +0000
draft: false
url: /2021/12/10/compare-pdf-documents-using-csharp/
aliases:
    - /2019/11/06/find-differences-in-pdf-accept-or-reject-changes-in-csharp/
    - /2019/11/06/accept-or-reject-pdf-comparison-changes-in-csharp/
author: 'Shoaib Khan'
summary: "Due to the fact that PDF is one of the most in-use formats of the digital world, it is often required to compare two versions of the same document. This article discusses, **how to compare two PDF documents and highlight the differences using C#**. Further, we will see how to compare password-protected PDF files, accept and reject changes, and also the comparison of more than two PDF files with C# examples."
tags: ['compare PDF files', 'Compare PDF in CSharp', 'Compare PDF to Accept or Reject Changes in CSharp', 'pdf comparison']
categories: ['GroupDocs.Comparison Product Family']
---

Due to the fact that PDF is one of the most in-use formats of the digital world, it is often required to compare two versions of the same document. This article discusses, **how to compare two PDF documents and highlight the differences using C#**. Further, we will see how to compare password-protected PDF files, accept and reject changes, and also the comparison of more than two PDF files with C# examples.



{{< figure align=center src="images/compare-pdf-files-using-csharp.jpg" alt="Compare PDF Documents to find differences using .NET API">}}


The following topics are discussed here:

*   [PDF Comparison .NET API][1]
*   [Compare Two PDF Documents][2]
*   [Accept or Reject Identified Changes within PDF Documents][3]
*   [Compare More than Two PDF Documents][4]
*   [Compare Password Protected PDF Files][5]

## .NET API to Compare PDF Files {#pdf-comparison-dotnet-api}

[GroupDocs.Comparison for .NET][6] is the API that allows comparison among multiple PDF documents and many other files of the same document format within the .NET applications. I will use this API in C# code examples of this article to compare PDF documents.

You can download the DLLs or MSI installer from the [downloads section][7] or install the API in your .NET application via [NuGet][8].

```
PM> Install-Package GroupDocs.Comparison
```

## Compare PDF Documents using C# {#compare-two-pdf-files}

If you have multiple copies of a PDF document, you can compare these files to find the differences (additions, deletions). After comparing the PDF content, you can create a new document that highlights all the identified changes. The following are the steps to compare two PDF documents and highlight the differences using C#.

*   Load the first PDF document using [Comparer][9] class.
*   Add the second file to **Comparer** using [Add()][10] method.
*   Compare both the PDF files and get the changes summary by calling [Compare()][11] method.

The following C# code snippet shows how to compare PDF documents and highlight the changes in the resultant document.

{{< gist GroupDocsGists bf49902dda69a05f94f88a324f67dd4e "ComparePDF.cs" >}}

## Accept or Reject Identified Changes of PDF Files using C# {#accept-reject-changes}

Just like the track changes features, you can programmatically accept or reject each identified change in PDF documents. The following steps show how to compare and then accept or reject the identified changes within the PDF documents.

*   Load the source and target PDF files using [Comparer][12] class.
*   Compare of loaded documents using [Compare()][13] method.
*   Get the identified changes using [GetChanges()][14] method.
*   Now traverse the changes and set the [ComparisonAction][15].
    *   Select **Accept**, or **Reject** for each change.
*   Call the [ApplyChanges()][16] method to get the resultant document with the accepted changes.

The following code snippet compares two PDF documents and then accepts an identified change and then rejects another one using C#.

{{< gist GroupDocsGists bf49902dda69a05f94f88a324f67dd4e "AcceptRejectPdfComparisonChanges.cs" >}}

## Compare More than Two PDF Files using C# {#compare-multiple-pdf-documents}

Similarly, you can compare more than two documents. The following are the steps that compare multiple PDF documents for differences and highlight the identified changes.

*   Load the first PDF files using [Comparer][17] class.
*   Add other document(s) to **Comparer** using the [Add()][18] method.
*   Compare all the PDF files using the [Compare()][19] method and get the changes & summary of changes.

The following example shows how to compare multiple PDF files in C# and get the changes in the resultant document.

{{< gist GroupDocsGists bf49902dda69a05f94f88a324f67dd4e "CompareMultiplePdfFiles.cs" >}}

## Compare Password Protected PDF Documents using C# {#compare-password-protected-pdf-files}

You can compare the password-protected files by just providing their passwords while loading these documents. The following steps show how we can compare the PDF content of password-protected documents using C#.

*   Prepare the loading options for source and target documents by providing the password.
*   Load the source document using [Comparer][20] class.
*   Add the target document to **Comparer** using the prepared loading options.
*   Get the differences summary by calling the [Compare()][21] method.

The following example compares two password-protected PDF files and highlights the identified differences in a separate document using C#.

{{< gist GroupDocsGists bf49902dda69a05f94f88a324f67dd4e "CompareProtectedPdfFiles.cs" >}}

## Get a Free API License

You can [get a free temporary license][22] to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned how to compare two or more PDF files using C#. Further, we highlighted the differences and programmatically accept or reject the identified changes. Lastly, we saw, how to compare password-protected PDF documents within .NET applications.

Several other [customizations][23] are available to control the comparison results. You can set the comparison sensitivity, show only the summary page, ignore **gaps**, etc. Learn more about **GroupDocs.Comparison for .NET** from the [documentation][24]. You can build your own document comparison applications for various [document formats][25]. For queries, contact us via the [forum][26].

## See Also

*   [Image Comparison using C# & Spot the Differences][27]
*   [Compare Word Documents using C#][28]
*   [Compare Documents with Java Difference Library][29]







[1]: #pdf-comparison-dotnet-api
[2]: #compare-two-pdf-files
[3]: #accept-reject-changes
[4]: #compare-multiple-pdf-documents
[5]: #compare-password-protected-pdf-files
[6]: https://products.groupdocs.com/comparison/
[7]: https://downloads.groupdocs.com/comparison/net
[8]: https://www.nuget.org/packages/groupdocs.comparison
[9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[10]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[12]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges/index
[15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/comparisonaction
[16]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/applychanges/index
[17]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[22]: https://purchase.groupdocs.com/temporary-license
[23]: https://docs.groupdocs.com/comparison/net/comparison/
[24]: https://docs.groupdocs.com/comparison/net
[25]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[28]: https://blog.groupdocs.com/2021/12/01/compare-word-documents-using-csharp/
[29]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/

