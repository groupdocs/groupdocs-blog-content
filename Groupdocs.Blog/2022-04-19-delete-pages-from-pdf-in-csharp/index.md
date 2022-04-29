---
title: "Remove Pages from PDF using C#"
seoTitle: "Remove Pages from PDF using C# | Even, Odd, List & Range"
description: "Remove any set of pages from the PDF files using C#. Delete list of pages, any given range, even or odd pages from PDF files within .NET application."
date: Tue, 19 Apr 2022 11:00:00 +0000
draft: false
url: /2022/04/19/delete-pages-from-pdf-in-csharp/
aliases:
    - /2019/10/29/delete-one-or-more-pages-from-a-document-in-c/
    - /2019/10/29/delete-pages-from-documents-in-csharp/
author: 'Shoaib Khan'
summary: 'We often require removing the unwanted, obsolete, highly confidential pages from the documents while sharing or finalizing the drafts. In this article, we will learn **how to programmatically remove such pages from the PDF document using C#**. Requirements may differ at times, so we will discuss different ways to remove the different sets of pages within the PDF document.'
tags: ['delete pages', 'delete pages in csharp', 'remove pages', 'remove pages in csharp', 'delete pages from pdf in csharp', 'delete pages in csharp']
categories: ['GroupDocs.Merger Product Family']
---

We often require removing the unwanted, obsolete, highly confidential pages from the documents while sharing or finalizing the drafts. In this article, we will learn **how to programmatically remove such pages from the PDF document using C#**. Requirements may differ at times, so we will discuss different ways to remove the different sets of pages within the PDF document. 

The following topics are discussed below:

- [PDF Page Removal .NET API](#pdf-page-removal-dotnet-api)
- [Remove Selection/List of Pages](#remove-pdf-pages-list-in-csharp)
- [Delete Pages Range](#remove-pdf-pages-range-in-csharp)
- [Remove Even or Odd Range of Pages](#remove-even-odd-pdf-pages-in-csharp)

## .NET API to Remove Pages from PDF {#pdf-page-removal-dotnet-api}

GroupDocs.Merger showcases the .NET API that allows programmatically deleting pages from the PDF document. Additionally, it allows .NET applications to change pages orientation, move pages, split documents, extract, and rotate document pages. We will use this [GroupDocs.Merger for .NET][1] to delete selective pages of PDF files using C#. For the details and other features of the API, you can visit the [documentation][2].

You can download the DLLs or MSI installer from the [downloads section][3] or install the API in your .NET application via [NuGet][4].

```
PM> Install-Package GroupDocs.Merger
```

## Remove Selected Pages from PDF using C# {#remove-pdf-pages-list-in-csharp}

Just provide the list of pages from the loaded PDF document to remove. The below steps allow removing the provided list of selective pages from a PDF document using C#.

- Initialize [RemoveOptions][5] class with the **list of page numbers** to remove.
- Instantiate [Merger][6] object with source document path or stream.
- Call RemovePages() method to delete the listed pages.
- Call the appropriate Save() method to save the resultant document.

The following C# code example removes the selected 3rd and 5th pages from the PDF document.

{{< gist GroupDocsGists f1bb9b5f075b0ffa76183b96a7799c91 "RemoveListedPdfPages.cs" >}}

## Remove Pages Range from PDF using C# {#remove-pdf-pages-range-in-csharp}

Likewise, you can remove any range of pages within the PDF document. The following steps allow removing a sequence of pages within the provided range using C#.

- Initialize [RemoveOptions][5].
- Provide the **page range** by setting **starting** and **ending** page number.
- Instantiate [Merger][6] object with source document path or stream.
- Call RemovePages() method with the range.
- Call the appropriate Save() method to save the resultant document.

The following C# sample code removes all the pages from the PDF document within the provided range i.e. 2 to 4.

{{< gist GroupDocsGists f1bb9b5f075b0ffa76183b96a7799c91 "RemovePdfPagesRange.cs" >}}

## Remove Even or Odd Pages from PDF using C# {#remove-even-odd-pdf-pages-in-csharp}

Similarly, you can remove all the even or odd pages of the document. The following steps show how to remove even or odd pages of the PDF file within the given range using C#.

- Initialize [RemoveOptions][5] class with the page range.
- Set the mode to **even** or **odd**.
- Instantiate [Merger][6] object with source document path or stream.
- Call RemovePages() method with the removal options.
- Call the appropriate Save() method to save the resultant document.

The following C# code sample removes all the even pages from the PDF document within the provided range i.e. 1-6.

{{< gist GroupDocsGists f1bb9b5f075b0ffa76183b96a7799c91 "RemovePdfEvenPages.cs" >}}

The following C# code snippet removes all the odd pages from the whole PDF document.

{{< gist GroupDocsGists f1bb9b5f075b0ffa76183b96a7799c91 "RemovePdfOddPages.cs" >}}

## Get a Free API License

You can [get a free temporary license][7] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we just learned how to delete pages from a PDF document using C# within .NET applications. Specifically, we have seen how to delete pages by providing page numbers and page ranges. Finally, we saw how to remove even or odd pages from any PDF document. You can try building your own application to eliminate any variation of selected pages from the PDF files.

For more details about the API, visit the documentation. For queries, contact us via the [forum][8].

## See Also
- [Remove Watermarks from PDF Documents in C#][9]
- [Convert PDF to Grayscale using C#][10]
- [How to Rearrange PDF Pages using C#][11]
- [Find and Replace Text in PDF using C#][12]
- [Lock & Unlock PDF Files with Password using C#][13]

[1]: https://products.groupdocs.com/merger/net
[2]: https://docs.groupdocs.com/merger/net/
[3]: https://downloads.groupdocs.com/merger/net
[4]: https://www.nuget.org/packages/groupdocs.merger/
[5]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/removeoptions
[6]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[7]: https://purchase.groupdocs.com/temporary-license
[8]: https://forum.groupdocs.com/
[9]: https://blog.groupdocs.com/2022/03/25/remove-watermark-from-pdf-in-csharp/
[10]: https://blog.groupdocs.com/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/
[11]: https://blog.groupdocs.com/2022/02/22/move-pdf-pages-using-csharp/
[12]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[13]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
