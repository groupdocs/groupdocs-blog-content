---
title: 'Add Annotations in a PDF file using C#'
date: Wed, 20 Nov 2019 18:17:39 +0000
draft: false
url: /2019/11/20/add-annotation-in-a-pdf-file-using-csharp/
author: 'Atir Tahir'
summary: ''
tags: ['add annotations in PDF using csharp', 'annotations using csharp', 'Document annotation']
categories: ['GroupDocs.Annotation Product Family']
---

We are living in a paper-less era. Everything in business has gone digital. If you are given a document (e.g. PDF, Word, Presentation) and asked to brief the sales achieved in 2018. What will you do? You will try to highlight or add arrow to the concerned text.

## **Supported Annotations**

Following are the supported annotation types:

*   Area
*   Arrow
*   Distance
*   Ellipse
*   Link
*   Point

See full list of supported annotations in this [article](https://docs.groupdocs.com/display/annotationnet/Add+annotation+to+the+document) and list of supported file formats [here](https://docs.groupdocs.com/display/annotationnet/Supported+Document+Formats).

## **Insert** Annotation to PDF file using C#

In this post, we will see the implementation of arrow annotation in a PDF file. Arrow annotation draws an arrow on the document as shown in the picture below.



{{< figure align=center src="images/arrow-2.jpg" alt="Arrow Annotation in a PDF file using Java">}}


There is an ability to specify the next properties for **ArrowAnnotation** type:

*   Box - defines annotation position at document page
*   Opacity - allows to set annotation opacity
*   PenColor - defines frame color
*   PenStyle - defines frame line style (solid, dash, dot etc.)
*   PenWidth -  defines frame line width in pixels

{{< gist GroupDocsGists 30ab2737322332b12f18849e8eeb6040 "AddArrowAnnotationToPdf.cs" >}}

Download our open-source example [project](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET) to evaluate API features. If you face any issue, raise it on [forum](https://forum.groupdocs.com/c/annotation).




