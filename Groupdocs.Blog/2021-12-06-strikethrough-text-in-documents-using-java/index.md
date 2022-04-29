---
title: 'Strikethrough Text in Documents using Java'
seoTitle: "Strikethrough Text in Documents in Java | C̶r̶o̶s̶s̶ o̶u̶t̶ Text in Word, PDF"
description: "Let's strikeout the text within documents using Java. Automate the crossing out of invalid text using strikethrough annotation with Java API."
date: Mon, 06 Dec 2021 07:19:00 +0000
draft: false
url: /2021/12/06/strikethrough-text-in-documents-using-java/
author: 'Shoaib Khan'
summary: 'Probably you have some content that is no more valid. Let’s cross it out. Crossing out is one of the ways, used to highlight the invalid content within the documents. In order to automate the cross-out within the applications, this article shows how to strikethrough text in documents in Java.'
tags: ['Cross out Text', 'Cross out Text in Java', 'Strike through Text in Java', 'Strikeout Text', 'Strikethrough Text']
categories: ['GroupDocs.Annotation Product Family']
---



{{< figure align=center src="images/strikethrough-text-using-java.jpg" alt="StrikeThrough Text using Java">}}


Probably you have some content that is no more valid. Let's cross it out. Crossing out is one of the ways, used to highlight the invalid content within the documents. In order to automate the cross-out within the applications, this article shows **how to strikethrough text in documents in Java**.

The following topics are discussed in this article.

*   [Java API for Strikethrough Annotations][1]
*   [How to Strikeout Text in Documents][2]

## Java API to Strikethrough Text {#strikethrough-text-java-api}

[GroupDocs.Annotation][3] showcases Java API that supports various annotations that can be applied to multiple documents and images. We will use it in the examples of this article to cross out the selected text within the documents.

You can download the **JAR** file from the [downloads section][4] or use the latest repository and dependency [Maven][5] configurations within your Java applications.

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

## How to Strikethrough Text in Documents using Java {#how-to-strikethrough-text-using-java}

Let's cross out the area of the document that is not valid anymore. The following steps allow you to strike through the text within documents in Java.

*   Load the source document (PDF, Word, etc) using [Annotator][6] class.
*   Create and define the strikethrough annotation using [StrikeoutAnnotation][7] class.
    *   Set the line color for strikeout.
    *   Set opacity, document page number.
    *   Define Coordinates and other properties.
*   Add the prepared strikeout annotation to the annotator using [add()][8] method.
*   Finally, save the annotated document using the [save()][9] method.

Similarly, you can annotate Word documents, spreadsheets, presentations, PDF documents, web pages, email messages, and many other documents.

The following Java code example strikes out the selected text in a PDF document.

{{< gist GroupDocsGists d248b7146303cf285b8b51f6af40549b "StrikethroughText.java" >}}

## Get a Free API License

You can use [GroupDocs.Annotation for Java][10] for free by [getting a temporary license][11].

## Conclusion

To conclude, we discussed programmatically adding the cross-out annotation to documents within Java applications. Additionally, you can strike out the text within PDF files, spreadsheets, presentations, and Word documents. Likewise, you can also use other annotations as you like.

Learn more about **GroupDocs.Annotation for Java** from its [documentation][12]. Try building your own annotator for the [supported document formats][13]. Feel free to contact us for queries via the [forum][14].

## See Also

*   [Add or Remove Annotations from PDF files using Java][15]
*   [Highlight PDF Content in Java][16]
*   [Strikethrough Text in Documents using C#][17]







[1]: #strikethrough-text-java-api
[2]: #how-to-strikethrough-text-using-java
[3]: https://products.groupdocs.com/annotation/
[4]: https://downloads.groupdocs.com/viewer
[5]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/StrikeoutAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://products.groupdocs.com/annotation/java/
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/annotation/java/
[13]: https://docs.groupdocs.com/annotation/java/supported-document-formats/
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/10/07/highlight-pdf-using-annotations-in-java/
[17]: https://blog.groupdocs.com/2021/12/18/strikethrough-text-in-documents-using-csharp/

