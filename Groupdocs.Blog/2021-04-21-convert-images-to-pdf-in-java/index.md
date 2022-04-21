---
title: 'Convert Images to PDF in Java'
date: Wed, 21 Apr 2021 10:57:00 +0000
draft: false
url: /2021/04/21/convert-images-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "As PDF is the most common portable document format used to exchange files, there arises the requirement to convert documents as well as images to PDF format without losing the quality. In this article, we will learn to programmatically convert images to PDF format in Java."
tags: ['Convert Image to PDF in Java', 'Image Conversion Java API', 'Image to PDF in Java', 'JPG to PDF in Java', 'PNG to PDF in Java', 'WebP to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

As PDF is the most common portable document format used to exchange files, there arises the requirement to convert documents as well as images to PDF format without losing the quality. In this article, we will learn to programmatically convert JPG, PNG, GIF, and other images to PDF format using Java.



{{< figure align=center src="images/convert-images-to-pdf-in-java.jpg" alt="Convert Images to PDF using Java">}}


The following are the topics discussed briefly below:

*   [Image Conversion Java API][2]
*   [Convert JPG Image to PDF][3]
*   [Convert PNG, GIF, BMP Images to PDF][4]
*   [Image Conversion to PDF with Options][5]

## Image Conversion Java API {#java-image-conversion-api}

For the conversion of images and documents within your Java applications, GroupDocs offers native, specialized [GroupDocs.Conversion for Java][6] API. It allows converting whole documents, specific pages, applying rotations, watermarks even on password-protected files. The API has a long list of documents and images [supported file formats][7] that can be converted back and forth.

### Download and Configure

[Get the conversion library][8] from downloads or add the following pom.xml configuration in your Maven-based Java applications. After that, you can try examples of this article and many more available examples on [GitHub][9]. For the details, you may visit the [API Reference][10].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.4</version> 
</dependency>
```

## Convert JPG to PDF in Java {#jpg-to-pdf}



{{< figure align=center src="images/mount-everest.jpg" alt="Mountain JPG Image">}}


To convert images to PDF format, there is a simple way. Let's start with a JPG image and follow the steps to convert a JPG image to a PDF document.

*   Load the JPG image using the [Converter][11] class.
*   Convert the provided image to PDF using the [convert][12] method.
*   Get the converted PDF image from the location it was saved.

The following code sample shows how to convert a JPG image to PDF using Java in just 2 lines of code.

{{< gist GroupDocsGists d5a680abe2fd15a68e8ceca277e3b59c "ConvertJpgToPDF.java" >}}

## Convert PNG, GIF, BMP Images to PDF in Java {#png-gif-bmp-to-pdf}

The API is not restricted to just JPG images. It supports a wide range of image formats for their conversion to PDF in the same way. Whether it is PNG to PDF, GIF to PDF, BMP to PDF, or any other conversion, it can be performed likewise.

The following are the steps to convert any image to a PDF document.

*   Load any image using the [Converter][13] class.
*   Convert the provided image to PDF using the [convert][14] method.

The following code sample shows how to convert a PNG image to a PDF in the same way.

{{< gist GroupDocsGists d5a680abe2fd15a68e8ceca277e3b59c "ConvertImageToPDF.java" >}}

## Image to PDF Conversion in Java with Options {#image-to-pdf-advanced}

The following are the steps to convert images to a PDF document with some customizations as per requirement. You can adjust **margins**, **height**, **width**, **DPI**, apply **watermark**, and some other options while converting the images to PDF format.



{{< figure align=center src="images/image-to-pdf-with-watermark-and-margin.png" alt="Converted JPG to PDF">}}


*   Load the image using the [Converter][15] class.
*   Initialize the PDF Conversion Options using [PdfConvertOptions][16].
*   Set the margins, height, width using respective methods.
*   Apply watermark using [WatermarkOptions][17].
*   Convert the provided image to PDF with set options using the [convert][18] method.

The following code sample shows how to convert a JPG image to a PDF document using Java with options like; setting **margins**, specific **size**, apply **watermark** with **rotation** and **transparency**.

{{< gist GroupDocsGists d5a680abe2fd15a68e8ceca277e3b59c "ConvertImageToPdfAdv.java" >}}

## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][19] to use the API without evaluation limitations.

## Conclusion

In this article, you have learned how to convert the images to PDF format. Specifically, we discussed the conversion of JPG, PNG, BMP images to PDF using Java. Further, you have seen how to set margins, size, apply watermark while converting images PDF.

To explore more about the Java Conversion API, you can consult the [documentation][20]. For any queries, reach us via the [forum][21].

## See Also

*   [Convert Images to PDF using C#][22]
*   [Convert Spreadsheets (XLS, XLSX) to PDF in Java][23]







[1]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[2]: #java-image-conversion-api
[3]: #jpg-to-pdf
[4]: #png-gif-bmp-to-pdf
[5]: #image-to-pdf-advanced
[6]: https://products.groupdocs.com/conversion/java
[7]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[8]: https://downloads.groupdocs.com/conversion/java
[9]: https://github.com/groupdocs-conversion
[10]: https://apireference.groupdocs.com/conversion/java
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[15]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[19]: https://purchase.groupdocs.com/temporary-license
[20]: https://docs.groupdocs.com/conversion/
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[23]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/

