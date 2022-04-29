---
title: 'Strikethrough Text in Documents using C#'
seoTitle: "Strikethrough Text in Documents using C# | C̶r̶o̶s̶s̶ o̶u̶t̶ Text in Word, PDF"
description: "Use the strikeout annotation to cross out the invalid text within the documents using C#. Automate the document and image annotations with the .NET API."
date: Sat, 18 Dec 2021 19:10:44 +0000
draft: false
url: /2021/12/18/strikethrough-text-in-documents-using-csharp/
author: 'Shoaib Khan'
summary: "There are cases where you need to point out the content that has mistakes or it is no more valid. Crossed out is one of the ways to mark the invalid content within the documents. In order to automate the striking out within .NET applications, this article shows **how to strikethrough text in documents using C#**."
tags: ['Cross out Text', 'Cross out Text in CSharp', 'Strikeout Text', 'Strikethrough Text', 'Strikethrough Text in CSharp']
categories: ['GroupDocs.Annotation Product Family']
---



{{< figure align=center src="images/strikethrough-text-using-csharp.jpg" alt="StrikeThrough Text using C#">}}


There are cases where you need to point out the content that has mistakes or it is no more valid. Crossing out is one of the ways to mark the invalid content within the documents. So, in order to automate the striking out within .NET applications, this article shows **how to strikethrough text in documents using C#**.

The following topics are discussed in this article.

*   [.NET API for Strikethrough Annotations][1]
*   [How to Strikeout Text in Documents][2]

## .NET API to Strikethrough Text {#strikethrough-text-dotnet-api}

[GroupDocs.Annotation][3] is a document and image annotation solution that allows automating various annotation types within multiple document formats. Therefore, I will use its .NET API in the examples of this article to strikethrough text within the documents. In addition to the strikeout annotation, there are many other [supported annotation types][4] mentioned in the [documentation][5].

Download the DLLs or MSI installer from the [downloads section][6] or install the API in your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Annotation
```

## How to Strikethrough Text in Documents using C# {#strikethrough-text-using-csharp}

Let's quickly start to strike out the identified mistakes with the document. The following steps allow you to strikethrough the text in documents using C#.

*   Load the source document using [Annotator][8] class.
*   Create and define the strikethrough annotation using [StrikeoutAnnotation][9] class.
    *   Set the strikeout line color.
    *   Opacity, document page number
    *   Coordinates and other properties
*   Add the prepared strikeout annotation to the annotator using [Add()][10] method.
*   Save the annotated document using the [Save()][11] method.

The following C# code example crosses out the selected text in a PDF document.

{{< gist GroupDocsGists 685b95eda9e5db503efb2b123574c5af "StrikethroughText.cs" >}}

## Get a Free API License

You can use GroupDocs.Annotation for .NET for free by [getting a temporary license][12].

## Conclusion

To sum up, you learned to add strikethrough annotation using C#. Using this annotation, you can programmatically strike out the text within Word, PDF, spreadsheet, presentation documents. Similarly, you can try various other annotation types according to your requirement.

Learn more about **GroupDocs.Annotation for .NET** by visiting its [documentation][13]. You can build your own annotator application for the [supported document formats][14]. You can contact us for queries via the [forum][15].

## See Also

*   [Highlight PDF using Annotations in C#][16]
*   [Wavy Underline in Documents using C#][17]







[1]: #strikethrough-text-dotnet-api
[2]: #strikethrough-text-using-csharp
[3]: https://products.groupdocs.com/annotation/
[4]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[5]: https://docs.groupdocs.com/annotation/net/
[6]: https://downloads.groupdocs.com/annotation/net
[7]: https://www.nuget.org/packages/groupdocs.comparison
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/strikeoutannotation
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/annotation/net
[14]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[17]: https://blog.groupdocs.com/2021/12/04/add-wavy-underline-in-documents-using-csharp/

