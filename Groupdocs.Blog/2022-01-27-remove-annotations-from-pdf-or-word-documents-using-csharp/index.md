---
title: 'Remove Annotations from PDF or Word Documents using C#'
date: Thu, 27 Jan 2022 14:29:00 +0000
draft: false
url: /2022/01/27/remove-annotations-from-pdf-or-word-documents-using-csharp/
author: 'Shoaib Khan'
summary: 'Annotations are commonly used in documents for pointing out different observations and providing feedbacks for discussion. We discussed in a separate articles, [how to add different annotations to PDF](https://blog.groupdocs.com/2022/01/25/annotate-pdf-files-using-csharp) and [Word documents](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/) using C#. Today, this article discuss **how to remove annotations from documents like PDF and Word DOC/DOCX files using C#**.'
tags: ['Remove Annotation from PDF in CSharp', 'Remove Annotation in CSharp', 'Remove Annotations', 'Remove Annotations from Word in C#']
categories: ['GroupDocs.Annotation Product Family']
---

Annotations are commonly used in documents for pointing out different observations and providing feedback for discussion. We discussed in separate articles, how to add different annotations to PDF and Word documents using C#. Today, this article discusses **how to remove annotations from documents like PDF and Word DOC/DOCX files using C#**.

The following topics are discussed below:

*   [Annotation .NET API](#dotnet-annotation-api)
*   [Remove All Annotations](#remove-all-annotations)
*   [Remove Annotations by IDs](#remove-annotation-by-id)
*   [Eliminate Annotations by Annotation Object](#remove-annotations-by-obj)

## .NET API for Annotations {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) provides the .NET API to deal with annotations within various documents and images. It allows adding, removal, and extraction of annotations from PDF, Word, and many other documents. You can have a look at the documentation for the complete list of [supported document formats for annotation](https://docs.groupdocs.com/annotation/net/supported-document-formats/).

Download its **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/annotation) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.annotation). You may also use the following command from the Package Manager.

```
PM> Install-Package GroupDocs.Annotation
```

## Remove All Annotations from PDF, Word documents using C# {#remove-all-annotations}

There are various ways to remove annotations from documents. You can remove all the annotations at once, remove specific annotation(s) by providing ID(s), or remove specific annotation by annotation object. For more options, visit the [documentation](https://docs.groupdocs.com/annotation/net/remove-annotation-from-document/) article.

The following are the steps to remove all the annotations from PDF or Word DOC/DOCX document(s) using C#.

*   Load the document using [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator).
*   Initialize [Saving Options](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions) class.
*   Set the annotation type to **None**.
*   Save the file, free of annotations using the [Save()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method.

The following code shows how to remove annotations from PDF or Word files using C#.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "RemoveAnnotationsFromPdf.cs" >}}

## Remove Annotation by IDs using C# {#remove-annotation-by-id}

Similarly, you can provide annotation ID(s) to eliminate these annotations from the document. Just provide the ID or list of IDs to get rid of the specified annotation. The following code shows how to remove the annotation(s) from PDF or Word documents by providing the ID(s) using C#.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "RemoveAnnotationsbyIdsFromPdf.cs" >}}

## Remove Annotation by Annotation Object using C# {#remove-annotations-by-obj}

You can also get rid of the specific annotation by proving the Annotation object. In order to show this, the following code example removes the annotation(s) from PDF or Word documents by using annotation objects in C#.

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "RemoveAnnotationsbyAnnotationFromPdf.cs" >}}

## Conclusion

To conclude, you have learned how to remove annotations from the documents using C#. Specifically, we removed all the annotations from PDF & Word files. Later we removed annotations by providing IDs and also by proving the annotation objects.

Build your own document annotation remover .NET application using **GroupDocs.Annotation for .NET**. Learn more about the API from the [documentation](https://docs.groupdocs.com/annotation/net/) and the [GitHub](https://github.com/groupdocs-annotation) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/).

## See Also

*   [Annotate or Markup PDF files using C#](https://blog.groupdocs.com/2022/01/25/annotate-pdf-files-using-csharp/)
*   [Annotate or Markup Word files using C#](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)
*   [Highlight PDF using Annotations in C#](https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/)
*   [Create Hyperlinks in PDF using Annotations in C#](https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/)




