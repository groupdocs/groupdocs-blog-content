---
title: "'用 Java 读取 MP3 标签 - （ID3、歌词、APE) '"
date: Sat, 12 Feb 2022 11:43:14 +0000
draft: false
url: /zh/2022/02/12/read-mp3-tags-in-java/
author: 'Shoaib Khan'
summary: "元数据变体附有不同文件格式的文档。 MP3 文件通常包含 ID3 元数据标签。本文讨论**如何在 Java 中读取不同的 MP3 标签**。我们将一一了解如何使用 Java 元数据 API 从 mp3 文件中提取 ID3（IDEv1、ID3v2) 、歌词和 APEv2 元数据标签。"
tags: ['read ID3 tags', 'read mp3 lyrics', 'Read MP3 tags', 'Read MP3 Tags in Java']
categories: ['GroupDocs.Metadata Product Family']
---

元数据变体附有不同文件格式的文档。 MP3 文件通常包含 ID3 元数据标签。本文讨论**如何在 Java 中读取不同的 MP3 标签**。我们将一一了解如何使用 Java 元数据 API 从 mp3 文件中提取 ID3（IDEv1、ID3v2) 、歌词和 APEv2 元数据标签。

以下主题涵盖以下内容：

* [管理 MP3 标签的 Java API](#mp3-tags-java-api)
* [读取 MP3 ID3 标签 - ID3v1 & ID3v2](#read-mp3-id3-tags)
* [获取 MP3 歌词标签](#read-mp3-lyrics-tags)
* [检索 MP3 APEv2 标签](#read-mp3-ape-tags)

## MP3 元数据标签的 Java API {#mp3-tags-java-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) 配备 API，可自动管理 [各种文件格式](https://docs.groupdocs.com/metadata/net/supported-document) 的元数据-formats/) 在应用程序中。它的 Java API 允许您读取、更新、添加、清理和删除 Java 应用程序中许多文件格式的元数据。我们将使用它来处理 MP3 元数据标签。

### 下载并配置

从 [下载](https://downloads.groupdocs.com/metadata/java) 部分获取元数据库。对于基于 Maven 的 Java 应用程序，只需添加以下 pom.xml 配置。在此之后，您可以尝试本文的示例以及 [GitHub](https://github.com/groupdocs-metadata) 上提供的更多示例。详情可访问 [API 参考](https://apireference.groupdocs.com/metadata/java)。

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

## 用 Java 读取 MP3 ID3 标签 - ID3v1 & ID3v2 {#read-mp3-id3-tags}

以下步骤展示了如何使用 Java 读取 MP3 ID3v1 标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) 类加载 MP3 文件。
* 使用 **getRootPackageGeneric()** 方法检索 [MP3RootPackage](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage)。
* 从根包中，检索每个 ID3v1 属性。

以下 Java 源代码读取 MP3 文件的一些 MP3 ID3v1 标签。

```
// 读取 MP3 文件 ID3V1 标签
try (Metadata metadata = new Metadata("path/audio-ID3V1.mp3")) {
	MP3RootPackage root = metadata.getRootPackageGeneric();
	if (root.getID3V1() != null) {

		System.out.println(root.getID3V1().getAlbum());
		System.out.println(root.getID3V1().getArtist());
		System.out.println(root.getID3V1().getTitle());
		System.out.println(root.getID3V1().getVersion());
		System.out.println(root.getID3V1().getComment());
		// ...
	}
}
```

您可以以类似的方式提取 ID3v2 标签。以下步骤显示了如何在 Java 中检索 MP3 ID3v2 标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) 类加载 MP3 文件。
* 获取[根包](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage)。
* 从根目录，您可以轻松检索所有 ID3v2 标签，如艺术家、作曲家、出版商、标题等。
* 附加图片的详细信息可以从 [附加图片框架](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V2AttachedPictureFrame) 的属性中检索。

以下 Java 源代码示例读取 MP3 文件的一些 MP3 ID3v2 标签和附加图片详细信息。

```
// 读取 MP3 文件 ID3V2 标签
try (Metadata metadata = new Metadata("path/audio-ID3V2.mp3")) {
    MP3RootPackage root = metadata.getRootPackageGeneric();
 
    if (root.getID3V2() != null) {
        System.out.println(root.getID3V2().getAlbum());
        System.out.println(root.getID3V2().getArtist());
        System.out.println(root.getID3V2().getBand());
        System.out.println(root.getID3V2().getTitle());
        System.out.println(root.getID3V2().getComposers());
        System.out.println(root.getID3V2().getCopyright());
        System.out.println(root.getID3V2().getPublisher());
        System.out.println(root.getID3V2().getOriginalAlbum());
        System.out.println(root.getID3V2().getMusicalKey());
 
        if (root.getID3V2().getAttachedPictures() != null) {
            for (ID3V2AttachedPictureFrame attachedPicture : root.getID3V2().getAttachedPictures()) {
                System.out.println(attachedPicture.getAttachedPictureType());
                System.out.println(attachedPicture.getMimeType());
                System.out.println(attachedPicture.getDescription()); 
            }
        }
    }
}
```

## 在 Java 中读取 MP3 歌词标签 {#read-mp3-lyrics-tags}

以下步骤指导如何在 Java 中读取 MP3 歌词标签。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) 类加载 MP3 文件。
* 检索[根包](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage)。
* 从根目录中，您可以获取歌词标签及其属性，如歌词、艺术家、曲目等。

以下 Java 代码片段从 MP3 文件中检索 MP3 歌词标签和一些属性。

```
// 读取 MP3 文件歌词标签
try (Metadata metadata = new Metadata("path/audio-Lyrics.mp3")) {
	MP3RootPackage root = metadata.getRootPackageGeneric();
	if (root.getLyrics3V2() != null) {
		System.out.println(root.getLyrics3V2().getLyrics());
		System.out.println(root.getLyrics3V2().getAlbum());
		System.out.println(root.getLyrics3V2().getArtist());
		System.out.println(root.getLyrics3V2().getTrack());
		// ...

    // Similarly, you can traverse the tag fields
		for (LyricsField field : root.getLyrics3V2().toList()) {
			System.out.println(String.format("%s = %s", field.getID(), field.getData()));
		}
	}
}
```

## 在 Java 中读取 MP3 APEv2 标签 {#read-mp3-ape-tags}

以下步骤展示了我们如何在 Java 应用程序中提取 MP3 APEv2 标记。

* 使用 [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata) 类加载 MP3 文件。
* 使用 ****getRootPackageGeneric**()** 方法检索 **[root 包](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage)**。
* 从根目录，您可以检索 APEv2 标签，如专辑、流派、版权、语言等。

以下 Java 代码示例读取 MP3 文件的 MP3 APE 标记的一些属性。

```
// 读取 MP3 文件 APE 标签
try (Metadata metadata = new Metadata("path/audio-APE.mp3")) {
	MP3RootPackage root = metadata.getRootPackageGeneric();

	if (root.getApeV2() != null) {
		System.out.println(root.getApeV2().getAlbum());
		System.out.println(root.getApeV2().getTitle());
		System.out.println(root.getApeV2().getArtist());
		System.out.println(root.getApeV2().getComposer());
		System.out.println(root.getApeV2().getCopyright());
		System.out.println(root.getApeV2().getGenre());
		System.out.println(root.getApeV2().getLanguage());
		// ...
	}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

综上所述，我们学习了如何从 Java 中的 MP3 文件中提取元数据标签。我们从 MP3 文件中一一读取 ID3v1、ID3v2、歌词和 APE 标签及其属性。考虑构建您自己的 MP3 在线标签编辑器和元数据查看器，就像 [在线元数据应用程序](https://products.groupdocs.app/metadata/total)。

从 [文档](https://docs.groupdocs.com/metadata/java/) 了解有关 API 的更多信息，并通过 [论坛](https://forum.groupdocs.com/) 联系我们进行查询。

## 也可以看看

* [使用 Java 的文档和图像元数据清理器](https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/)
* [删除 Java 中的 MP3 标签](https://blog.groupdocs.com/2022/01/30/remove-mp3-tags-in-java/)
* [使用 Java 管理 HEIF/HEIC 图像的 XMP 和 EXIF 数据](https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-爪哇/)
* [用Java提取WAV文件的RIFF INFO和元数据](https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/)





