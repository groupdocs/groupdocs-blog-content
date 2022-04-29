---
title: 'Add Wavy Underline in Word, PDF &amp; Other Documents using C#'
seoTitle: "Add Wavy Underline in Word, PDF, PPT using C# | Squiggly Annotation"
description: "Insert different colored wavy underlines in Word, PDF, and other documents using C#. Add squiggly annotation in documents within the .NET applications."
date: Sat, 04 Dec 2021 15:37:01 +0000
draft: false
url: /2021/12/04/add-wavy-underline-in-documents-using-csharp/
author: 'Shoaib Khan'
summary: "Squiggly underlines are normally used to show inconsistencies in the document. We are quite familiar with these lines as Microsoft Word uses red squiggly underlines to indicate spelling mistakes and blue squiggly/wavy underlines for formatting issues. We can also add such underline annotations in documents programmatically. In this article, we will learn **how to add wavy underlines in Word, PDF, PPT, and other documents using C#**."
tags: ['Annotation in CSharp', 'Squiggly Annotation in CSharp', 'Squiggly Underline in Word', 'Wavy Underline in CSharp', 'Wavy Underline in Word']
categories: ['GroupDocs.Annotation Product Family']
---

Squiggly underlines are normally used to show inconsistencies in the document. We are quite familiar with these lines as Microsoft Word uses red squiggly underlines to indicate spelling mistakes and blue squiggly/wavy underlines for formatting issues. We can also add such underline annotations in documents programmatically. In this article, we will learn **how to add wavy underlines in Word, PDF, PPT, and other documents using C#**.



{{< figure align=center src="images/adding-squiggly-annotation.jpg" alt="Add Squiggly Annotation to Documents">}}


The following topics are discussed below:

*   [.NET API for Wavy Underline / Squiggly Annotation][1]
*   [Add Wavy Underline to Text in Word Documents - Squiggly Annotation][2]
*   [Add Wavy Underline to Text in PDF, PPT, and other Documents][3]

## .NET API for Wavy Underline - Squiggly Annotation {#wavy-underline-dotnet-api}

[GroupDocs.Annotation][4] provides the annotation solution that allows manipulation and automation of various annotation types in documents within .NET applications. We will use its [GroupDocs.Annotation for .NET][5] API to add a squiggly annotation in documents using C#.

You can download the **DLLs** or **MSI** installer from the [downloads section][6] or install the API in your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Annotation
```

## Add Wavy Underline to Text in Word (DOC/DOCX) using C# - Squiggly Annotation {#add-wavy-underline-in-word}

The following step shows how to insert a wavy underline in a Word document using C#.

*   **Load** the Word (DOC, DOCX) using the [Annotator][8] class.
*   **Create the wavy underline** using the [SquigglyAnnotation][9] class.
*   **Personalize** the squiggly underline by setting its color, opacity, coordinates, page number, etc.
*   [**Add**][10] the squiggly annotation to the annotator.
*   **Save** the updated Word file using [Save()][11] method.

The following C# code example adds the wavy underline to the selected text of the Word document.

{{< gist GroupDocsGists 0d25b0bfdc7cfaaa084bbaab8509adf9 "AddSquigglyAnnotationToWord.cs" >}}

You can add any other annotation type from various [AnnotationModels][12].

## Add Wavy Underline to Text in PDF, PPT, and Other Documents using C# {#wavy-underline-in-pdf-ppt-etc}

Similarly, you can add the squiggly underline to any document using the same C# code (Check the documentation if your intended document file format is supported by the API).

The following are the steps for how to insert a wavy underline in a PDF document using C#.

*   **Load** the PDF document using the [Annotator][13] class.
*   **Create the squiggly underline** using the [SquigglyAnnotation][14] class.
*   **Customize** the color, opacity, coordinates, page number, etc for the squiggly/wavy underline.
*   **Add** the squiggly annotation to the annotator using [Add()][15] method.
*   **Save** the updated PDF file using [Save()][16] method.

The following C# code example adds the wavy underline to the selected text of the PDF file.

{{< gist GroupDocsGists 0d25b0bfdc7cfaaa084bbaab8509adf9 "AddSquigglyAnnotationToPDF.cs" >}}

## Conclusion

To sum up, we discussed how to add wavy/squiggly underline in Word documents using C#. Additionally, the same squiggly annotation can be added to other documents like PDF, PPT, and more. Squiggly annotation is a new addition to [many other annotation types offered by the API][17].

Learn more about **GroupDocs.Annotation for .NET**. Visit its [documentation][18] to start building your own document annotation applications for various [supported document formats][19]. For queries, contact us via the [forum][20].

## See Also

*   [Add or Remove Annotations or Markup Word files using C#][21]
*   [Add or Remove Annotations from PDF files using Java][22]



[1]: #wavy-underline-dotnet-api
[2]: #add-wavy-underline-in-word
[3]: #wavy-underline-in-pdf-ppt-etc
[4]: https://products.groupdocs.com/annotation/
[5]: https://products.groupdocs.com/annotation/net/
[6]: https://downloads.groupdocs.com/annotation
[7]: https://www.nuget.org/packages/groupdocs.annotation
[8]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[9]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation
[10]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[11]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[12]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation
[15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels
[18]: https://docs.groupdocs.com/annotation/net
[19]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[20]: https://forum.groupdocs.com/
[21]: https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/
[22]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/

