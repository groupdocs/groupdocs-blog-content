---
title: 'Read MP3 Tags using C# - (ID3, Lyrics, APE)'
date: Sat, 22 Jan 2022 12:49:38 +0000
draft: false
url: /2022/01/22/read-mp3-tags-using-csharp/
author: 'Shoaib Khan'
summary: 'There are different metadata standards that are used with MP3 files. Various types of data can be stored using different standards. In this article, we will discuss how to read different MP3 tags using C#. Specifically, we will learn to extract ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from the mp3 files within the .NET application.'
tags: ['read ID3 tags', 'read mp3 lyrics', 'Read MP3 tags', 'Read MP3 Tags CSharp']
categories: ['GroupDocs.Metadata Product Family']
---



{{< figure align=center src="images/mp3-icon.png" alt="mp3 - extract its metadata mp3 tags">}}


There are different metadata standards that are used with MP3 files. Various types of data can be stored using different standards. In this article, we will discuss **how to read different MP3 tags using C#**. Specifically, we will learn to extract ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from the mp3 files within the .NET application.

The following topics are covered below:

*   [.NET API to Manage MP3 tags](#mp3-tags-dotnet-api)
*   [Read MP3 ID3 Tags - ID3v1 & ID3v2](#read-mp3-id3-tags)
*   [Get MP3 Lyrics Tags](#read-mp3-lyrics-tags)
*   [Retrieve MP3 APEv2 Tags](#read-mp3-ape-tags)

## .NET API for MP3 Tags Editor {#mp3-tags-dotnet-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) provides .NET API to automate metadata management of [various file formats](https://docs.groupdocs.com/metadata/net/supported-document-formats/) within .NET applications. The API allows to read, update, add, clean, and remove the metadata for many file formats. We will use this API to deal with metadata tags of MP3 files.

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/metadata) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.metadata).

```
PM> Install-Package GroupDocs.Metadata
```

## Read MP3 ID3 Tags using C# - ID3v1 & ID3v2 {#read-mp3-id3-tags}

The following steps show how to read the MP3 ID3v1 tags using C#.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) class.
*   Retrieve the [root package](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage) using the **GetRootPackage()** method.
*   From the root, you can retrieve each of the ID3v1.

The following C# source code reads some of the MP3 ID3v1 tags of the MP3 file.

{{< gist GroupDocsGists 693b046433c72acce25a581440fe3dc4 "ReadMP3ID3V1.cs" >}}

Similarly, you can extract the ID3v2 tags. The following steps show how to retrieve the MP3 ID3v2 tags using C#.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) class.
*   Get the [root package](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage).
*   From the root, you can retrieve all the ID3v2 tags like Band, Artist, Composers, etc.
*   For the attached pictures and their details, use the AttachedPictures properties.

The following C# source code example reads some of the MP3 ID3v2 tags and attached pictures details of the MP3 file.

{{< gist GroupDocsGists 693b046433c72acce25a581440fe3dc4 "ReadMP3ID3V2.cs" >}}

## Read MP3 Lyrics Tags in C# {#read-mp3-lyrics-tags}

The following steps guide to read the MP3 Lyrics tags using C#.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) class.
*   Retrieve the [root package](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage).
*   From the root, you can get lyrics tags and its properties like Lyrics, artist, etc.

The following C# code snippet retrieves MP3 lyrics tags and some of its properties from the MP3 file.

{{< gist GroupDocsGists 693b046433c72acce25a581440fe3dc4 "ReadMP3Lyrics.cs" >}}

## Read MP3 APEv2 Tags in C# {#read-mp3-ape-tags}

The following steps show how we can extract the MP3 APEv2 tags using C#.

*   Load the MP3 file using [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) class.
*   Retrive the **root package** using **GetRootPackage()** method.
*   From the root, you can retrieve all the APEv2 tags like Album, Genre, Copyrights, Language, etc.

The following C# code examples read some of the properties of MP3 APE tags of an MP3 file.

{{< gist GroupDocsGists 693b046433c72acce25a581440fe3dc4 "ReadMP3APE.cs" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to extract metadata tags from the MP3 files using C#. We read ID3v1, ID3v2, Lyrics, and APE tags and their properties from the MP3 files. You can learn more about the API from the [documentation](https://docs.groupdocs.com/metadata/net/) and contact us for queries via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Metadata Remover for Documents and Images using C#](https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/)
*   [Extract RIFF INFO and Metadata of WAV files in C#](https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/)
*   [Manage XMP and EXIF Data of HEIF/HEIC Images using C#](https://blog.groupdocs.com/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/)
*   [Manage EXIF Data of Images in C# .NET](https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/)




