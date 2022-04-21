---
title: 'Convert Presentations to Images in Java'
date: Tue, 18 Jan 2022 09:02:01 +0000
draft: false
url: /2022/01/18/convert-presentations-to-images-in-java/
author: 'Shoaib Khan'
summary: 'Welcome developer! you are hopefully here to programmatically convert some of your presentation slides to image formats. This could be needed when we want to share specific slide(s) as images or you want to create thumbnails from the presentations. In this article, you will learn **how to convert the PPT or PPTX presentation slides into JPG and PNG images** in Java.'
tags: ['Convert PPT', 'Convert PPT to JPG in Java', 'Convert PPT to PNG in Java', 'Convert PPTX', 'PPT to JPG in Java', 'PPT to PNG in Java']
categories: ['GroupDocs.Conversion Product Family']
---

Welcome developer! you are hopefully here to programmatically convert some of your presentation slides to image formats. This could be needed when we want to share specific slide(s) as images or you want to create thumbnails from the presentations. In this article, you will learn **how to convert the PPT or PPTX presentation slides into JPG and PNG images** in Java.



{{< figure align=center src="images/convert-ppt-to-jpg-png-image-in-java.jpg" alt="Convert PPT to JPG or PNG Image in Java">}}


The following topics are discussed here:

*   [Java API for Presentation Conversion](#ppt-convert-java-api)
*   [PPT/PPTX to JPG Image](#ppt-to-jpg)
*   [PPT/PPTX to PNG Image](#ppt-to-png)
*   [Convert to Image with Effects](#convert-to-image-with-effects)

## Java API to Convert Presentations {#ppt-convert-java-api}

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/) provides Java API that allows conversion of presentations to images. Today, we will use its [GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/net/) to convert the presentations of PPT & PPTX formats to JPG and PNG images. The API further supports many other conversions word-processing documents, spreadsheets, presentations, eBooks, images, and more that are mentioned in the [documentation](https://docs.groupdocs.com/conversion/java/supported-document-formats/).

### Download or Configure

You may download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/conversion), or just get the repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.10.1</version> 
</dependency>
```

## Convert Presentation to JPG Image in Java {#ppt-to-jpg}

Let's achieve the objective by transforming the presentation to JPG image format. The following steps guide how to convert the Powerpoint PPT/PPTX to JPG image format in Java.

*   Load the presentation using the [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) class.
*   Prepare the [Image Convert Options](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
*   Define the conversion file format as **JPG**.
*   Provide the slide number to convert.
*   Convert the presentation slide to JPG image using the **convert()** method.

The following Java source code converts the PowerPoint presentation to JPG format.

{{< gist GroupDocsGists 0e4392fdb047439a38f81bb75f563351 "ConvertPptToJpg.java" >}}

## Convert Presentation to PNG Image in Java {#ppt-to-png}

Similarly, you can convert to other popular image formats like PNG. Let's convert any slide of the presentation to PNG. The following steps show how to convert the PPT/PPTX presentation slide to PNG image format in Java.

*   Load the presentation file using [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) class.
*   Prepare the [Image Convert Options](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
*   Set the conversion file format as **PNG**.
*   Define the selected slides number to convert.
*   Convert the slide to PNG image using the **convert()** method.

The following Java source code example converts the PowerPoint presentation to PNG format.

{{< gist GroupDocsGists 0e4392fdb047439a38f81bb75f563351 "ConvertPptToPng.java" >}}

## Convert to Image with Effects {#convert-to-image-with-effects}

While converting the slides you can apply many variations to the output image file. You can learn more from any of the following articles:

*   [Convert to Image with Advanced Options in Java](https://blog.groupdocs.com/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/)
*   [API documentation for Advanced Image Conversion](https://docs.groupdocs.com/conversion/java/convert-to-image-with-advanced-options/)

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To conclude we learned how presentation slides can be converted to JPG and PNG Images in Java. To build your conversion applications, you may learn more from the [documentation](https://docs.groupdocs.com/conversion/java/) and from the running examples on [GitHub](https://github.com/groupdocs-conversion). Contact us for any query via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Convert Presentations to PDF in Java](https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/)
*   [Convert Images to PDF in Java](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)
*   [Excel Spreadsheets to PDF Conversion in Java](https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/)




