---
title: 'How to Rearrange Pages in Word using C#'
date: Sat, 05 Feb 2022 08:19:00 +0000
draft: false
url: /2022/02/05/move-word-pages-using-csharp/
author: 'Shoaib Khan'
summary: 'In the digital world, word processing documents are one of the most commonly used file formats that are used to create and edit documents. While dealing with large documents, it is really not easy to move pages without losing the formatting. Formatting loss often happens when we try to [combine multiple documents of different types](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/) or we simply [merge the same type of files](https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/) into one single document. In order to rearrange the pages, this article discusses, **how to programmatically move pages in Word documents (DOC/DOCX) using C#**.'
tags: ['Move Pages in CSharp', 'Move Pages in DOC/DOCX', 'Rearrange Document', 'Rearrange Document Pages in CSharp', 'Rearrange pages in CSharp', 'Rearrange pages in Word']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-word-pages-using-csharp-dotnet.jpg" alt="Rearrange Word Pages using C# .NET">}}


In the digital world, word processing documents are one of the most commonly used file formats that are used to create and edit documents. While dealing with large documents, it is really not easy to move pages without losing the formatting. Formatting loss often happens when we try to [combine multiple documents of different types](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/) or we simply [merge the same type of files](https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/) into one single document. In order to rearrange the pages, this article discusses, **how to programmatically move pages in Word documents (DOC/DOCX) using C#**.

## .NET API to Move Word Document Pages

**GroupDocs.Merger** provides the .NET API that enables moving, removing, splitting of documents, and extraction of pages, changes in page orientation, and rotation of document pages within the .NET applications. Today, we will use this API to move pages of DOC/ DOCX files using C#. For the details and other features of the API, you can visit the [documentation](https://docs.groupdocs.com/merger/).

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/merger) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.merger).

```
PM> Install-Package GroupDocs.Merger
```

## Move Pages in Word Documents using C#

The moving of pages is simple. Just command that particular page to move to its new position. The following are the steps that rearrange the pages of a Word document using C#.

*   Define the page number of the target page and its new position using the [MoveOptions](https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/moveoptions) class.
*   Load the DOC/DOCX document using the [Merger](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger) class.
*   Use [MovePage()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/movepage) method to move the page.
*   Save the rearranged document using the [Save()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index) method.

The following C# code helps rearrange the pages of a Word document. Precisely, it moves the 7th page of a DOCX document to the 2nd place.

{{< gist GroupDocsGists 82e3cb6fd5443747d7e700199a5a3cb4 "MovePagesInWord.cs" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned how to change page order in Word documents using C# within .NET applications. We saw the source code example that changed the position of the page in a DOCX file. You can build your own application that can rearrange Word pages online by easily shuffling the pages.

For more details about the API, visit the [documentation](https://docs.groupdocs.com/merger/net). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Compare Word Documents](https://blog.groupdocs.com/2021/12/01/compare-word-documents-using-csharp/)
*   [Edit Word Documents](https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/)
*   [Protect/UnProtect Word Files with Password](https://blog.groupdocs.com/2021/11/27/password-protect-word-documents-using-csharp/)
*   [View Word Documents as HTML Responsive Page](https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/)
*   [Add or Remove Annotations or Markup Word files](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)




