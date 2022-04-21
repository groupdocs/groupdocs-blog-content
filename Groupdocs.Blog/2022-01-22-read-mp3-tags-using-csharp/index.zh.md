---
title: "'使用 C# 读取 MP3 标签 - （ID3、歌词、APE) '"
date: Sat, 22 Jan 2022 12:49:38 +0000
draft: false
url: /zh/2022/01/22/read-mp3-tags-using-csharp/
author: 'Shoaib Khan'
summary: 'There are different metadata standards that are used with MP3 files. Various types of data can be stored using different standards. In this article, we will discuss how to read different MP3 tags using C#. Specifically, we will learn to extract ID3v1, ID3v2, Lyrics, and APEv2 metadata tags from the mp3 files within the .NET application.

本文涵盖以下主题：

* .NET API 来管理 MP3 标签
* 阅读 MP3 ID3 标签 - ID3v1 & ID3v2
* 获取 MP3 歌词标签
* 检索 MP3 APEv2 标签'
tags: ['read ID3 tags', 'read mp3 lyrics', 'Read MP3 tags', 'Read MP3 Tags CSharp']
categories: ['GroupDocs.Metadata Product Family']
---



{{< figure align=center src="images/mp3-icon.png" alt="mp3 - 提取其元数据 mp3 标签">}}


MP3 文件使用不同的元数据标准。可以使用不同的标准存储各种类型的数据。在本文中，我们将讨论**如何使用 C# 读取不同的 MP3 标签**。具体来说，我们将学习从 .NET 应用程序中的 mp3 文件中提取 ID3v1、ID3v2、歌词和 APEv2 元数据标签。

以下主题涵盖以下内容：

* [.NET API 来管理 MP3 标签](#mp3-tags-dotnet-api)
* [读取 MP3 ID3 标签 - ID3v1 & ID3v2](#read-mp3-id3-tags)
* [获取 MP3 歌词标签](#read-mp3-lyrics-tags)
* [检索 MP3 APEv2 标签](#read-mp3-ape-tags)

## MP3 标签编辑器的 .NET API {#mp3-tags-dotnet-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) 提供 .NET API 来自动化 [各种文件格式](https://docs.groupdocs.com/metadata/net/supported-document) 的元数据管理-formats/) 在 .NET 应用程序中。 API 允许读取、更新、添加、清理和删除许多文件格式的元数据。我们将使用这个 API 来处理 MP3 文件的元数据标签。

您可以从 [下载部分](https://downloads.groupdocs.com/metadata) 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.metadata)。

```
PM> Install-Package GroupDocs.Metadata
```

## 使用 C# 读取 MP3 ID3 标签 - ID3v1 & ID3v2 {#read-mp3-id3-tags}

以下步骤显示如何使用 C# 读取 MP3 ID3v1 标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) 类加载 MP3 文件。
* 使用 **GetRootPackage()** 方法检索 [根包](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage)。
* 从根目录中，您可以检索每个 ID3v1。

以下 C# 源代码读取 MP3 文件的一些 MP3 ID3v1 标签。

```
// 读取 MP3 文件 ID3V1 标签
using (Metadata metadata = new Metadata(Constants.MP3WithID3V1))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.ID3V1 != null)
    {
        Console.WriteLine(root.ID3V1.Album);
        Console.WriteLine(root.ID3V1.Artist);
        Console.WriteLine(root.ID3V1.Title);
        Console.WriteLine(root.ID3V1.Version);
        Console.WriteLine(root.ID3V1.Comment);
    }
}
```

同样，您可以提取 ID3v2 标签。以下步骤显示如何使用 C# 检索 MP3 ID3v2 标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) 类加载 MP3 文件。
* 获取[根包](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage)。
* 从根目录中，您可以检索所有 ID3v2 标签，如乐队、艺术家、作曲家等。
* 对于附加图片及其详细信息，请使用 AttachedPictures 属性。

下面的 C# 源代码示例读取 MP3 文件的一些 MP3 ID3v2 标签和附加图片详细信息。

```
// 读取 MP3 文件 ID3V2 标签
using (Metadata metadata = new Metadata(Constants.MP3WithID3V2))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.ID3V2 != null)
    {
        Console.WriteLine(root.ID3V2.Album);
        Console.WriteLine(root.ID3V2.Artist);
        Console.WriteLine(root.ID3V2.Band);
        Console.WriteLine(root.ID3V2.Title);
        Console.WriteLine(root.ID3V2.Composers);
        Console.WriteLine(root.ID3V2.Copyright);
        Console.WriteLine(root.ID3V2.Publisher);
        Console.WriteLine(root.ID3V2.OriginalAlbum);
        Console.WriteLine(root.ID3V2.MusicalKey);

        if (root.ID3V2.AttachedPictures != null)
        {
            foreach (var attachedPicture in root.ID3V2.AttachedPictures)
            {
                Console.WriteLine(attachedPicture.AttachedPictureType);
                Console.WriteLine(attachedPicture.MimeType);
                Console.WriteLine(attachedPicture.Description);
            }
        }
    }
}
```

## 在 C# 中读取 MP3 歌词标签 {#read-mp3-lyrics-tags}

以下步骤指导使用 C# 读取 MP3 歌词标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) 类加载 MP3 文件。
* 检索[根包](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage)。
* 从根目录中，您可以获取歌词标签及其属性，如歌词、艺术家等。

以下 C# 代码片段从 MP3 文件中检索 MP3 歌词标签及其一些属性。

```
// 读取 MP3 文件歌词标签
using (Metadata metadata = new Metadata(Constants.MP3WithLyrics))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.Lyrics3V2 != null)
    {
        Console.WriteLine(root.Lyrics3V2.Lyrics);
        Console.WriteLine(root.Lyrics3V2.Album);
        Console.WriteLine(root.Lyrics3V2.Artist);
        Console.WriteLine(root.Lyrics3V2.Track);

        // Alternatively, you can loop through a full list of tag fields
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## 在 C# 中读取 MP3 APEv2 标签 {#read-mp3-ape-tags}

以下步骤展示了我们如何使用 C# 提取 MP3 APEv2 标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) 类加载 MP3 文件。
* 使用 **GetRootPackage()** 方法检索 **root 包**。
* 从根目录，您可以检索所有 APEv2 标签，如专辑、流派、版权、语言等。

以下 C# 代码示例读取 MP3 文件的 MP3 APE 标记的一些属性。

```
// 读取 MP3 文件 APE 标签
using (Metadata metadata = new Metadata(Constants.MP3WithApe))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.ApeV2 != null)
    {
        Console.WriteLine(root.ApeV2.Album);
        Console.WriteLine(root.ApeV2.Title);
        Console.WriteLine(root.ApeV2.Artist);
        Console.WriteLine(root.ApeV2.Composer);
        Console.WriteLine(root.ApeV2.Copyright);
        Console.WriteLine(root.ApeV2.Genre);
        Console.WriteLine(root.ApeV2.Language);
    }
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

最后，我们学会了使用 C# 从 MP3 文件中提取元数据标签。我们从 MP3 文件中读取 ID3v1、ID3v2、歌词和 APE 标签及其属性。您可以从 [文档](https://docs.groupdocs.com/metadata/net/) 了解有关 API 的更多信息，并通过 [论坛](https://forum.groupdocs.com/) 联系我们进行查询.

## 也可以看看

* [使用 C# 的文档和图像的元数据删除器](https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/)
* [在 C# 中提取 WAV 文件的 RIFF INFO 和元数据](https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/)
* [使用 C# 管理 HEIF/HEIC 图像的 XMP 和 EXIF 数据](https://blog.groupdocs.com/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/)
* [在 C# .NET 中管理图像的 EXIF 数据](https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/)





