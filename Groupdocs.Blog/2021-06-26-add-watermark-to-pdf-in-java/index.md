---
title: "Watermark PDF Files in Java"
seoTitle: "Add Watermark to PDF in Java | Text and Image Watermarks"
description: "Add image watermarks or apply text watermarks to PDF files in Java. Apply watermarks to all & selective pages of PDF using GroupDocs Watermarking Java API."
date: Sat, 26 Jun 2021 09:48:16 +0000
draft: false
url: /2021/06/26/add-watermark-to-pdf-in-java/
author: 'Shoaib Khan'
summary: 'Whether you want to apply branding to your documents or you want to protect our files from any illegal use, the watermark does the job for you. In this article, you will learn to programmatically add the watermarks to your PDF files using Java.'
tags: ['Image Watermark PDF in Java', 'Text Watermark PDF in Java', 'Watermark in Java', 'Watermark PDF in Java', 'Watermarking Java API']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-pdf-in-java.jpg" alt="Apply Watermark to PDF in Java">}}


Whether you want to apply branding to your documents or you want to protect the files from any illegal use, the watermark does the job for you. In this article, you will learn to programmatically add the watermarks to your PDF files using Java.

The following topics are covered below:

*   [Java Watermarking API][1]
*   [Apply Text Watermark to PDF][2]
*   [Apply Image Watermark to PDF][3]

## Watermarking API for Java {#java-watermarking-api}

[GroupDocs.Watermark for Java][4] is a watermarking API that allows working with text and image watermarks within the PDF files. Along with the PDF files, the API allows adding, removing, and extraction of watermarks for word-processing documents, spreadsheets, presentations, email messages, images, Visio drawings, and many other formats. From the [documentation][5], you may further check the features and [supported file formats][6].

### Download and Configure

Get the PDF watermarking library from the [downloads][7] section. For Maven-based Java applications, add the following configuration within pom.xml. Later, you can try the examples of this article as well as many more from [GitHub][8]. For the details, you may also visit the [API Reference][9].

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

## Add Text Watermark to PDF using Java {#text-watermark-to-pdf}

The text watermark can be applied to PDF files by adding the formatted text on either all the pages or any selective page on the set location.

The following steps show how to add text to PDF files as watermark.

*   Load the PDF document using [Watermarker][10] class.
*   Initialize the text watermark using [TextWatermark][11] class.
*   Set the appearance by changing rotation angle, x-y positions, opacity, foreground and background colors, etc.
*   Set the targetted page index (Optional). If you do not set the index, the watermark will be applied to all pages by default.
*   Add the text watermark to Watermarker.
*   Save the watermarked file using the appropriate [save][12] method.

The source code shows how to add text watermark to PDF files in Java.

{{< gist GroupDocsGists bd37f51efdd22e78fa9ff7e572060585 "TextWatermarkToPDF.java" >}}

The output of the above source code shows the text watermark on both the pages of the given PDF file.



{{< figure align=center src="images/text-watermark-to-pdf-in-java-1024x585.png" alt="Text Watermark to PDF">}}


## Add Image Watermark to PDF using Java {#image-watermark-to-pdf}

Similarly, you can add images to any PDF file at any location just like the text watermark options.

The following steps show how to add image to PDF files as watermark.

*   Load the PDF document using [Watermarker][13] class.
*   Initialize the image watermark using [ImageWatermark][14] class.
*   Set the appearance by adjusting the rotation angle, x-y positions, opacity, and other options.
*   Set the targetted page index. (Optional)
*   Add the image watermark to Watermarker.
*   Save the watermarked file using the appropriate [save][15] method.

The source code shows how to add image watermark to PDF files using Java.

{{< gist GroupDocsGists bd37f51efdd22e78fa9ff7e572060585 "ImageWatermarkToPDF.java" >}}

The output of the above source code shows the image watermark on the second page of the given PDF file.



{{< figure align=center src="images/image-watermark-to-pdf-in-java-1024x585.png" alt="Image Watermark to PDF">}}


## Get a Free API License

You can [get a free temporary license][16] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you learned to apply watermarks to PDF files using Java. We discussed adding text as well as images on PDF files as watermarks. For more details or learning about the API, visit [documentation][17]. For queries, contact us via the [forum][18].

## See Also

*   [Add Watermark to Images in Java][19]
*   [Watermark Excel Sheets in Java][20]
*   [Add Watermark to Presentations in Java][21]







[1]: #java-watermarking-api
[2]: #text-watermark-to-pdf
[3]: #image-watermark-to-pdf
[4]: https://products.groupdocs.com/watermark/java
[5]: https://docs.groupdocs.com/watermark/java/
[6]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/comparison/java
[8]: https://github.com/groupdocs-comparison
[9]: https://apireference.groupdocs.com/comparison/java
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/watermark/
[18]: https://forum.groupdocs.com/
[19]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[20]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[21]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/

