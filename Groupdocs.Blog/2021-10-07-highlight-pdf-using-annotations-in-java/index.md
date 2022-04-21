---
title: 'Highlight PDF using Annotations in Java'
date: Thu, 07 Oct 2021 10:35:00 +0000
draft: false
url: /2021/10/07/highlight-pdf-using-annotations-in-java/
aliases:
    - /2021/10/07/highlight-pdf-files-using-annotations-in-java/
author: 'Shoaib Khan'
summary: "It is often needed to highlight important areas of your documents on purpose. As a developer, you can automate highlighting within your applications. In this article, you will learn **how to highlight text and any area in PDF files using Java**. Additionally, there will be several properties of highlighting that can be adjusted according to the requirement."
tags: ['annotate PDF', 'Annotate PDF in Java', 'Highlight Annotation', 'Highlight PDF in Java', 'Highlight Text in PDF', 'Text Highlight']
categories: ['GroupDocs.Annotation Product Family']
---

It is often needed to highlight important areas of your documents on purpose. As a developer, you can automate highlighting within your applications. In this article, you will learn **how to highlight text and any area in PDF files using Java**. Additionally, there will be several properties of highlighting that can be adjusted according to the requirement.

The following topics are covered below:

*   [Java API to Highlight in PDF][1]
*   [How to Programmatically Highlight in PDF][2]



{{< figure align=center src="images/add-highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Highlight Text in PDF - Programmatically">}}


## Java API to Highlight in PDF {#highlight-pdf-java-api}

[GroupDocs.Annotation for Java][3] is the API that allows easy manipulation and automation of annotations in documents within your Java-based applications. We will use this API to highlight text in the PDF file.

### Download or Configure

You may download the **JAR** file from the [downloads section][4], or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

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

## Highlight in PDF using Java {#how-to-highlight-pdf}

The following are the steps to highlight text or any area in PDF using Java.

*   Load the PDF document using [Annotator][5] class.
*   Define list of [Point][6]s to select the area of highlight.
*   Create the [HighlightAnnotation][7] object.
*   Define the highlight properties like color, opacity, and page number.
*   Add the defined highlighting to the loaded PDF document using [add][8] method.
*   Save the annotated PDF using [save][9] method.

**Note:** You may change the highlight color, opacity, and other properties.

The following Java code shows how to highlight the text in PDF programmatically.

{{< gist GroupDocsGists b8061ef7e09f811300992f5e29b18a27 "HighlightPDF.java" >}}

Here is the output of the above code.



{{< figure align=center src="images/highlight-annotation-in-pdf-using-groupdocs.jpg" alt="Highlight Text in PDF - Programmatically">}}


## Get a Free API License

You can [get a free temporary license][10] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we have discussed how to programmatically add highlight annotation in PDF files using Java. Additionally, we can change the highlight color, opacity, and other properties with ease. Many [different types of annotations][11] are available through the API. These annotations can be added in a similar way using the same API. To learn about the API, visit the [documentation][12]. For queries, contact us via the [forum][13].

## See Also

*   [Highlight Annotations in PDF using C#][14]
*   [Add or Remove Annotations of PDF files in Java][15]
*   [Watermark PDF Files in Java][16]
*   [Add Watermark to Images in Java][17]







[1]: #highlight-pdf-java-api
[2]: #how-to-highlight-pdf
[3]: https://products.groupdocs.com/annotation/java/
[4]: https://downloads.groupdocs.com/redaction
[5]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#Annotator(java.io.InputStream)
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/Point
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/package-frame
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[17]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/

