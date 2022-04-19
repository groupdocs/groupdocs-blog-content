---
title: "在 Java 中提取 WAV 文件的 RIFF INFO 和元数据"
date: Mon, 22 Mar 2021 16:37:44 +0000
draft: false
url: /zh/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/
author: 'Shoaib Khan'
summary: "**RIFF** 文件容器格式，用于存储音频和视频多媒体。存储在块中的这些数据可以包括许多信息，例如创建日期、版权信息、艺术家、评论等。您可以以编程方式操作元数据以及 RIFF 信息。本文指导开发人员**以编程方式从 Java 中的 WAV 音频文件中提取元数据和 RIFF INFO**。"
tags: ['extract metadata in java', 'Extract Metadata of WAV file in Java', 'Extract RIFF INFO of WAV in Java']
categories: ['GroupDocs.Metadata Product Family']
---

**RIFF** 文件容器格式，用于存储音频和视频多媒体。存储在块中的这些数据可以包括许多信息，例如创建日期、版权信息、艺术家、评论等。您可以以编程方式操作元数据以及 RIFF 信息。本文指导开发人员**以编程方式从 Java 中的 WAV 音频文件中提取元数据和 RIFF INFO**。

本文简要介绍了以下主题：

* [用于元数据管理的 Java API][2]
* [用Java提取WAV文件的元数据][3]
* [用Java提取WAV文件的RIFF信息][4]

## 用于管理元数据和 RIFF INFO 的 Java API {#metadata-management-java-api}

[GroupDocs.Metadata for Java][5] 是用于各种文档和图像文件格式的元数据自动化和操作 API。我将使用这个 API 从 WAV 文件中提取元数据和 RIFF INFO。除了音频 WAV 文件外，该 API 还支持从 **MP3 文件** 和 **videos** 添加、删除、更新和提取元数据。此外，它还支持**Microsoft Office** 和**Open Office** 文件格式、**eBooks**、**images** 和许多其他文档格式。

### 下载并配置

[从下载中获取库][6] 或在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置以尝试以下示例。有关详细信息，您可以访问 [API 参考][7]。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>21.2</version> 
</dependency>
```

## 在 Java 中提取 WAV 文件的元数据 {#extract-metadata-of-wav-audio-in-java}

以下步骤和下面提到的 Java 代码示例提取 WAV 文件的元数据。

* 加载 WAV 音频文件。
* 获取元数据的[WavRootPackage][8]。
* 使用 _getWavPackage_ 方法提取 [WavPackage][9]。
* 现在您可以访问 WAV 音频的所有属性。

```
// 用Java提取WAV文件的元数据
try (Metadata metadata = new Metadata("audio.wav"))
{
    WavRootPackage root = metadata.getRootPackageGeneric();
    System.out.println(root.getWavPackage().getBitsPerSample()); // Bits per Sample
    System.out.println(root.getWavPackage().getBlockAlign()); // Block Align
    System.out.println(root.getWavPackage().getByteRate()); // Byte Rate
    System.out.println(root.getWavPackage().getNumberOfChannels()); // No. of Channels
    System.out.println(root.getWavPackage().getAudioFormat()); // Audio Format
    System.out.println(root.getWavPackage().getSampleRate()); // Sample Rate
}
```

上面的代码使用提供的 wav 文件生成以下输出：

```
Bits per Sample: 16
Block Align: 4
Byte Rate: 176400
Number of Channels: 2
Audio Format: 1
Sample Rate: 44100
```

## 在 Java 中提取 WAV 文件的 RIFF INFO {#extract-riff-info-of-wav-audio-in-java}

如果您想提取 WAV 文件的 RIFF INFO，您可以使用这些步骤在您的 Java 应用程序中获取它。这类似于我们提取上面显示的元数据的方式。

* 加载 WAV 文件。
* 获取元数据的[WavRootPackage][10]。
* 从根包中提取 [RiffInfoPackage][11]。
* 现在可以访问 WAV 音频的属性。

以下代码示例提取 Java 中 WAV 文件的 RIFF INFO 包元数据属性。

```
// 在 Java 中提取 WAV 文件的 RIFF INFO
try (Metadata metadata = new Metadata("audio.wav"))
{
    WavRootPackage root = metadata.getRootPackageGeneric();
    System.out.println(root.getRiffInfoPackage().getArtist()); // Artist
    System.out.println(root.getRiffInfoPackage().getComment()); // Comment
    System.out.println(root.getRiffInfoPackage().getCopyright()); // Copyright
    System.out.println(root.getRiffInfoPackage().getCreationDate()); // Creation Date
    System.out.println(root.getRiffInfoPackage().getSoftware()); // Software
    System.out.println(root.getRiffInfoPackage().getEngineer()); // Engineer
    System.out.println(root.getRiffInfoPackage().getGenre()); // Genre
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

在本文中，我们讨论了如何以编程方式从 Java 中的 WAV 音频文件中提取元数据和 RIFF INFO。我希望你觉得它很简单。现在，您可以使用 GroupDocs.Metadata for Java 构建您自己的元数据提取器 Java 应用程序。

## 有关 API 的更多信息

* [文档][12]
* [源代码示例][13]
* [API 参考][14]

**让我们清除任何疑问@** [免费支持论坛。][15]

## 也可以看看

* [在 C# 中提取 WAV 文件的 RIFF INFO 和元数据][16]
* [用Java管理图像的EXIF数据][17]







[1]: https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java
[2]: #metadata-management-java-api
[3]: #extract-metadata-of-wav-audio-in-java
[4]: #extract-riff-info-of-wav-audio-in-java
[5]: https://products.groupdocs.com/metadata/java
[6]: https://downloads.groupdocs.com/metadata/java
[7]: https://apireference.groupdocs.com/metadata/java
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/WavRootPackage
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/WavPackage
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/WavRootPackage
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/RiffInfoPackage
[12]: https://docs.groupdocs.com/metadata/java/
[13]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
[14]: https://apireference.groupdocs.com/metadata/java
[15]: https://forum.groupdocs.com/c/metadata
[16]: https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
[17]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


