---
title: "在 C# 中提取 WAV 文件的 RIFF INFO 和元数据"
date: Fri, 05 Mar 2021 17:58:00 +0000
draft: false
url: /zh/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
author: 'Shoaib Khan'
summary: "**RIFF**（资源交换文件格式）是一种文件容器格式，用于将数据存储为标记的块。它主要用于存储视频和音频等多媒体。 chunk 可能包含艺术家、创作日期、版权信息等信息。本文将指导开发者**从 C# 中的 WAV 音频文件中提取元数据和 RIFF INFO。"
tags: ['Extract Metadata in CSharp', 'Extract Metadata of WAV file in CSharp', 'Extract RIFF INFO of WAV in CSharp']
categories: ['GroupDocs.Metadata Product Family']
---

**RIFF**（资源交换文件格式）是一种文件容器格式，用于将数据存储为标记的块。它主要用于存储视频和音频等多媒体。 chunk 可能包含艺术家、创作日期、版权信息等信息。本文将指导开发者**从 C# 中的 WAV 音频文件中提取元数据和 RIFF INFO。

本文将简要介绍以下主题：

* [用于管理元数据的.NET API][2]
* [在C#中提取WAV文件的元数据][3]
* [在 C# 中提取 WAV 文件的 RIFF 信息][4]

## 用于管理元数据的 .NET API {#metadata-management-dotnet-api}

在本文中，我将在 C# 示例中使用 [GroupDocs.Metadata for .NET][5] API 从 WAV 文件中提取元数据。除了音频 WAV 文件外，API 还支持从 MP3 文件和视频中添加、删除、更新和提取元数据。此外，它还支持 Microsoft Office 和 Open Office 文件格式、电子书、图像和许多其他文档格式。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Metadata
```

## 在 C# 中提取 WAV 文件的元数据 {#extract-metadata-of-wav-audio-in-csharp}

让我们从从 WAV 文件中提取元数据开始。按照以下步骤和下面提到的代码示例，在 C# 中提取 WAV 文件的 WAV 包元数据属性。

* 加载 WAV 音频文件。
* 获取元数据的[WavRootPackage][8]。
* 从根包中提取 [WavPackage][9]。
* 现在您可以访问 WAV 音频的所有属性。

```
// 在 C# 中提取 WAV 文件的元数据
using (Metadata metadata = new Metadata("audio.wav"))
{
    var root = metadata.GetRootPackage<WavRootPackage>();
    Console.WriteLine("Bits per Sample: "   + root.WavPackage.BitsPerSample); // Bits per Sample
    Console.WriteLine("Block Align: "       + root.WavPackage.BlockAlign); // Block Align
    Console.WriteLine("Byte Rate: "         + root.WavPackage.ByteRate); // Byte Rate
    Console.WriteLine("Number of Channels: " + root.WavPackage.NumberOfChannels); // Number of Channels
    Console.WriteLine("Audio Format: "      + root.WavPackage.AudioFormat); // Audio Format 
    Console.WriteLine("Sample Rate: "       + root.WavPackage.SampleRate); // Sample Rate
}
```

以下是上述代码的输出：

```
Bits per Sample: 16
Block Align: 4
Byte Rate: 176400
Number of Channels: 2
Audio Format: 1
Sample Rate: 44100
```

## 在 C# 中提取 WAV 文件的 RIFF INFO {#extract-riff-info-of-wav-audio-in-csharp}

WAV 文件的 RIFF INFO 也可以以与前面所示的 WavPackage 属性提取相同的方式提取。使用以下步骤，您可以在 .NET 应用程序中提取 WAV 文件格式的音频文件的 RIFF INFO。

* 加载 WAV 音频文件。
* 获取元数据的[WavRootPackage][10]。
* 从根包中提取 [RiffInfoPackage][11]。
* 现在访问 WAV 音频的属性。

以下代码示例提取 C# 中 WAV 文件的 RIFF INFO 包元数据属性。

```
// 在 C# 中提取 WAV 文件的 RIFF INFO
using (Metadata metadata = new Metadata("audio.wav"))
{
    var root = metadata.GetRootPackage<WavRootPackage>();
    Console.WriteLine("Artist: "      + root.RiffInfoPackage.Artist); // Artist
    Console.WriteLine("Comment: "     + root.RiffInfoPackage.Comment); // Comment
    Console.WriteLine("Copyright: "   + root.RiffInfoPackage.Copyright); // Copyright
    Console.WriteLine("CreationDate: " + root.RiffInfoPackage.CreationDate); // Creation Date
    Console.WriteLine("Software: "    + root.RiffInfoPackage.Software); // Software
    Console.WriteLine("Engineer: "    + root.RiffInfoPackage.Engineer); // Engineer
    Console.WriteLine("Genre: "       + root.RiffInfoPackage.Genre); // Genre
}
```

以下是上述代码的输出：

```
Artist: GroupDocs 
Comment: Sample WAV File
Copyright: 
CreationDate: 2020-12-03
Software: Sound Forge
Engineer: SGEFFNER
Genre: Mystery
```

## 结论

简而言之，在 C# 中从 WAV 文件中取出元数据和 RIFF INFO 非常容易。在尝试了上述示例之后，请考虑开发您自己的元数据提取器 .NET 应用程序，例如 [GroupDocs.Metadata App][12]。

[GitHub 存储库][13] 中提供了更多开源示例。下载源代码并使用 [入门][14] 指南快速运行示例。如有任何困难，请访问 [文档][15] 或随时在 [论坛][16] 上联系支持团队。

## 也可以看看

* [用C#管理图片的EXIF数据][17]
* [用Java管理图像的EXIF数据][18]







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


