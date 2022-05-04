---
title: "Extract RIFF INFO and Metadata of WAV files in C#"
seoTitle: "Extract RIFF INFO and Metadata of WAV files in C#"
description: "Extract metadata and RIFF INFO of WAV audio files in C#. Metadata API allows metadata management within your .NET applications."
date: Fri, 05 Mar 2021 17:58:00 +0000
draft: false
url: /2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
author: 'Shoaib Khan'
summary: "**RIFF** (Resource Interchange File Format) is a file container format for storing data as tagged chunks. It is mainly used to store multimedia like video and audio. The chunk may include information such as the artist, the creation date, and copyright information, etc. This article will be guiding developers to **extract metadata and RIFF INFO from the WAV audio files in C#**."
tags: ['Extract Metadata in CSharp', 'Extract Metadata of WAV file in CSharp', 'Extract RIFF INFO of WAV in CSharp']
categories: ['GroupDocs.Metadata Product Family']
---

**RIFF** (Resource Interchange File Format) is a file container format for storing data as tagged chunks. It is mainly used to store multimedia like video and audio. The chunk may include information such as the artist, the creation date, and copyright information, etc. This article will be guiding developers to **extract metadata and RIFF INFO from the WAV audio files in C#**.

The following topics will be covered in the article in brief:

*   [.NET API for Managing Metadata][2]
*   [Extract Metadata of WAV Files in C#][3]
*   [Extract RIFF INFO of WAV Files in C#][4]

## .NET API for Managing Metadata {#metadata-management-dotnet-api}

In this article, I will be using [GroupDocs.Metadata for .NET][5] API in the C# examples for extracting metadata from WAV files. In addition to the audio WAV files, the API supports adding, removing, updating, and extracting metadata from MP3 files and videos. Furthermore, it supports Microsoft Office and Open Office file formats, eBooks, images, and many other document formats.

You can download the **DLLs** or **MSI** installer from the [downloads section][6] or install the API in your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Metadata
```

## Extract Metadata of WAV Files in C# {#extract-metadata-of-wav-audio-in-csharp}

Let's start with the extraction of the metadata from the WAV files. Follow the steps and the below-mentioned code example for extracting the WAV package metadata properties of WAV files in C#.

*   Load the WAV audio file.
*   Get the [WavRootPackage][8] of metadata.
*   Extract the [WavPackage][9] from the root package.
*   Now you can access all the properties of WAV audio.

{{< gist GroupDocsGists da2d3e1b0d6c1d2724d2057eddacd7c7 "ExtractWavMetadata.cs" >}}

Here is the output of the above code:

```
Bits per Sample: 16
Block Align: 4
Byte Rate: 176400
Number of Channels: 2
Audio Format: 1
Sample Rate: 44100
```

## Extract RIFF INFO of WAV Files in C# {#extract-riff-info-of-wav-audio-in-csharp}

RIFF INFO of the WAV files can also be extracted in no different way than the extraction of WavPackage properties shown earlier. Using the following steps, you can extract the RIFF INFO of the audio file of WAV file format within your .NET application.

*   Load the WAV audio file.
*   Get the [WavRootPackage][10] of metadata.
*   Extract the [RiffInfoPackage][11] from the root package.
*   Now access the properties of WAV audio.

The following code example extracts the RIFF INFO package metadata properties of the WAV file in C#.

{{< gist GroupDocsGists da2d3e1b0d6c1d2724d2057eddacd7c7 "ExtractWavRiffInfo.cs" >}}

The following is the output of the above code:

```
Artist: GroupDocs 
Comment: Sample WAV File
Copyright: 
CreationDate: 2020-12-03
Software: Sound Forge
Engineer: SGEFFNER
Genre: Mystery
```

## Conclusion

In short, it is very easy to take out the metadata and RIFF INFO from the WAV files in C#. After trying the above examples, think about developing your own metadata extractor .NET application like [GroupDocs.Metadata App][12].

There are many more open-source examples available at [GitHub Repository][13]. Download the source code and quickly run the examples using the [getting started][14] guide. In case of any difficulty, visit the [documentation][15] or reach the support team any time on the [forum][16].

## See Also

*   [Manage EXIF Data of Images in C#][17]
*   [Manage EXIF Data of Images in Java][18]







[1]: https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp
[2]: #metadata-management-dotnet-api
[3]: #extract-metadata-of-wav-audio-in-csharp
[4]: #extract-riff-info-of-wav-audio-in-csharp
[5]: https://products.groupdocs.com/metadata/net
[6]: https://downloads.groupdocs.com/metadata/net
[7]: https://www.nuget.org/packages/groupdocs.metadata
[8]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/index
[9]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/wavpackage
[10]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/index
[11]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/riffinfopackage
[12]: https://products.groupdocs.app/metadata/family
[13]: https://github.com/groupdocs-metadata
[14]: https://docs.groupdocs.com/metadata/net/getting-started/
[15]: https://docs.groupdocs.com/metadata/net
[16]: https://forum.groupdocs.com/c/metadata
[17]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
[18]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/

