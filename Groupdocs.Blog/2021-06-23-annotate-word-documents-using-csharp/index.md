---
title: 'Add or Remove Annotations or Markup Word files using C#'
date: Wed, 23 Jun 2021 11:23:00 +0000
draft: false
url: /2021/06/23/annotate-word-documents-using-csharp/
aliases:
    - /2021/06/24/annotate-documents-programmatically-using-groupdocs.annotation-for-.net/
    - /2019/10/14/annotate-documents-programmatically-using-groupdocs.annotation-for-.net/
author: 'Shoaib Khan'
summary: 'Forget to discuss documents content and feedbacks in long email threads. Simply use annotations to markup documents with messages and replies. In this article, you will learn how to programmatically add and remove annotations to markup Word documents in C# with your .NET applications.

The following topics are discussed in this article:

*   .NET API for Word DOC/DOCX Annotations
*   Add Annotations to Word
    *   Arrow annotations
    *   Rectangle annotations
    *   Ellipse or Oval annotations
    *   Distance annotations
*   Remove Annotations from Word Files'
tags: ['Add Annotations in Word using CSharp', 'Annotate Word in CSharp', 'Remove Annotations from Word in C#']
categories: ['GroupDocs.Annotation Product Family']
---

Forget to discuss documents' content and feedback in long email threads. Simply use annotations to markup documents with messages and replies. In this article, you will learn how to programmatically add and remove annotations to markup Word documents in C# with your .NET applications.

The following are the topics discussed briefly below:

*   [.NET API for Word DOC/DOCX Annotations][1]
*   [Add Annotations to Word][2]
    *   [Arrow annotations][3]
    *   [Rectangle annotations][4]
    *   [Ellipse or Oval annotations][5]
    *   [Distance annotations][6]
*   [Remove Annotations from Word Files][7]

## .NET API to Annotate and Markup Word Files {#dotnet-annotation-api}

[GroupDocs.Annotation][8] provides the .NET API to work with the annotations for your documents and images within your .NET applications. The API allows you to add, remove, and extract annotations from Word documents. Furthermore, it supports spreadsheets, presentations, images, PDF files, webpages, email messages, Visio drawings. Some AutoCAD drawings and digital imaging formats like DICOM are also on the list. For the complete list of [supported document formats for annotation][9], you can visit the documentation.

Download the **DLLs** or **MSI** installer from the [downloads section][10] or install the API in your .NET application via [NuGet][11]. You may also use the following command from the Package Manager.

```
PM> Install-Package GroupDocs.Annotation
```

## Add Annotations to Word in C# {#add-annotations-to-word}

Let's add some of the different kinds of annotations to the Word documents. There are many different types of annotation, so we will be covering only a few in this article.



{{< figure align=center src="images/add-annotations-to-doc-docx-using-groupdocs-dotnet-java-api-1024x624.png" alt="Add Annotations to DOC DOCX using GroupDocs API">}}


There are some of the supported annotation types, you may [learn about each annotation individually][12].

*   Area / Rectangle annotation
*   Arrow
*   Underline
*   Watermark
*   Distance
*   Strikeout
*   Text Field
*   Ellipse
*   Highlight
*   Link
*   Point
*   Polyline
*   Replacement
*   Resource Redaction
*   Text Redaction

## Add Arrow Annotation to Word using C# {#add-arrow-annotation}

The following are the steps to add arrow annotation to a Word document in C#.



{{< figure align=center src="images/arrow-annotation.jpg" alt="Add Arrow Annotation Programmatically in Java and .NET">}}


*   Load the document using the [Annotator][13] class.
*   Initialize arrow annotation with [ArrowAnnotation][14] class.
*   Adjust the position, size, page number of the arrow annotation.
*   Add the created arrow annotation using [Add][15] method.
*   Save the annotated Word document to the path using the [Save][16] method.

The following code sample shows how to add an arrow annotation to a Word document using C#.

{{< gist GroupDocsGists 8b7eabe47e6268c246f47e8fb58529f5 "AddArrowAnnotationToWord.cs" >}}

## Insert Rectangle or Area Annotation to Word using C# {#add-area-annotation}

Customizations can be done for any annotation while adding it to the document. The following are the steps to add rectangle or area annotation to a DOC/DOCX document with some customizations. It is very similar to adding Arrow annotations but uses **AreaAnnotation** class this time.

*   Load the DOC/DOCX document using the [Annotator][17] class.
*   Initialize rectangle annotation using [AreaAnnotation][18] class.
*   Adjust the position, size, and color of the rectangle.
*   Set other properties like **page number, background, opacity, style, pen width**, **messages**, and **time**.
*   Add the created rectangle annotation to the Annotator.
*   Save the annotated file to the path using the [Save][19] method.



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Add Rectangle or Area Annotation Programmatically in .NET and Java">}}


The following code sample shows how to add rectangle/area annotation to a Word document using C#.

{{< gist GroupDocsGists 8b7eabe47e6268c246f47e8fb58529f5 "AddRectangleAnnotationToWord.cs" >}}

## Add Oval or Ellipse Annotation to Word using C# {#add-ellipse-annotation}

The following are the steps to add oval annotation or ellipse annotation to a document in C#.



{{< figure align=center src="images/ellipses-annotation.jpg" alt="Add Ellipses or Oval Annotation Programatically in C# .NET and Java">}}


*   Load the DOC/DOCX document using the [Annotator][20] class.
*   Initialize ellipse annotation using [EllipseAnnotation][21] class.
*   Set the position and size of the initialized ellipse annotation.
*   Add the created ellipse annotation to the Annotator object.
*   Provide the path and save the annotated Word file using the [Save][22] method.

The following code sample shows how to add oval or ellipse annotation to a Word document using C#.

{{< gist GroupDocsGists 8b7eabe47e6268c246f47e8fb58529f5 "AddOvalAnnotationToWord.cs" >}}

## Insert Distance Annotation to Word using C# {#add-distance-annotation}

Similarly, you can add the distance annotation to mark the distance between two points. The following are the steps to add distance annotation to the document.



{{< figure align=center src="images/distance-annotation.jpg" alt="Add Distance Annotation Programmatically in C# .NET and Java">}}


*   After loading the Word document, initialize distance annotation using [DistanceAnnotation][23] class.
*   Set the appearance of the annotation.
*   Add the distance annotation to the Annotator object.
*   Save the annotated Word files at the given location by specifying the path.

The following code sample shows how to add distance annotation to a DOC/DOCX document using C#.

{{< gist GroupDocsGists 8b7eabe47e6268c246f47e8fb58529f5 "AddDistanceAnnotationToWord.cs" >}}

## Complete Code

To sum up, here is the complete code with the output showing all the added **annotations** and **messages** with **replies**. The following C# code below adds, arrow, rectangle, ellipse, distance annotations, messages, and replies to a Word file.

{{< gist GroupDocsGists 8b7eabe47e6268c246f47e8fb58529f5 "AddAnnotationsToWord.cs" >}}

## Remove Annotations from Word DOC/DOCX files using C# {#remove-annotations}

Annotations from the documents can be removed easily. There are many options to remove the annotations from a Word document. You can remove all the annotations at once. Additionally, you can provide the indexes to remove the specific annotations. For more options, visit the [documentation][24] article.

The following are the steps to remove all the annotations from a Word file.

*   Load the document.
*   Initialize saving options using [SaveOptions][25] class.
*   Set the annotation types to None.
*   Save the Word file. It will have no annotation in it.

The following code shows how to remove annotations from a Word file using C#.

{{< gist GroupDocsGists 8b7eabe47e6268c246f47e8fb58529f5 "RemoveAnnotationsFromWord.cs" >}}

## Conclusion

In short, you have learned how to add annotations to Word documents within .NET applications using C#. Specifically, we added arrow, ellipse, area, and distance annotations to the Word DOC/DOCX file. Further, you have also seen how to remove all the annotations from any Word file. Now, you can think to build your own document annotator .NET application.

Learn more about GroupDocs.Annotation for .NET from the [documentation][26] and the [GitHub][27] repository. For further queries, contact the support on the [forum][28].

## See Also

*   [Add Watermark to Images using C#][29]
*   [Annotate PDF files in Java][30]







[1]: #dotnet-annotation-api
[2]: #add-annotations-to-word
[3]: #add-arrow-annotation
[4]: #add-area-annotation
[5]: #add-ellipse-annotation
[6]: #add-distance-annotation
[7]: #remove-annotations
[8]: https://products.groupdocs.com/annotation/
[9]: https://docs.groupdocs.com/annotation/net/supported-document-formats/
[10]: https://downloads.groupdocs.com/annotation
[11]: https://www.nuget.org/packages/groupdocs.annotation
[12]: https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/
[13]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[14]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation
[15]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add/index
[16]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[17]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[18]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation
[19]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[20]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator
[21]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/ellipseannotation
[22]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index
[23]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/distanceannotation
[24]: https://docs.groupdocs.com/annotation/net/remove-annotation-from-document/
[25]: https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions
[26]: https://docs.groupdocs.com/annotation/net/
[27]: https://github.com/groupdocs-annotation
[28]: https://forum.groupdocs.com/
[29]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[30]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/

