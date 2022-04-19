---
title: "'使用 C# 删除 MP3 标签'"
date: Thu, 06 Jan 2022 05:27:00 +0000
draft: false
url: /zh/2022/01/06/remove-mp3-tags-using-csharp/
author: 'Shoaib Khan'
summary: '[MP3](https://docs.fileformat.com/audio/mp3/) 文件可能包含各种标准的元数据。有时您不需要某些元数据信息。我们可以通过编程方式快速删除这些元数据 MP3 标签。在本文中，我们将讨论**如何使用 C# 删除不同的 MP3 标签**。准确地说，我们将学习从 .NET 应用程序中的 mp3 文件中删除 ID3v1、ID3v2、Lyrics 和 APEv2 元数据标签。

本文涵盖以下主题：

* .NET API 删除 MP3 标签
* 删除 MP3 ID3 标签 - ID3、歌词、APE
* C# 代码示例'
tags: ['Remove APE', 'Remove Metadata in CSharp', 'Remove MP3 ID3', 'Remove MP3 Metadata', 'Remove MP3 Tags', 'Remove MP3 Tags in CSharp']
categories: ['GroupDocs.Metadata Product Family']
---

[MP3](https://docs.fileformat.com/audio/mp3/) 文件可能包含各种标准的元数据。有时您不需要某些元数据信息。我们可以通过编程方式快速删除这些元数据 MP3 标签。在本文中，我们将讨论**如何使用 C# 删除不同的 MP3 标签**。准确地说，我们将学习从 .NET 应用程序中的 mp3 文件中删除 ID3v1、ID3v2、Lyrics 和 APEv2 元数据标签。

以下主题涵盖以下内容：

* [.NET API 删除 MP3 标签](#mp3-tags-dotnet-api)
* [删除 MP3 ID3 标签 - ID3、歌词、APE](#remove-mp3-tags)
* [C# 代码示例](#source-code-remove-mp3-tags)

## 用于 MP3 标签删除的 .NET API {#mp3-tags-dotnet-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) 展示了[元数据管理 .NET API](https://products.groupdocs.com/metadata/net/) 以处理 . NET 应用程序。 API 允许读取、更新、添加、清理和完全删除许多文件格式的元数据。我们将使用此 API 删除 MP3 文件的元数据标签。

您可以从 [下载部分](https://downloads.groupdocs.com/metadata)下载 **DLL** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.metadata) 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Metadata
```

## 使用 C# 删除 MP3 标签 - ID3v1、ID3v2、歌词、APE {#remove-mp3-tags}

以下步骤将允许您快速从 C# 中的 MP3 文件中删除 MP3 元数据标记。

1. **加载** MP3 文件。
2. 获取 **MP3 根包**。
3. **删除**相关的 MP3 标签。
4. **保存**更新的 MP3 文件。

### 1。 **加载 MP3**

选择 MP3 文件并使用 [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata) 类加载它。

```
Metadata metadata = new Metadata("path/mp3File.mp3");
```

### 2。获取 MP3 根包

使用[GetRootPackage()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage/index) 方法。

```
var root = metadata.GetRootPackage();
```

### 3。删除 MP3 标签

从以下删除不同元数据标签的方法中，您可以使用相关的删除策略。

#### **ID3v**1

要删除 **ID3v1** 元数据标签，请设置根包的 [ID3V1](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/id3v1) 属性为空。

```
root.ID3V1 = null;
```

#### **ID3v2**

要删除 **ID3v2** 元数据标签，请取消 [ID3V2](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/id3v2) 属性。

```
root.ID3V2 = null;
```

#### **歌词**

通过将 [Lyrics3V2](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/lyrics3v2) 属性设置为 null 来移除 **Lyrics** 标签。

```
root.Lyrics3V2 = null;
```

#### ****猿****

使用根包的[RemoveApeV2()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/methods/removeapev2)方法去除**APEv2**标签。

```
root.RemoveApeV2();
```

### 4。保存文件

最后，使用 [Save()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index) 方法**保存**更新的 MP3 文件。

```
metadata.Save("path/mp3TagsRemoved.mp3");
```

## 完整代码 - 删除 {#source-code-remove-mp3-tags}

以下源代码示例显示了如何在 C# 中从 MP3 文件中删除相关的 MP3 标签。

```
// 从 C# 中的 MP3 文件中删除 MP3 元数据标签 - ID3v1、ID3v2、歌词、APE
using (Metadata metadata = new Metadata("path/mp3File.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Use the relevant MP3 Tag propertie(s)
    root.ID3V1 = null;
    root.ID3V2 = null;
    root.Lyrics3V2 = null;
    root.RemoveApeV2();

    metadata.Save("path/mp3TagsRemoved.mp3");
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

总而言之，我们学会了使用 C# 从 MP3 文件中删除元数据标签。我们专门从 MP3 文件中删除了 ID3v1、ID3v2、歌词和 APE 标签。您可以从 [文档](https://docs.groupdocs.com/metadata/net/) 了解有关 API 的更多信息，并通过 [论坛](https://forum.groupdocs.com/) 联系我们进行查询.

## 也可以看看

* [使用 C# 读取 MP3 标签 – (ID3, Lyrics, APE)](https://blog.groupdocs.com/2022/01/22/read-mp3-tags-using-csharp/)
* [在 C# 中提取 WAV 文件的 RIFF INFO 和元数据](https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/)
* [使用 C# 管理 HEIF/HEIC 图像的 XMP 和 EXIF 数据](https://blog.groupdocs.com/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/)