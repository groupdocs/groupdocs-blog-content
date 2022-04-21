---
title: 'Highlight PDF using Annotations in C#'
date: Tue, 12 Oct 2021 14:08:00 +0000
draft: false
url: /2021/10/12/highlight-pdf-with-annotations-using-csharp/
author: 'Shoaib Khan'
summary: "While reviewing or to attract viewer to an important content, you may need to highlight some part of the document. As a developer, you can automate this feature by using highlight annotations within your applications. In this article, you will learn **how to highlight text and any area in PDF files using C#**."
tags: ['annotate PDF', 'Annotate PDF in CSharp', 'Highlight Annotation', 'Highlight PDF in CSharp', 'Highlight Text in PDF', 'Text Highlight']
categories: ['GroupDocs.Annotation Product Family']
---

While reviewing or to attract viewer to an important content, you may need to highlight some part of the document. As a developer, you can automate this feature by using highlight annotations within your applications. In this article, you will learn **how to highlight text and any area in PDF files using C#**.

The following topics are covered below:

*   [.NET API to Highlight in PDF][1]
*   [How to Programmatically Highlight in PDF][2]



{{< figure align=center src="images/add-highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Highlight Text in PDF - Programmatically">}}


## .NET API to Highlight in PDF {#highlight-pdf-dotnet-api}

[GroupDocs.Annotation][3] provides .NET API that allows manipulating annotations and their automation in documents within .NET applications. I am using this API to highlight text in the PDF file in the example of this article.

You can download the **DLLs** or **MSI** installer from the [downloads section][4] or install the API in your .NET application via [NuGet][5].

```
PM> Install-Package GroupDocs.Annotation
```

## Highlight in PDF using C# {#how-to-highlight-pdf}

The following are the steps to highlight text or any area in PDF from your .NET application.

*   Load the source PDF document using [Annotator][6] class.
*   Create the [HighlightAnnotation][7] object.
*   Define the highlight properties like the color, opacity, page number, and points.
*   Add the defined highlighting to the loaded PDF document using [Add][8] method.
*   Save the annotated PDF using [Save][9] method.

**Note:** You may change the highlight color, opacity, and other properties.

The following code sample shows how to highlight the text in PDF programmatically using C#.

{{< gist GroupDocsGists 489db43078dc098ec014662a64d3e81d "HighlightPDF.cs" >}}

The following is the output of the above code.



{{< figure align=center src="images/highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Highlight Text in PDF - Programmatically">}}


## Get a Free API License

You can [get a free temporary license][10] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we have learned how to add highlight annotation in PDF files programmatically using C#. Additionally, we can change the highlight color, opacity, and other properties. Many [different types of annotations][11] can be added in a similar way using the same API.

To learn about the API, visit the [documentation][12]. For queries, contact us via the [forum][13].

## See Also

*   [Watermark PDF Files using C#][14]
*   [Add Watermark to Images using C#][15]
*   [Add or Remove Annotations or Markup Word files using C#][16]







[1]: #highlight-pdf-dotnet-api
[2]: #how-to-highlight-pdf
[3]: https://products.groupdocs.com/annotation/
[4]: https://downloads.groupdocs.com/annotation
[5]: https://www.nuget.org/packages/groupdocs.annotation
[6]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[7]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/highlightannotation
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[15]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[16]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/

