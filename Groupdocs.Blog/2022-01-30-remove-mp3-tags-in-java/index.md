---
title: 'Remove MP3 Tags in Java'
date: Sun, 30 Jan 2022 05:05:23 +0000
draft: false
url: /2022/01/30/remove-mp3-tags-in-java/
author: 'Shoaib Khan'
summary: 'When the metadata is not really required, you can eliminate it. In this article, we will learn **how to programmatically remove different MP3 tags in Java.** Precisely, we will see the removal of ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from mp3 files within the Java application.

The following topics are covered below:

*   Java API for MP3 tags
*   Remove MP3 ID3 Tags - ID3, Lyrics, APE
*   Java Code - Remove MP3 Metadata Example'
tags: ['Remove APE', 'Remove Metadata in Java', 'Remove MP3 ID3', 'Remove MP3 Metadata', 'Remove MP3 Tags', 'Remove MP3 Tags in Java']
categories: ['GroupDocs.Metadata Product Family']
---

When the metadata is not really required, you can eliminate it. In this article, we will learn **how to programmatically remove different MP3 tags in Java.** Precisely, we will see the removal of ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from mp3 files within the Java application.

The following topics are covered below:

*   [Java API for MP3 tags](#mp3-tags-java-api)
*   [Remove MP3 ID3 Tags - ID3, Lyrics, APE](#remove-mp3-tags)
*   [Java Code - Remove MP3 Metadata Example](#source-code-remove-mp3-tags)

## Java API for MP3 Tags Removal {#mp3-tags-java-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) provides [metadata management Java API](https://products.groupdocs.com/metadata/java/) to deal with metadata of different file formats. **GroupDocs.Metadata for Java** allows to read, update, add, clean, and totally remove the metadata for [various file formats](https://docs.groupdocs.com/metadata/java/supported-document-formats/). I will use this API to remove metadata tags of MP3 files.

### Download or Configure

You may download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/metadata), or just get the repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>21.8</version> 
</dependency>
```

## Remove MP3 Tags in Java - ID3v1, ID3v2, Lyrics, APE {#remove-mp3-tags}

The following steps will quickly allow you to remove MP3 metadata tags from your MP3 files in Java.

1.  **Load** the MP3 file.
2.  Get the **MP3 root package**.
3.  **Remove** the relevant MP3 Tag(s).
4.  **Save** the updated MP3 file.

### 1\. **Load MP3**

Select the MP3 file and load it using the [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) class.

```
Metadata metadata = new Metadata("path/mp3File.mp3");
```

### 2\. Get MP3 Root Package

Get the [MP3 Root Package](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage) of the MP3 file using the [getRootPackageGeneric()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackageGeneric()) method.

```
MP3RootPackage root = metadata.getRootPackageGeneric();
```

### 3\. Remove MP3 Tags

Following are ways to remove different metadata tags. You can use the relevant removal method for your MP3 files.

#### **ID3v**1

To remove the **ID3v1** metadata tags, set the [ID3V1](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V1Tag) property of the root package to null.

```
root.setID3V1(null);
```

#### **ID3v2**

Set the [ID3V2](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V2Tag) property to null to remove the **ID3v2** metadata tags.

```
root.setID3V2(null);
```

#### **Lyrics**

Remove the **Lyrics** tags by setting the [Lyrics Tag](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/LyricsTag) to null.

```
root.setLyrics3V2(null);
```

#### ****APE****

Use the [removeApeV2()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage#removeApeV2()) method of the root package to eliminate **APEv2** tags.

```
root.removeApeV2();
```

### 4\. Save the File

Lastly, **save** the updated MP3 file using the [save()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save()) method.

```
metadata.save("path/mp3TagsRemoved.mp3");
```

## Complete Code - Remove MP3 Tags {#source-code-remove-mp3-tags}

The following Java source code example shows how to remove relevant MP3 Tags from the MP3 files.

{{< gist GroupDocsGists 4b08d867482e4331d10c5a69aaa457ea "RemoveMP3Tags.java" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to remove metadata tags from MP3 files in Java using Metadata API. One by one, we looked into how to remove ID3v1, ID3v2, Lyrics, and APE tags from the MP3 files.

You can learn more about the API from the [documentation](https://docs.groupdocs.com/metadata/java/). Contact us for queries via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Metadata Cleaner for Documents and Images using Java](https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/)
*   [Extract RIFF INFO and Metadata of WAV files in Java](https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/)
*   [Manage XMP and EXIF Data of HEIF/HEIC Images using Java](https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java/)




