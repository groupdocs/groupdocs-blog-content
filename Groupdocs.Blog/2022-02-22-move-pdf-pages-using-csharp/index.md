---
title: 'How to Rearrange PDF Pages using C#'
date: Tue, 22 Feb 2022 12:10:45 +0000
draft: false
url: /2022/02/22/move-pdf-pages-using-csharp/
aliases:
    - /2022/02/22/move-pdf-pages-using-csharp-2/
    - /2019/10/30/move-pages-in-pdf-using-groupdocs.merger-for-.net-and-java/
author: 'Shoaib Khan'
summary: 'In this digital era, PDF is one of the most used file formats and is popular due to its portability. On the other hand, most of the time we can not edit the PDF files. When we merge multiple documents and pages together to form a combined comprehensive document, it often happens that we finish combining the pages in the wrong order. This article discusses, **how to rearrange PDF pages programmatically using C#**.'
tags: ['Rearrange Document', 'Rearrange PDF Pages', 'Rearrange PDF Pages in CSharp']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-pdf-pages-using-csharp-dotnet.jpg" alt="Rearrange PDF Pages using C# .NET">}}


In this digital era, PDF is one of the most used file formats and is popular due to its portability. On the other hand, most of the time we can not edit the PDF files. When we merge multiple documents and pages together to form a combined comprehensive document, it often happens that we finish combining the pages in the wrong order. This article discusses, **how to rearrange PDF pages programmatically using C#**.

## .NET API to Rearrange PDF Pages & Merge Documents

In order to rearrange pages in documents, GroupDocs provides [GroupDocs.Merger for .NET](https://products.groupdocs.com/merger/net/). The API enables removing, splitting, and extraction of pages, changes in page orientation, and rotation of document pages within .NET applications. For the details and other features of the API, you can visit the [documentation](https://docs.groupdocs.com/merger/net/).

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/merger) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.merger).

```
PM> Install-Package GroupDocs.Merger
```

## Rearrange PDF Pages using C#

The following are the steps that reorder the pages of PDF documents using C#.

*   Define the existing and new position of the page in [MoveOptions](https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/moveoptions) class.
*   Load the PDF document using the [Merger](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger) class.
*   Use [MovePage()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/movepage) method to reorder according to defined options.
*   Save the PDF file with the new page order using the [Save()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index) method.

The following C# code rearranges the pages of PDF documents. Precisely, it moves the 6th page of the document to the 1st place.

{{< gist GroupDocsGists a02ebe5ab882ca7a519891925490e1bb "MovePagesInPDF.cs" >}}

Here is the output of the above code.



{{< figure align=center src="images/Screenshot-1024x454.png" alt="">}}


## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned how to reorder pages of the PDF files using C# within the .NET applications. We saw the running example to change the position of the page. You can try building a simple application that can organize the PDF files by easily shuffling their pages.

For more details about the API, visit the [documentation](https://docs.groupdocs.com/merger/). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [How to Rearrange PDF Pages in Java](https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/)
*   [Password Protect PDF Files using C#](https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/)
*   [Split PDF Files using C#](https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/)
*   [Merge Multiple File Types into One Document using C#](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/)




