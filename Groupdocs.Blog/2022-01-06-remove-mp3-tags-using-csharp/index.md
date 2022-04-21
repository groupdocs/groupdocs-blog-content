---
title: 'Remove MP3 Tags using C#'
date: Thu, 06 Jan 2022 05:27:00 +0000
draft: false
url: /2022/01/06/remove-mp3-tags-using-csharp/
aliases:
    - /2017/11/22/clean-metadata-from-avi-mp3-format-groupdocs.metadata-for-.net-17.11/
author: 'Shoaib Khan'
summary: '[MP3](https://docs.fileformat.com/audio/mp3/) files could contain metadata of various standards. Sometimes you do not require certain metadata information. We can quickly remove these metadata MP3 tags programmatically. In this article, we will discuss **how to remove different MP3 tags using C#**. Precisely, we will learn to remove ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from the mp3 files within the .NET application.'
tags: ['Remove APE', 'Remove Metadata in CSharp', 'Remove MP3 ID3', 'Remove MP3 Metadata', 'Remove MP3 Tags', 'Remove MP3 Tags in CSharp']
categories: ['GroupDocs.Metadata Product Family']
---

[MP3](https://docs.fileformat.com/audio/mp3/) files could contain metadata of various standards. Sometimes you do not require certain metadata information. We can quickly remove these metadata MP3 tags programmatically. In this article, we will discuss **how to remove different MP3 tags using C#**. Precisely, we will learn to remove ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from the mp3 files within the .NET application.

The following topics are covered below:

*   [.NET API to Remove MP3 tags](#mp3-tags-dotnet-api)
*   [Remove MP3 ID3 Tags - ID3, Lyrics, APE](#remove-mp3-tags)
*   [C# Code Example](#source-code-remove-mp3-tags)

## .NET API for MP3 Tags Removal {#mp3-tags-dotnet-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) showcases [metadata management .NET API](https://products.groupdocs.com/metadata/net/) to deal with various file formats within .NET applications. The API allows to read, update, add, clean, and totally remove the metadata for many file formats. We will use this API to remove metadata tags of MP3 files.

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/metadata) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.metadata).

```
PM> Install-Package GroupDocs.Metadata
```

## Remove MP3 Tags using C# - ID3v1, ID3v2, Lyrics, APE {#remove-mp3-tags}

The following steps will quickly allow you to remove MP3 metadata tags from your MP3 files in C#.

1.  **Load** the MP3 file.
2.  Get the **MP3 root package**.
3.  **Remove** the relevant MP3 Tag(s).
4.  **Save** the updated MP3 file.

### 1\. **Load MP3**

Select the MP3 file and load it using the [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) class.

```
Metadata metadata = new Metadata("path/mp3File.mp3");
```

### 2\. Get MP3 Root Package

Get the [MP3 Root Package](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage) of the MP3 file using the [GetRootPackage()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage/index) method.

```
var root = metadata.GetRootPackage();
```

### 3\. Remove MP3 Tags

From the following ways of removing different metadata tags, you can use your relevant removal strategy.

#### **ID3v**1

To remove the **ID3v1** metadata tags, set the [ID3V1](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/id3v1) property of the root package as null.

```
root.ID3V1 = null;
```

#### **ID3v2**

To remove the **ID3v2** metadata tags, nullify the [ID3V2](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/id3v2) property.

```
root.ID3V2 = null;
```

#### **Lyrics**

Remove the **Lyrics** tags by setting the [Lyrics3V2](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/lyrics3v2) property to null.

```
root.Lyrics3V2 = null;
```

#### ****APE****

Use the [RemoveApeV2()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/methods/removeapev2) method of the root package to eliminate **APEv2** tags.

```
root.RemoveApeV2();
```

### 4\. Save the File

Lastly, **save** the updated MP3 file using the [Save()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index) method.

```
metadata.Save("path/mp3TagsRemoved.mp3");
```

## Complete Code - Remove {#source-code-remove-mp3-tags}

The following source code example shows how to remove relevant MP3 Tags from the MP3 file in C#.

{{< gist GroupDocsGists ae3589a5e5039c8e1234fdb4bd099c1d "RemoveMP3Tags.cs" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) to use the API without the evaluation limitations.

## Conclusion

To sum up, we learned to remove metadata tags from the MP3 files using C#. We specifically removed ID3v1, ID3v2, Lyrics, and APE tags from the MP3 files. You can learn more about the API from the [documentation](https://docs.groupdocs.com/metadata/net/) and contact us for queries via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Read MP3 Tags using C# – (ID3, Lyrics, APE)](https://blog.groupdocs.com/2022/01/22/read-mp3-tags-using-csharp/)
*   [Extract RIFF INFO and Metadata of WAV files in C#](https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/)
*   [Manage XMP and EXIF Data of HEIF/HEIC Images using C#](https://blog.groupdocs.com/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/)




