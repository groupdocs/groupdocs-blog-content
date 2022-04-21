---
title: 'Add or Remove Annotations or Markup PDF files using C#'
date: Tue, 25 Jan 2022 14:15:00 +0000
draft: false
url: /2022/01/25/annotate-pdf-files-using-csharp/
aliases:
    - /2019/11/20/add-arrow-annotation-in-a-pdf-file-using-csharp/
    - /2019/11/20/add-annotation-in-a-pdf-file-using-csharp/
author: 'Shoaib Khan'
summary: 'No more long discussions within long email threads on the content of the document(s). You can use annotations to markup documents with personalized messages and their replies. This article discussed **how to programmatically annotate PDF files to markup documents using C#**. Additionally, we will also discuss how to remove annotations from PDF files.'
tags: ['Add annotations in PDF', 'add annotations in PDF using csharp', 'annotate PDF', 'Annotate PDF in CSharp']
categories: ['GroupDocs.Annotation Product Family']
---

No more long discussions within long email threads about the content of the document(s). You can use annotations to markup documents with personalized messages and their replies. This article discusses **how to programmatically annotate PDF files to markup documents using C#**. Additionally, we will also discuss how to remove annotations from PDF files.

The following topics are discussed briefly below:

*   [.NET API to Annotate PDF Files](#dotnet-annotation-api)
*   [Add Annotations to PDF](#add-annotations-to-pdf)
    *   [Arrow annotations](#add-arrow-annotation)
    *   [Rectangle annotations](#add-area-annotation)
    *   [Ellipse or Oval annotations](#add-ellipse-annotation)
    *   [Distance annotations](#add-distance-annotation)
*   [Remove Annotations from PDF Files](#remove-annotations)

## .NET API to Annotate PDF Files {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) has its .NET API to work with the annotations within the documents and images. It allows you to add, remove, and extract annotations from PDF & Word documents, spreadsheets, and presentations. Furthermore, it supports images, webpages, email messages, Visio drawings, and much more. You can have a look at the documentation for the complete list of [supported document formats for annotation](https://docs.groupdocs.com/annotation/net/supported-document-formats/).

Download its **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/annotation) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.annotation). You may also use the following command from the Package Manager.

```
PM> Install-Package GroupDocs.Annotation
```

## Add Annotations to PDF using C# {#add-annotations-to-pdf}

There are many different types of annotations that are available to add within the documents, however, we will discuss only a few in this article.



{{< figure align=center src="images/added-annotations-to-pdf.jpg" alt="Added Annotations to PDF">}}


The following are some of the supported annotations. You may [learn about each annotation individually](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/).

<figure class="wp-block-table is-style-regular"><table><tbody><tr><td>- Area / Rectangle annotation<br>- Arrow<br>- Distance<br>- Ellipse<br>- Highlight<br>- Link<br>- Point<br>- Polyline</td><td>- Replacement<br>- Resource Redaction<br>- Strikeout<br>- Text Field<br>- Text Redaction<br>- Underline<br>- Watermark</td></tr></tbody></table></figure>

## Add Arrow Annotation to PDF using C# {#add-arrow-annotation}

The following are the steps for how to add arrow annotations to PDF documents in C#.



{{< figure align=center src="images/arrow-annotation.jpg" alt="Add Arrow Annotation Programmatically in Java and C# .NET">}}


*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.
*   Initialize the [Arrow Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation).
*   Define the position, size, page number of the arrow annotation.
*   Add the defined arrow annotation using the [Add](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index) method.
*   Save the annotated document using the appropriate [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method.

The following C# code sample shows how to add an arrow annotation to a PDF document.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "AddArrowAnnotationToPdf.cs" >}}

## Insert Rectangle or Area Annotation to PDF using C# {#add-area-annotation}

The following are the steps to add a rectangle or area annotation to a PDF document with some customizations. It is very similar to adding Arrow annotations but uses **AreaAnnotation**.

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.
*   Initialize the rectangle annotation using [AreaAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation) class.
*   Specify the position, size, and color of the rectangle.
*   You can also set other properties like **page number, background, opacity, style, pen width**, **messages**, and **time**.
*   Add the defined rectangle annotation to the Annotator.
*   Lastly, save the annotated file using the [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method.



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Add Rectangle or Area Annotation Programmatically in C# .NET and Java">}}


The following code sample adds rectangle/area annotation to a PDF document using C#.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "AddRectangleAnnotationToPdf.cs" >}}

## Add Oval or Ellipse Annotation to PDF using C# {#add-ellipse-annotation}

Likewise, let's add the ellipse/oval annotation. The following steps show how an oval annotation or ellipse annotation can be added to a PDF file using C#.



{{< figure align=center src="images/ellipses-annotation.jpg" alt="Add Ellipses or Oval Annotation Programatically in C# .NET and Java">}}


*   Load the PDF file using the [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.
*   Initialize the [Ellipse Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation).
*   Set the position, size, and other properties of the initialized annotation.
*   Add the created ellipse annotation to the Annotator object.
*   Use the [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method to save the annotated PDF file.

The following C# code example adds an oval/ellipse annotation to a PDF document.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "AddOvalAnnotationToPdf.cs" >}}

## Insert Distance Annotation to PDF using C# {#add-distance-annotation}

You can use distance annotation to point out the distance between two objects. The following are the steps that add distance annotation to the PDF document using C#.



{{< figure align=center src="images/distance-annotation.jpg" alt="Add Distance Annotation Programmatically in C# .NET and Java">}}


*   After loading the PDF document using [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class, initialize the distance annotation using [DistanceAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation) class.
*   Set the appearance, line color, thickness, style, etc.
*   Add the distance annotation to the Annotator.
*   Save the PDF file with the annotation using the appropriate [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method.

The following code snippet shows how to add the distance annotation within the PDF using C#.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "AddDistanceAnnotationToPdf.cs" >}}

## Remove Annotations from PDF files using C# {#remove-annotations}

There are different ways to remove annotations from PDF documents. Either, you can remove all the annotations at once, or you can provide IDs, indexes to remove the selective ones. We discussed the [different ways of removing annotations](https://blog.groupdocs.com/2022/01/27/remove-annotations-from-pdf-or-word-documents-using-csharp) in the separate article. However, here are the steps to remove all the annotations from a PDF file.

*   Load the document.
*   Initialize the [Save Options](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions).
*   Set the annotation types to **None**.
*   Save the annotation free PDF file using the [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method.

The following C# code shows how to remove annotations from PDF files.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "RemoveAnnotationsFromPdf.cs" >}}

## Conclusion

To conclude, you learned how to add different annotations to PDF documents within the .NET applications using C#. More precisely, we added arrow, ellipse, area, and distance annotations. Further, you have also seen one of the ways to remove all the annotations from any PDF file.

You can think to build your own document annotator .NET application. For more about the **GroupDocs.Annotation for .NET**, visit the [documentation](https://docs.groupdocs.com/annotation/net/) and the [GitHub](https://github.com/groupdocs-annotation) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/).

## See Also

*   [Create Hyperlinks in PDF using Annotations in C#](https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/)
*   [Highlight PDF using Annotations in C#](https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/)
*   [Add or Remove Annotations or Markup Word files using C#](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)




