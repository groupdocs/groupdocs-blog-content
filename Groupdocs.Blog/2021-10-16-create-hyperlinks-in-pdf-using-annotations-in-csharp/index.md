---
title: 'Create Hyperlinks in PDF using Annotations in C#'
date: Sat, 16 Oct 2021 01:00:00 +0000
draft: false
url: /2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/
author: 'Shoaib Khan'
summary: "Hyperlinks are normally used to associate external data to any specified area of the document. We can transform any part of the documents to hyperlinks using the link annotations. As a programmer, you can add these link annotations to documents within your .NET applications. In this article, we are going to discuss that **how to create hyperlinks in PDF files using C#**."
tags: ['annotate PDF', 'Annotate PDF in CSharp', 'Create Hyperlink in PDF', 'Link Annotation', 'Link Annotation in CSharp', 'Link Annotation in PDF']
categories: ['GroupDocs.Annotation Product Family']
---

Hyperlinks are normally used to associate external data to any specified area of the document. We can transform any part of the documents to hyperlinks using the link annotations. As a programmer, you can add these link annotations to documents within your .NET applications. In this article, we are going to discuss that **how to create hyperlinks in PDF files using C#**.

The following topics are covered below:

*   [.NET API to Add Hyperlinks in PDF files][1]
*   [How to Programmatically Create Hyperlinks in PDF][2]



{{< figure align=center src="images/add-link-annotation-in-pdf-using-groupdocs.jpg" alt="Create Link in PDF - Programmatically">}}


## .NET API to Create Hyperlinks in PDF {#hyperlink-dotnet-api}

[GroupDocs.Annotation][3] provides the annotation solution for different kinds of applications. Its .NET API allows manipulation and automation of various annotations in documents within your .NET applications. We will use its [GroupDocs.Annotation for .NET][4] API to create hyperlink annotations in the PDF file using C#.

You can download the **DLLs** or **MSI** installer from the [downloads section][5] or install the API in your .NET application via [NuGet][6].

```
PM> Install-Package GroupDocs.Annotation
```

## Create Hyperlinks in PDF using C# {#how-to-create-hyperlink-annotations}

The following are the steps to create hyperlinks anywhere in the PDF file using C#.

*   Load the source PDF document using [Annotator][7] class.
*   Create the [Link Annotation][8] object.
*   Define the hyperlink properties like url, page number, points, etc.
*   Add the defined hyperlink to the loaded PDF document using [Add][9] method.
*   Save the annotated PDF using [Save][10] method.

The following code sample shows how to convert any part of the PDF file into a hyperlink using C#.

{{< gist GroupDocsGists 489db43078dc098ec014662a64d3e81d "AddHyperlinkInPDF.cs" >}}

The following is the output of the above code.



{{< figure align=center src="images/link-annotation-in-pdf-using-groupdocs.jpg" alt="Create Link in PDF - Programmatically">}}


## Get a Free API License

You can [get a free temporary license][11] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you have learned how the link annotations can be added to create hyperlinks in PDF files using C#. Likewise, using link annotations, you can convert any part of the document into hyperlinks. Many other [annotation types][12] can also be added in a similar way using the same API. Learn further about the API by visiting the [documentation][13]. For queries, contact us via the [forum][14].

## See Also

*   [Watermark PDF Files using C#][15]
*   [Add Watermark to Images using C#][16]
*   [Highlight PDF using Annotations in C#][17]
*   [Add or Remove Annotations or Markup Word files using C#][18]







[1]: #hyperlink-dotnet-api
[2]: #how-to-create-hyperlink-annotations
[3]: https://products.groupdocs.com/annotation/
[4]: https://products.groupdocs.com/annotation/net/
[5]: https://downloads.groupdocs.com/annotation
[6]: https://www.nuget.org/packages/groupdocs.annotation
[7]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[13]: https://docs.groupdocs.com/redaction
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[16]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[17]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[18]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/

