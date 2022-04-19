---
title: "'删除 Java 中的 MP3 标签'"
date: Sun, 30 Jan 2022 05:05:23 +0000
draft: false
url: /zh/2022/01/30/remove-mp3-tags-in-java/
author: 'Shoaib Khan'
summary: '当元数据不是真正需要时，您可以消除它。在本文中，我们将学习**如何以编程方式在 Java 中删除不同的 MP3 标签。** 准确地说，我们将看到从 Java 应用程序中的 mp3 文件中删除 ID3v1、ID3v2、Lyric 和 APEv2 元数据标签。

以下主题涵盖以下内容：

* MP3 标签的 Java API
* 删除 MP3 ID3 标签 - ID3、歌词、APE
* Java 代码 - 删除 MP3 元数据示例'
tags: ['Remove APE', 'Remove Metadata in Java', 'Remove MP3 ID3', 'Remove MP3 Metadata', 'Remove MP3 Tags', 'Remove MP3 Tags in Java']
categories: ['GroupDocs.Metadata Product Family']
---

当元数据不是真正需要时，您可以消除它。在本文中，我们将学习**如何以编程方式在 Java 中删除不同的 MP3 标签。** 准确地说，我们将看到从 Java 应用程序中的 mp3 文件中删除 ID3v1、ID3v2、Lyric 和 APEv2 元数据标签。

以下主题涵盖以下内容：

* [用于 MP3 标签的 Java API](#mp3-tags-java-api)
* [删除 MP3 ID3 标签 - ID3、歌词、APE](#remove-mp3-tags)
* [Java 代码 - 删除 MP3 元数据示例](#source-code-remove-mp3-tags)

## 用于 MP3 标签删除的 Java API {#mp3-tags-java-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) 提供[元数据管理Java API](https://products.groupdocs.com/metadata/java/) 来处理不同文件格式的元数据。 **GroupDocs.Metadata for Java** 允许读取、更新、添加、清理和完全删除[各种文件格式](https://docs.groupdocs.com/metadata/java/supported-document-formats/)的元数据。我将使用这个 API 来删除 MP3 文件的元数据标签。

### 下载或配置

您可以从 [下载部分](https://downloads.groupdocs.com/metadata) 下载 **JAR** 文件，或者只获取基于 **maven 的 pox.xml 的存储库和依赖项配置** Java 应用程序。

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

## 删除 Java 中的 MP3 标签 - ID3v1、ID3v2、歌词、APE {#remove-mp3-tags}

以下步骤将允许您快速从 Java 中的 MP3 文件中删除 MP3 元数据标签。

1. **加载** MP3 文件。
2. 获取 **MP3 根包**。
3. **删除**相关的 MP3 标签。
4. **保存**更新的 MP3 文件。

### 1。 **加载 MP3**

选择 MP3 文件并使用 [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) 类加载它。

```
Metadata metadata = new Metadata("path/mp3File.mp3");
```

### 2。获取 MP3 根包

使用[getRootPackageGeneric()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackageGeneric()) 方法。

```
MP3RootPackage root = metadata.getRootPackageGeneric();
```

### 3。删除 MP3 标签

以下是删除不同元数据标签的方法。您可以对 MP3 文件使用相关的删除方法。

#### **ID3v**1

要删除 **ID3v1** 元数据标签，请将根包的 [ID3V1](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V1Tag) 属性设置为 null。

```
root.setID3V1(null);
```

#### **ID3v2**

将 [ID3V2](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V2Tag) 属性设置为 null 以删除 **ID3v2** 元数据标签。

```
root.setID3V2(null);
```

#### **歌词**

通过将 [Lyrics Tag](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/LyricsTag) 设置为 null 来移除 **Lyrics** 标签。

```
root.setLyrics3V2(null);
```

#### **猿**

使用根包的[removeApeV2()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage#removeApeV2())方法去除**APEv2**标签。

```
root.removeApeV2();
```

### 4。保存文件

最后，使用 [save()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save()) 方法**保存**更新的 MP3 文件。

```
metadata.save("path/mp3TagsRemoved.mp3");
```

## 完整代码 - 删除 MP3 标签 {#source-code-remove-mp3-tags}

以下 Java 源代码示例显示了如何从 MP3 文件中删除相关的 MP3 标签。

```
// 从 C# 中的 MP3 文件中删除 MP3 元数据标签 - ID3v1、ID3v2、歌词、APE
Metadata metadata = new Metadata("path/mp3File.mp3")

MP3RootPackage root = metadata.getRootPackageGeneric();
root.setID3V1(null); // delete ID3v1
root.setID3V2(null); // delete ID3v2
root.setLyrics3V2(null); // delete Lyrics3v2
root.removeApeV2(); // delete APE

metadata.save("path/mp3TagsRemoved.mp3");
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

总而言之，我们学会了使用 Metadata API 从 Java 中的 MP3 文件中删除元数据标签。我们一一研究了如何从 MP3 文件中删除 ID3v1、ID3v2、歌词和 APE 标签。

您可以从 [文档](https://docs.groupdocs.com/metadata/java/) 了解有关 API 的更多信息。通过 [论坛](https://forum.groupdocs.com/) 联系我们进行查询。

## 也可以看看

* [使用 Java 的文档和图像元数据清理器](https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/)
* [用Java提取WAV文件的RIFF INFO和元数据](https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/)
* [使用 Java 管理 HEIF/HEIC 图像的 XMP 和 EXIF 数据](https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java/)





