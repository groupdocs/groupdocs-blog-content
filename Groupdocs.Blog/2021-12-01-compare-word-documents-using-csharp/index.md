---
title: 'Compare Word Documents using C#'
date: Wed, 01 Dec 2021 09:58:00 +0000
draft: false
url: /2021/12/01/compare-word-documents-using-csharp/
aliases:
    - /2014/07/19/groupdocs-comparison-for-dot-net-library-compare-two-word-documents-in-c-sharp-asp-net/
author: 'Shoaib Khan'
summary: "Word processing documents are the most common way to draft contracts, agreements, papers, and many other official documents. If you need to compare and merge two Word documents, just like the track changes option of Microsoft Word, we can programmatically do it within our .NET applications. In this article, we will discuss **how to compare two Word documents and highlight the identified differences using C#**. Additionally, we will look at how to compare password-protected documents, **accept and reject changes**, and compare more than two documents with C# examples."
tags: ['automate document comparison', 'compare two word documents', 'compare two word documents and highlight differences', 'Compare Word Documents CSharp', 'compare word files in c#', 'GroupDocs Comparison']
categories: ['GroupDocs.Comparison Product Family']
---

Word processing documents are the most common way to draft contracts, agreements, papers, and many other official documents. If you need to compare and merge two Word documents, just like the track changes option of Microsoft Word, we can programmatically do it within our .NET applications. In this article, we will discuss **how to compare two Word documents and highlight the identified differences using C#**. Additionally, we will look at how to compare password-protected documents, **accept and reject changes**, and compare more than two documents with C# examples.



{{< figure align=center src="images/compare-word-files-using-csharp.jpg" alt="Compare Word Documents to find differences using .NET API">}}


The following topics are discussed here:

*   [Document Comparison .NET API][1]
*   [Compare Two Word Documents][2]
*   [Accept or Reject Identified Changes in Word Document][3]
*   [Compare More than Two Word Documents][4]
*   [Compare Password Protected Word Files][5]

## .NET API to Compare Word Documents {#doc-comparison-dotnet-api}

[GroupDocs.Comparison][6] provides a .NET API that allows [comparing and then merging various documents of multiple file-formats][7] within the .NET application. I will use its .NET API i.e. [GroupDocs.Comparison for .NET][8] to compare Word documents.

You can download the DLLs or MSI installer from the [downloads section][9] or install the API in your .NET application via [NuGet][10].

```
PM> Install-Package GroupDocs.Comparison
```

## Compare Word Documents using C# {#compare-two-word-files}

If you have two versions of a document, you can compare the documents to find their differences (additions, deletions) and create a new document that shows all the changes. The following are the steps to compare any two Word documents and highlight the differences.

*   Load the first Word document using [Comparer][11] class.
*   Add the second file to **Comparer** using [Add()][12] method.
*   Compare the get changes summary by just calling [Compare()][13] method.

The following C# code shows how to compare Word documents and get the changes in the resultant document.

{{< gist GroupDocsGists 2bc5a8376473a179e59310fd3dc23a9f "CompareWordDocs.cs" >}}

## Accept or Reject Identified Changes of Word Documents using C# {#accept-reject-changes}

Similar to the track changes option of MS Word, you can accept or reject each identified change. The following are the steps to compare and then accept or reject the identified changes within the Word documents.

*   Load the source document and add target Word document(s) using [Comparer][14] class.
*   Make the comparison of loaded documents using [Compare()][15] method.
*   Get the identified changes using [GetChanges()][16] method.
*   Now you can traverse the changes and set [ComparisonAction][17] of each change.
    *   For each change you can select **Accept**, or **Reject**.
*   When done with changes, call the [ApplyChanges()][18] method to get the resultant document having the applied changes.

The following C# source code compares two Word documents and then accepts an identified change and then rejects another one.

{{< gist GroupDocsGists 2bc5a8376473a179e59310fd3dc23a9f "AcceptRejectComparedChanges.cs" >}}

## Compare More than Two Documents using C# {#compare-multiple-word-documents}

Similarly, more than two documents can be compared in one go. The following are the steps to compare multiple Word documents for differences and highlight the identified changes.

*   Load the first Word document using [Comparer][19] class.
*   Keep adding the other document(s) to **Comparer** using the [Add()][20] method.
*   Call the [Compare()][21] method to get the changes & summary of changes.

The following C# code shows how to compare more than two Word documents and get the changes in the resultant document.

{{< gist GroupDocsGists 2bc5a8376473a179e59310fd3dc23a9f "CompareMultipleDocs.cs" >}}

## Compare Password Protected Word Documents using C# {#compare-password-protected-word-docs}

If your documents are password-protected, just provide their password while loading the documents. The following steps show how we can compare the content of password-protected documents using C#.

*   Prepare the loading options for source and target documents by providing the password.
*   Load the source document using [Comparer][22] class.
*   Add the target document to **Comparer** using the prepared loading options.
*   Get the differences summary by calling the [Compare()][23] method.

The following C# code example compares two password-protected Word files and generates the resultant document that highlights the differences.

{{< gist GroupDocsGists 2bc5a8376473a179e59310fd3dc23a9f "CompareProtectedWordDocs.cs" >}}

## Get a Free API License

You can [get a free temporary license][24] to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to compare two or more Word documents using C#. Further, after highlighting the differences, we learned to programmatically accept and reject the identified changes. In the end, we also discussed how could we compare the password-protected Word documents within .NET applications.

There are many other [customizations to control the comparison results][25], like setting the comparison sensitivity, showing only the summary page, ignoring **gaps**, and much more. Learn more about **GroupDocs.Comparison for .NET**. Visit its [documentation][26] to start building your own document comparison applications for various [supported document formats][27]. For queries, contact us via the [forum][28].

## See Also

*   [Compare Image using C# to Spot the Differences][29]
*   [Compare PDF Documents using C# – Highlight, Accept or Reject Changes][30]
*   [How to Compare Text, Word, and PDF Files in Java][31]







[1]: #doc-comparison-dotnet-api
[2]: #compare-two-word-files
[3]: #accept-reject-changes
[4]: #compare-multiple-word-documents
[5]: #compare-password-protected-word-docs
[6]: https://products.groupdocs.com/comparison/
[7]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[8]: https://products.groupdocs.com/comparison/net/
[9]: https://downloads.groupdocs.com/comparison/net
[10]: https://www.nuget.org/packages/groupdocs.comparison
[11]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[12]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[15]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[16]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/getchanges/index
[17]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison.result/comparisonaction
[18]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/applychanges/index
[19]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[20]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[21]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[22]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[23]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/comparison/net/comparison/
[26]: https://docs.groupdocs.com/comparison/net
[27]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[30]: https://blog.groupdocs.com/2021/12/10/compare-pdf-documents-using-csharp/
[31]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/

