---
title: "Watermark Presentation Slides using Java"
seoTitle: "Add Watermark to Presentations in Java | Text and Image Watermarks"
description: "Add image watermark to presentation slides, or apply text watermarks to PPT, PPTX, PPS & more formats in Java using GroupDocs Watermarking API."
date: Wed, 09 Jun 2021 17:36:49 +0000
draft: false
url: /2021/06/09/watermark-presentation-slides-using-java/
author: 'Shoaib Khan'
summary: "For the protection of the documents and presentations from illegal use, we can use watermarking. In this article, we will learn to programmatically apply text and image-based watermarks to the presentations or specific slides of a presentation in Java. In another post, we have discussed [applying watermarks to presentations using C#][1]."
tags: ['Add Watermark to Presentation in Java', 'Image Watermark to PPT in Java', 'Text Watermark to PPT in Java', 'Watermark PPT in Java', 'Watermark PPTX in Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-presentations-in-java.jpg" alt="Apply Watermark to Presentation in Java">}}


For the protection of the documents and presentations from illegal use, we can use watermarking. In this article, we will learn to programmatically apply text and image-based watermarks to the presentations or specific slides of a presentation in Java. In another post, we have discussed [applying watermarks to presentations using C#][2].

The following topics will be covered below:

*   [Java Watermarking API][3]
*   [Add text watermarks to presentation slides][4]
*   [Add image watermarks to presentation slides][5]

## Java Watermarking API for Presentations {#java-watermarking-api}

[GroupDocs.Watermark][6] provides the Java API for watermarking, which allows adding text and image watermarks to the presentations within your application.

Alongside the presentations, the API supports adding, removing, and extracting watermarks from word-processing documents, spreadsheets, email messages, PDF files, images, and many other formats.

Among presentation file formats, it supports [PPT][7], [PPTX][8], [PPS][9], [PPTM][10], [PPSX][11], and others. From the [documentation][12], you may further check the features and [supported file formats][13].

### Download and Configure

You can get the watermarking library from the [downloads section][14]. For Maven-based Java applications, just add the following pom.xml configuration. Afterward, you can try watermarking examples of this article as well as many more examples from [GitHub][15]. For the details, you may visit the [API Reference][16].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## Add Text Watermark to Presentation Slides in Java {#text-watermark-to-slides}

Using the API, you can apply customizations while adding text to presentation slides as a watermark. The following steps show how to apply watermark to presentations within the Java application.

*   Load the presentation using [Watermarker][17].
*   Set watermark text and style using [TextWatermark][18].
*   Set watermark properties like size, location, opacity, rotation, and color.
*   Provide the slide index on which to apply the watermark. _(Optional)_
*   Add the formatted text watermark using the [add][19] method.
*   Save the watermarked presentation by calling the [save][20] method.

The following code sample shows how to add a text watermark in PPT or PPTX on all the slides with rotation using Java.

{{< gist GroupDocsGists 9a6c523f3245fc7029a35217c15a1b97 "TextWatermarkToPresentation.java" >}}

If the slide index is not set, the watermark will be applied to all the slides of the presentation by default. The above code also shows how to mention the slide index. The following is the output with a text watermark on all the slides of the PPTX presentation.



{{< figure align=center src="images/text-watermark-to-slide-in-Java.png" alt="Text Watermark to Presentation Slide">}}


## Add Image Watermark to PPT Slides using Java {#image-watermark-to-slides}

You can add image watermarks on the presentation files as well with a similar approach. Just use the [ImageWatermark][21] class instead of the TextWatermark.

The following steps guide how to add image watermark to presentation slides within your Java applications.

*   Load the presentation file using [Watermarker][22].
*   Load the image, logo, or photo using [ImageWatermark][23]. It will be used as an image watermark.
*   Set image watermark properties like rotation, size, opacity, color, and position.
*   Set the slide index on which the watermark will be applied.
*   Add the image watermark to the presentation using [add][24] method.
*   Save the presentation with the image watermark using [save][25] method.

The following code sample adds an image watermark to the second slide of the PPTX presentation in Java.

{{< gist GroupDocsGists 9a6c523f3245fc7029a35217c15a1b97 "ImageWatermarkToPresentation.java" >}}

The following is the output of the code with an image watermark only on the second slide of the PPT/PPTX.



{{< figure align=center src="images/image-watermark-to-slide-in-Java.png" alt="Image Watermark to Presentation Slide">}}


## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][26] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you have learned how to add watermarks to presentations in Java. To be more precise, we discussed how to insert text watermarks as well as image watermarks in presentations within Java-based applications. You can apply watermarks to all the slides as well as to any specific slide of the presentations.

Learn more about the API using [documentation][27]. Examples are available at [GitHub][28]. For queries, contact us via the [forum][29].

## See Also

*   [Watermark Excel Sheets in Java][30]
*   [Add Watermark to Images and Photos in Java][31]
*   [Find and Remove Watermarks from Documents in Java][32]
*   [Watermark Presentation Slides using C#][33]







[1]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[2]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[3]: #java-watermarking-api
[4]: #text-watermark-to-slides
[5]: #image-watermark-to-slides
[6]: https://products.groupdocs.com/watermark/
[7]: https://docs.fileformat.com/presentation/ppt/
[8]: https://docs.fileformat.com/presentation/pptx/
[9]: https://docs.fileformat.com/presentation/pps/
[10]: https://docs.fileformat.com/presentation/pptm/
[11]: https://docs.fileformat.com/presentation/ppsx/
[12]: https://docs.groupdocs.com/watermark/java/
[13]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[14]: https://downloads.groupdocs.com/watermark
[15]: https://github.com/groupdocs-watermark
[16]: https://apireference.groupdocs.com/conversion/java
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[19]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[20]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[21]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[22]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[23]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[24]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[25]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String,%20com.groupdocs.watermark.options.SaveOptions)
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/watermark/
[28]: https://github.com/groupdocs-watermark
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[31]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[32]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[33]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/

