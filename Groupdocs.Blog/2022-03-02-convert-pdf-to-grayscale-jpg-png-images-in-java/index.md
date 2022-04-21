---
title: 'Convert PDF to Grayscale in Java'
date: Wed, 02 Mar 2022 15:53:00 +0000
draft: false
url: /2022/03/02/convert-pdf-to-grayscale-jpg-png-images-in-java/
author: 'Shoaib Khan'
summary: 'Almost any document or image format (including images) can be converted to a black-and-white or grayscale monochrome image. In this article, we will discuss how to convert color PDF documents to **grayscale JPG and PNG image formats in Java**.'
tags: ['convert document to image', 'convert to grayscale', 'Convert to Grayscale in Java', 'PDF to Grayscale', 'PDF to Grayscale in Java', 'PDF to JPG Grayscale', 'PDF to PNG Grayscale']
categories: ['GroupDocs.Conversion Product Family']
---

Almost any document or image format (including images) can be converted to black-and-white or grayscale images. In this article, we will discuss how to convert color PDF documents to **grayscale JPG and PNG image formats in Java**.



{{< figure align=center src="images/Converted-Colored-PDF-to-Grayscale-1024x577.jpg" alt="Converted PDF to Grayscale">}}


## Java API to Convert Documents into Grayscale

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/net/) provides Java API for converting documents between a multitude of [supported file formats and image types](https://docs.groupdocs.com/conversion/net/supported-document-formats/). Conversion results can be customized using multiple advanced options. I will use this [GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java/) API to convert the PDF documents to grayscale JPG and PNG images.

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
        <version>22.3</version> 
</dependency>
```

## Convert PDF to Grayscale JPG Image in Java

Starting with the conversion of color PDF documents and transforming them to image formats. The following steps show how to convert the PDF to grayscale JPG in Java.

*   Load the PDF document using [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) class.
*   Prepare the [image conversion options](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
*   Set the conversion file format as **JPG**.
*   Set the grayscale option to true.
*   Convert to image using appropriate **convert()** method with options.

The following Java source code converts the PDF document to a grayscale JPG image.

{{< gist GroupDocsGists f9048bda36bd429f32e816b530244a77 "PdfToJpgGrayscale.java" >}}

Furthermore, there are many other options to customize the height, width, horizontal and vertical flip, document rotations, and properties like brightness, gamma, and contrast. Additionally, you can apply the watermarks with different settings to the output image.

## Convert PDF to Grayscale PNG Image in Java

Likewise, the color PDF document can also be converted to other image formats in grayscale. The following steps show how to convert a PDF file to grayscale PNG in Java.

*   Load the PDF document using [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) class.
*   Prepare conversion options using [ImageConvertOptions](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
*   Set the conversion file format as **PNG**.
*   Set the grayscale option to true.
*   Convert to PNG image using **convert()** method.

The following Java source code converts the PDF document to a grayscale PNG image.

{{< gist GroupDocsGists f9048bda36bd429f32e816b530244a77 "PdfToPngGrayscale.java" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To sum up we learned how PDF documents can be converted to PNG or JPG Image formats in Java. Try building your own conversion application, you may learn more about the low code and high code Java APIs from the [documentation](https://docs.groupdocs.com/conversion/net/) for the automation of document conversions.

The easiest way is to experience the examples from [GitHub](https://github.com/groupdocs-conversion). Contact us for any query via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Convert PDF to Grayscale using C#](https://blog.groupdocs.com/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/)
*   [Transform Presentations to Images in Java](https://blog.groupdocs.com/2022/01/18/convert-presentations-to-images-in-java/)
*   [Convert Images to PDF in Java](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)




