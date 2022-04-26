---
title: 'Convert WebP to JPG, PNG, and PDF in Java'
date: Mon, 18 Jan 2021 22:52:00 +0000
draft: false
url: /2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/
aliases:
    - /2020/01/26/convert-webp-to-png-jpg-and-pdf-in-java/
    - /2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
author: 'Shoaib Khan'
summary: "WebP images **give transparency like PNG**, **animate like GIF**, and the most important for any web developer is the **smaller size than comparative quality JPG format**. However, due to incompatibility issues or any other requirement, it is sometimes needed to convert the WebP image into JPG, PNG, or other formats."
tags: ['convert WebP to JPG in java', 'Convert WebP to PNG in Java', 'Java Convert WebP', 'Java WebP to JPG', 'Java WebP to PDF', 'Java WebP to PNG']
categories: ['GroupDocs.Conversion Product Family']
---

WebP is the image format introduced by [Google][1] that provides lossless and lossy compression for images on the web. WebP images are smaller in size as compared to the well-known and vastly used image formats like PNG and JPG, hence provides a faster web experience.


{{< figure align=center src="images/webp-to-jpg-converter-free-online.jpg" alt="Free Online WebP to JPG Converter">}}


_If you are here just to online convert your WebP files to JPG, PNG, or PDF documents, use the [free online WebP conversion tool by GroupDocs][2] that is developed using GroupDocs.Conversion API. However, if you want to achieve the exact thing programmatically in Java, continue reading._

WebP images **give transparency like PNG**, **animate like GIF**, and the most important for any web developer is the **smaller size than comparative quality JPG format**. However, due to incompatibility issues or any other requirement, it is sometimes needed to convert the WebP image into JPG, PNG, or other formats.

*   [Java API to Convert WebP Images][3]
*   [Convert WebP to JPG in Java][4]
*   [Convert WebP to JPG, PNG, TIFF with Advanced Options in Java][5]
*   [WebP to PDF Conversion in Java][6]



{{< figure align=center src="images/convert-webp-to-jpg-png-tiff-with-options.jpg" alt="Convert WebP image to JPG, PNG or PDF formats in Java and C#" caption="**The Original WebP image is changed to JPG format with color adjustments and options.** Image Used: [A Wild Cherry (Prunus avium) in flower][7]. Image Author: Benjamin Gimmel. Photo licensed under the [Creative Commons][8] [Attribution-Share Alike 3.0 Unported][9] license.">}}


## Java API to Convert WebP Images {#image-conversion-java-api}

GroupDocs provides the [solution][10] to convert 50+ document and image file formats. As a Java developer, you can use [GroupDocs.Conversion for Java][11] to convert WebP images within your Java-based applications.

You may download the **JAR** file from the [downloads section][12] or just add the following repository and dependency configurations in the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>20.10.3</version> 
</dependency>
```

While using GroupDocs.Conversion API, you can get the possible conversion formats of the source document or image by using the [getPossibleConversions()][13]  method of the [Converter][14] class. There are several ways to get the possible conversions, you may visit the [documentation][15] or the [API reference][16] for this.

## Convert WebP to JPG in Java {#convert-webp-to-jpg-in-java}

The following steps help you convert the WebP image to JPG or other formats:

*   Initialize the [Converter][17] class object with the WebP image file.
*   Set the conversion format to JPG using **setFormat** method of [ImageConvertOptions][18].
*   Convert the WebP to JPG using the convert method.

The below Java source code shows how easy is the WebP conversion to JPG format. For the conversion to some other supported formats, you just have to change the output format of the image by setting the appropriate ImageFileType. For instance, to convert WebP to PNG, just change the below ImageFileType from JPG to PNG.

{{< gist GroupDocsGists 6bfdc6033f28598a78631ccadf843c3c "ConvertWebPToJPG.java" >}}

## Convert WebP to JPG, PNG, TIFF with Advanced Options in Java {#convert-webp-with-advanced-options-in-java}

While converting the WebP to JPG, PNG, or other formats, you can also apply color adjustments to the output images. You can change the contrast, brightness, and gamma of the resultant image. The Image can be flipped, rotated, apply watermarks, or get the grayscale image as the output.

Above, I have shown the resultant images that are converted from WebP to JPG format after applying different variations using below mentioned Java code.

{{< gist GroupDocsGists 6bfdc6033f28598a78631ccadf843c3c "ConvertWebPWithAdvancedOptions.java" >}}

## WebP to PDF Conversion in Java {#webp-to-pdf-conversion-in-java}

Along with the conversion of WebP to other image formats, GroupDocs.Conversion API allows converting WebP into document formats like PDF as well. The following example shows how you can quickly convert WebP images into PDF (Portable Document Format). You can further apply different customization for the resultant PDF file using relevant [Convert Options][19].

{{< gist GroupDocsGists 6bfdc6033f28598a78631ccadf843c3c "ConvertWebPToPDF.java" >}}

There are many other open-source examples that are publicly available at [GitHub Repository][20]. Download the source code and quickly run the examples using the [getting started][21] guide. In case of any difficulty, look at the [documentation][22] or reach us at any time on the [forum][23].

## Conclusion

I think, as a Java developer, you are now confident to programmatically convert the WebP images to JPG, PNG, GIF, TIFF, PDF, and other formats in Java. You can now easily change the color adjustment (contrast brightness, gamma, grayscale) to the converted formats and flip, rotate, or apply watermarks.

Why not create your own java-based application? It can convert the supported image format and apply different filters and color variations.

Have a nice coding day!

## See Also

*   [Convert WebP to JPG, PNG, TIFF, and PDF in C#][24]







[1]: https://developers.google.com/speed/webp
[2]: https://products.groupdocs.app/conversion/webp-to-jpg
[3]: #image-conversion-java-api
[4]: #convert-webp-to-jpg-in-java
[5]: #convert-webp-with-advanced-options-in-java
[6]: #webp-to-pdf-conversion-in-java
[7]: http://commons.wikimedia.org/wiki/File:Fr%C3%BChling_bl%C3%BChender_Kirschenbaum.jpg
[8]: http://en.wikipedia.org/wiki/en:Creative_Commons
[9]: http://creativecommons.org/licenses/by-sa/3.0/deed.en
[10]: https://products.groupdocs.com/conversion
[11]: https://products.groupdocs.com/conversion/java
[12]: https://downloads.groupdocs.com/conversion/java
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#getAllPossibleConversions()
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://docs.groupdocs.com/conversion/java/get-possible-conversions/
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#getPossibleConversions()
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions
[19]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/package-frame
[20]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java
[21]: https://docs.groupdocs.com/display/conversionjava/Getting+Started
[22]: https://docs.groupdocs.com/display/conversionjava/Home
[23]: https://forum.groupdocs.com/c/conversion
[24]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/

