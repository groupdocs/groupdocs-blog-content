---
title: 'Add or Remove Annotations or Markup Word files in Java'
date: Sat, 19 Mar 2022 15:42:43 +0000
draft: false
url: /2022/03/19/annotate-word-documents-in-java/
author: 'Shoaib Khan'
summary: 'Annotations are normally used to mentioned errors in documents or to discuss their content. With annotations, you can avoid long and never-ending discussions within emails threads. In this article, you will learn how to programmatically add and remove annotations to markup Word documents in Java.'
tags: ['Add Annotations in Java', 'Add Annotations in Word using Java', 'Annotate Word in Java', 'Annotations in Java', 'Remove Annotation from Word in Java']
categories: ['GroupDocs.Annotation Product Family']
---

Annotations are normally used to mentioned errors in documents or to discuss their content. With annotations, you can avoid long and never-ending discussions within emails threads. In this article, you will learn how to programmatically add and remove annotations to markup Word documents in Java.

The following are the topics discussed briefly below:

*   [Java API for Word DOC/DOCX Annotations](#java-annotation-api)
*   [Add Annotations to Word](#add-annotations-to-word)
    *   [Arrow annotations](#add-arrow-annotation)
    *   [Rectangle annotations](#add-area-annotation)
    *   [Ellipse or Oval annotations](#add-ellipse-annotation)
    *   [Distance annotations](#add-distance-annotation)
*   [Remove Annotations from Word Files](#remove-annotations)

## Java API to Annotate and Markup Word Files {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) provides the Java API to deal with the annotations. The API allows the addition, removal, and extraction of annotations from Word documents and many other file formats. [Supported document formats](https://docs.groupdocs.com/annotation/java/supported-document-formats/) include; spreadsheets, presentations, images, PDF files, webpages, email messages, Visio drawings.

### Download or Configure

Download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/annotation), or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7.2</version> 
</dependency>
```

## Add Annotations to Word in Java {#add-annotations-to-word}

Let's add different types of annotations to the Word documents. Annotations are of many types, so we will be covering only a few here.

{{< figure align=center src="images/add-annotations-to-doc-docx-using-groupdocs-dotnet-java-api-1024x624.png" alt="Add Annotations to DOC DOCX using GroupDocs API">}}

## Add Arrow Annotation to Word in Java {#add-arrow-annotation}

The following are the steps to add an arrow annotation to a Word document in Java.

*   Load the document using the [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) class.
*   Initialize arrow annotation with [ArrowAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation) class.
*   Adjust the position, size, page number of the arrow annotation.
*   Add the created arrow annotation using the add() method.
*   Save the annotated Word document to the path using appropriate save() method.

The following Java code sample shows how to add an arrow annotation to a Word document.

{{< gist GroupDocsGists e7fb039edd9b4a84b04b94ae117179dc "AddArrowAnnotationToWord.java" >}}

{{< figure align=center src="images/arrow-annotation.jpg" alt="Add Arrow Annotation Programmatically in Java and .NET">}}

## Insert Rectangle or Area Annotation to Word in Java {#add-area-annotation}

The following are the steps to add rectangle or area annotation to a DOC/DOCX document with some customizations. It is similar to adding Arrow annotations but it uses **AreaAnnotation**.

*   Load the Word DOC/DOCX document using the [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) class.
*   Initialize rectangle annotation using [AreaAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation) class.
*   Adjust the position, size, and color of the rectangle.
*   Set other properties like **page number, background, opacity, style, pen width**, **messages**, and **time**.
*   Add the created rectangle annotation to the Annotator.
*   Save the annotated Word document to the path using the save() method.

The following Java code sample shows how to add rectangle/area annotation to a Word document.

{{< gist GroupDocsGists e7fb039edd9b4a84b04b94ae117179dc "AddRectangleAnnotationToWord.java" >}}

{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="Add Rectangle or Area Annotation Programmatically in .NET and Java">}}

## Add Oval or Ellipse Annotation to Word in Java {#add-ellipse-annotation}

The following are the steps to add oval/ellipse annotation to a document in Java.

*   Load the DOC/DOCX document using the [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) class.
*   Initialize ellipse annotation using [EllipseAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/EllipseAnnotation) class.
*   Set the position and size of the initialized ellipse annotation.
*   Add the created ellipse annotation to the Annotator.
*   Save the annotated Word file using the appropriate save() method.

The following Java code sample shows how to add oval/ellipse annotation to any Word document.

{{< gist GroupDocsGists e7fb039edd9b4a84b04b94ae117179dc "AddOvalAnnotationToWord.java" >}}

{{< figure align=center src="images/ellipses-annotation.jpg" alt="Add Ellipses or Oval Annotation Programatically in C# .NET and Java">}}

## Insert Distance Annotation to Word in Java {#add-distance-annotation}

Likewise, you can mention the distance between two points using the distance annotation. The following are the steps to add distance annotation to the document in Java.

*   After loading the Word document, initialize distance annotation using [DistanceAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation) class.
*   Set the appearance of the annotation.
*   Add the distance annotation to the Annotator object.
*   Save the annotated document at the given location or use the right save() mehod,

The following Java code sample shows how to add distance annotation to a DOC/DOCX document.

{{< gist GroupDocsGists e7fb039edd9b4a84b04b94ae117179dc "AddDistanceAnnotationToWord.java" >}}

{{< figure align=center src="images/distance-annotation.jpg" alt="Add Distance Annotation Programmatically in C# .NET and Java">}}

## Remove Annotations from Word DOC/DOCX files in Java {#remove-annotations}

There are many ways to remove annotations from Word documents. You can remove specific annotations by providing the indexes to remove the specific annotations. Additionally, you can remove all the annotations at once. Details and Java source code for removing annotations are discussed in a separate article.

The following are the steps to remove all the annotations from a Word file.

*   Load the document.
*   Initialize [saving options](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions).
*   Set the [annotation type](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/AnnotationType) to None.
*   Save the Word file. It will be free of annotations.

The following code shows how to remove annotations from a Word file in Java.

{{< gist GroupDocsGists e7fb039edd9b4a84b04b94ae117179dc "RemoveAnnotationsFromWord.java" >}}

## Conclusion

To sum up, you have learned how to add annotations to Word documents within Java applications. Specifically, we added arrow, ellipse, area, and distance annotations to the Word DOC/DOCX file using [GroupDocs.Annotation for Java](https://products.groupdocs.com/annotation/java/). Further, you have also seen how to remove all the annotations from any Word file. Now, you can try building your own document annotator Java application.

Learn more about the API from the [documentation](https://docs.groupdocs.com/annotation/java/) and the [GitHub](https://github.com/groupdocs-annotation) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/).

## See Also

*   [Annotate PDF files in Java](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)
*   [Render Word documents as Minified HTML in Java](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)
*   [Remove Annotations from PDF or Word Documents in Java](https://blog.groupdocs.com/2022/03/12/remove-annotations-from-pdf-or-word-documents-in-java/)