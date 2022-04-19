---
title: 'Read MP3 Tags in Java - (ID3, Lyrics, APE)'
date: Sat, 12 Feb 2022 11:43:14 +0000
draft: false
url: /2022/02/12/read-mp3-tags-in-java/
author: 'Shoaib Khan'
summary: 'Metadata variants are attached with documents of different file formats. MP3 files commonly contain ID3 metadata tags. This article discusses **how to read different MP3 tags in Java**. One by one, we will see how to extract ID3 (IDEv1, ID3v2), Lyrics, and APEv2 metadata tags from the mp3 files using Java Metadata API.'
tags: ['read ID3 tags', 'read mp3 lyrics', 'Read MP3 tags', 'Read MP3 Tags in Java']
categories: ['GroupDocs.Metadata Product Family']
---

Metadata variants are attached with documents of different file formats. MP3 files commonly contain ID3 metadata tags. This article discusses **how to read different MP3 tags in Java**. One by one, we will see how to extract ID3 (IDEv1, ID3v2), Lyrics, and APEv2 metadata tags from the mp3 files using Java Metadata API.

The following topics are covered below:

*   [Java API to Manage MP3 tags](#mp3-tags-java-api)
*   [Read MP3 ID3 Tags - ID3v1 & ID3v2](#read-mp3-id3-tags)
*   [Get MP3 Lyrics Tags](#read-mp3-lyrics-tags)
*   [Retrieve MP3 APEv2 Tags](#read-mp3-ape-tags)

## Java API for MP3 Metadata Tags {#mp3-tags-java-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) is equipped with APIs to automate metadata management of [various file formats](https://docs.groupdocs.com/metadata/net/supported-document-formats/) within applications. It's Java API allows you to read, update, add, clean, and remove the metadata for many file formats within the Java application. We will use it to work with MP3 metadata tags.

### Download and Configure

Get the metadata library from the [downloads](https://downloads.groupdocs.com/metadata/java) section. For your Maven-based Java application, just add the following pom.xml configuration. After this, you can try the examples of this article as well the many more example available on [GitHub](https://github.com/groupdocs-metadata). For the details, you may visit the [API Reference](https://apireference.groupdocs.com/metadata/java).

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>22.2</version> 
</dependency>
```

## Read MP3 ID3 Tags in Java - ID3v1 & ID3v2 {#read-mp3-id3-tags}

The following steps show how to read the MP3 ID3v1 tags using Java.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) class.
*   Retrieve the [MP3RootPackage](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage) using the **getRootPackageGeneric()** method.
*   From the root package, retrieve each of the ID3v1 properties.

The following Java source code reads some of the MP3 ID3v1 tags of the MP3 file.

{{< gist GroupDocsGists 3a2d619a89bcea9edd0790a983ad39d4 "ReadMP3ID3V1.java" >}}

You can extract the ID3v2 tags in a similar way. The following steps show how to retrieve the MP3 ID3v2 tags in Java.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) class.
*   Get the [root package](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage).
*   From the root, you can easily retrieve all the ID3v2 tags like Artist, Composers, Publisher, Title etc.
*   Details for attached pictures can be retrieved from the properties of [Attached Picture Frames](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V2AttachedPictureFrame).

The following Java source code example reads some of the MP3 ID3v2 tags and attached pictures details of the MP3 file.

{{< gist GroupDocsGists 3a2d619a89bcea9edd0790a983ad39d4 "ReadMP3ID3V2.java" >}}

## Read MP3 Lyrics Tags in Java {#read-mp3-lyrics-tags}

The following steps guide how to read the MP3 Lyrics tags in Java.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) class.
*   Retrieve the [root package](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage).
*   From the root, you can get lyrics tags and its properties like Lyrics, artist, track etc.

The following Java code snippet retrieves MP3 lyrics tags and some of the properties from the MP3 file.

{{< gist GroupDocsGists 3a2d619a89bcea9edd0790a983ad39d4 "ReadMP3Lyrics.java" >}}

## Read MP3 APEv2 Tags in Java {#read-mp3-ape-tags}

The following steps showing how we can extract the MP3 APEv2 tags within Java application.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) class.
*   Retrive the **[root package](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage)** using ****getRootPackageGeneric**()** method.
*   From the root, you can retrieve the APEv2 tags like Album, Genre, Copyrights, Language, etc.

The following Java code examples read some of the properties of MP3 APE tags of an MP3 file.

{{< gist GroupDocsGists 3a2d619a89bcea9edd0790a983ad39d4 "ReadMP3APE.java" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To sum up, we learned how to extract metadata tags from the MP3 files in Java. One by one, we read ID3v1, ID3v2, Lyrics, and APE tags and their properties from the MP3 files. Think about building your own MP3 online tag editor & metadata viewer just like [Online Metadata App](https://products.groupdocs.app/metadata/total).

Learn more about the API from the [documentation](https://docs.groupdocs.com/metadata/java/) and contact us for queries via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Metadata Cleaner for Documents and Images using Java](https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/)
*   [Remove MP3 Tags in Java](https://blog.groupdocs.com/2022/01/30/remove-mp3-tags-in-java/)
*   [Manage XMP and EXIF Data of HEIF/HEIC Images using Java](https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java/)
*   [Extract RIFF INFO and Metadata of WAV files in Java](https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/)




