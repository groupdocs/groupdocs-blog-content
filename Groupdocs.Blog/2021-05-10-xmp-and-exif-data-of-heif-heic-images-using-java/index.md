---
title: "Manage XMP and EXIF Data of HEIF/HEIC Images using Java"
seoTitle: "Handle XMP and EXIF Data of HEIF HEIC Images in Java"
description: "Manage XMP and EXIF data of HEIF, HEIC images in Java. Read, update, remove EXIF and XMP data using Metadata manipulation API within Java applications."
date: Mon, 10 May 2021 08:20:00 +0000
draft: false
url: /2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java/
author: 'Shoaib Khan'
summary: "**HEIC** stands for High-Efficiency Image Container. It is the file extension for the captured images for some of the apple devices. It is a container that can contain High-Efficiency Image Format **HEIF** images. In this article, we will discuss **how to extract, update, and remove the EXIF and XMP metadata of the HEIF/HEIC images** within Java applications."
tags: ['exif data', 'exif data in Java', 'exif data of heic in java', 'XMP data in Java', 'xmp data of heic in java', 'XMP metadata']
categories: ['GroupDocs.Metadata Product Family']
---

**HEIC** stands for High-Efficiency Image Container. It is the file extension for the captured images for some of the apple devices. It is a container that can contain High-Efficiency Image Format **HEIF** images. In this article, we will discuss **how to extract, update, and remove the EXIF and XMP metadata of the HEIF/HEIC images** within Java applications.

**EXIF**, the Exchangeable Image File Format is the standard that defines how to store metadata properties in the most common images and audio formats. **XMP** is an XML-based metadata standard, that can store any set of metadata properties as name/value pairs.

The following topics are covered below

*   [Metadata Java API for EXIF, XMP data][2]
*   [Read EXIF Data of HEIC/HEIF Images][3]
*   [Read XMP data of HEIC/HEIF Images][4]

## Java API for EXIF and XMP Metadata {#java-api-for-exif-and-xmp-metadata}

[GroupDocs.Metadata][5] provides the metadata manipulation API for your Java applications. The API allows to read, update, add, clean/remove, and traverse features for many file formats. It supports various metadata standards like EXIF, IPTC, and XMP. Word-processing documents, spreadsheets, presentations, email messages, eBooks, images, AutoCAD drawings, audio and video files, torrents, are among the supported document formats. More precisely, you can visit the documentation for the complete list of [supported file formats for metadata manipulation][6].

### Download and Configure

Get the metadata library from the [downloads][7] section. For your Maven-based Java application, just add the following pom.xml configuration. After this, you can try the examples of this article as well the many more example available on [GitHub][8]. For the details, you may visit the [API Reference][9].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>21.4</version> 
</dependency>
```

## Read EXIF data of HEIF / HEIC Images in Java {#read-exif-of-heic-heif-images}

The following are the steps to read and extract EXIF data of HEIC and HEIF images.

*   Load the HEIF or HEIC image using the Metadata class.
*   Get the root package.
*   Retrieve the EXIF package from the root package.
*   From the EXIF package, you can traverse the EXIF data properties.
*   Furthermore, you can get the IFD (Image File Directory) and GPS information from the EXIF package.

The following code shows how to get EXIF data, IFD and GPS metadata information of the HEIC image using Java.

{{< gist GroupDocsGists 7a8203b8c12e144476a5c260f91133e7 "ReadHeifExif.java" >}}

## Read XMP data of HEIC / HEIF Images in Java {#read-xmp-of-heic-heif-images}

The following steps read XMP metadata of HEIC or HEIF images.

*   Load the HEIF or HEIC image using the Metadata class.
*   Get the root package using the getRootPackage method.
*   From the root package, you can get the XMP basic information.
*   Further, you can get the DCMI Dublin Core information.
*   Additionally, you can get Photoshop information using the getPhotoshop method.

The following source code shows how to get XMP basic, DCMI, and Photoshop information in Java.

{{< gist GroupDocsGists 7a8203b8c12e144476a5c260f91133e7 "ReadHeifXmp.java" >}}

Likewise, there are many setter methods to set or update different XMP properties. You can even provide your own key-value pair to [set the custom XMP package property][10].

## Remove EXIF and XMP Metadata of HEIC/HEIF Images in Java

You can just set the respective EXIF package or XMP package to null to remove all the metadata properties.

The following code removes the EXIF data of HEIC images.

{{< gist GroupDocsGists 7a8203b8c12e144476a5c260f91133e7 "RemoveExifData.java" >}}

The following code removes the XMP data of HEIC images.

{{< gist GroupDocsGists 7a8203b8c12e144476a5c260f91133e7 "RemoveXmpData.java" >}}

## Conclusion

To sum up, we have learned to extract, update, remove EXIF and XMP metadata from the HEIF/HEIC images in Java. Furthermore, you have seen how to get IFD and GPS information from these images. Now you can easily get this information and also go ahead building your own applications like GroupDocs.Metadata App Product Family to automate metadata information.

For more information, options, and examples, you can visit the [documentation][11] and the [GitHub][12] repository. For further queries, contact us on the support [forum][13].

## See Also

*   [Extract RIFF INFO and Metadata of WAV files in Java][14]
*   [Clean Metadata of Documents and Images using Java][15]







[1]: https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java
[2]: #java-api-for-exif-and-xmp-metadata
[3]: #read-exif-of-heic-heif-images
[4]: #read-xmp-of-heic-heif-images
[5]: https://products.groupdocs.com/metadata
[6]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/metadata/java
[8]: https://github.com/groupdocs-metadata
[9]: https://apireference.groupdocs.com/metadata/java
[10]: https://docs.groupdocs.com/metadata/java/working-with-xmp-metadata/
[11]: https://docs.groupdocs.com/metadata/
[12]: https://github.com/groupdocs-metadata
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/
[15]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/

