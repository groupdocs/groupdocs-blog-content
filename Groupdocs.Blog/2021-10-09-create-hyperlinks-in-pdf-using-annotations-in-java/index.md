---
title: 'Create Hyperlinks in PDF using Annotations in Java'
date: Sat, 09 Oct 2021 15:29:53 +0000
draft: false
url: /2021/10/09/create-hyperlinks-in-pdf-using-annotations-in-java/
author: 'Shoaib Khan'
summary: 'Link annotations are used to create any part of the document as hyperlink. In other words, it allows us to associate external data with the specified area of the document. We can add these link annotations to documents within Java applications. In this article, you will learn **how to create hyperlinks in PDF files using Java**.

The following topics are covered in this article:

*   Java API to Add Hyperlinks in PDF files
*   How to Programmatically Create Hyperlinks in PDF'
tags: ['annotate PDF', 'Annotate PDF in Java', 'Create Hyperlink in PDF', 'Link Annotation', 'Link Annotation in Java', 'Link Annotation in PDF']
categories: ['GroupDocs.Annotation Product Family']
---

Link annotations are used to create any part of the document as hyperlinks. In other words, it allows us to associate external data with the specified area of the document. We can add these link annotations to documents within Java applications. In this article, you will learn **how to create hyperlinks in PDF files using Java**.

The following topics are covered below:

*   [Java API to Add Hyperlinks in PDF files][1]
*   [How to Programmatically Create Hyperlinks in PDF][2]



{{< figure align=center src="images/add-link-annotation-in-pdf-using-groupdocs.jpg" alt="Create Link in PDF - Programmatically">}}


## Java API to Create Hyperlinks in PDF {#hyperlink-java-api}

[GroupDocs.Annotation][3] provides the Java API that allows manipulation and automation of various annotations in documents within your Java-based applications. We will use this API to create hyperlink annotation in the PDF file.

### Download or Configure

Download the **JAR** file from the [downloads section][4], or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7</version> 
</dependency>
```

## Create Hyperlinks in PDF using Java {#how-to-create-hyperlinks-annotations}

The following are the steps to create hyperlinks anywhere in PDF using Java.

*   Load the PDF document using [Annotator][5] class.
*   Define list of [Points][6] that represent the area of Hyperlink.
*   Create the [LinkAnnotation][7] object.
*   Define the hyperlink properties like url, page number, points, etc.
*   Add the defined hyperlink to the loaded PDF document using [add][8] method.
*   Save the annotated PDF using [save][9] method.

The following Java code shows how to convert any part of the PDF file into a hyperlink programmatically.

{{< gist GroupDocsGists b8061ef7e09f811300992f5e29b18a27 "AddHyperlinkInPDF.java" >}}

The following is the output of the above code.



{{< figure align=center src="images/link-annotation-in-pdf-using-groupdocs.jpg" alt="Create Link in PDF - Programmatically">}}


## Get a Free API License

You can [get a free temporary license][10] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we have discussed how to programmatically add link annotations to create hyperlinks in PDF files using Java. By using link annotations, you can modify any part of the document into hyperlinks. Many [different types of annotations][11] are available through the API. These annotations can be added in a similar way using the same API. To learn more about the API, visit the [documentation][12]. For queries, contact us via the [forum][13].

## See Also

*   [Hyperlink Annotations in PDF using C#][14]
*   [Add or Remove Annotations of PDF files in Java][15]
*   [Highlight PDF using Annotations in Java][16]
*   [Add Watermark to Images in Java][17]







[1]: #hyperlink-java-api
[2]: #how-to-create-hyperlinks-annotations
[3]: https://products.groupdocs.com/annotation/java/
[4]: https://downloads.groupdocs.com/redaction
[5]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#Annotator(java.io.InputStream)
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/Point
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/LinkAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/package-frame
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/10/07/highlight-pdf-files-using-annotations-in-java/
[17]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/

