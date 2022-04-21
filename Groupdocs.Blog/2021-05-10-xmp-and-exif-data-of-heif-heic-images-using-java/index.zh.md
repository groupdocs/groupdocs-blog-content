---
title: "使用 Java 管理 HEIF/HEIC 图像的 XMP 和 EXIF 数据"
date: Mon, 10 May 2021 08:20:00 +0000
draft: false
url: /zh/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java/
author: 'Shoaib Khan'
summary: "**HEIC** 代表高效图像容器。它是某些苹果设备捕获的图像的文件扩展名。它是一个可以包含 High-Efficiency Image Format **HEIF** 图像的容器。在本文中，我们将讨论**如何在 Java 应用程序中提取、更新和删除 HEIF/HEIC 图像的 EXIF 和 XMP 元数据**。"
tags: ['exif data', 'exif data in Java', 'exif data of heic in java', 'XMP data in Java', 'xmp data of heic in java', 'XMP metadata']
categories: ['GroupDocs.Metadata Product Family']
---

**HEIC** 代表高效图像容器。它是某些苹果设备捕获的图像的文件扩展名。它是一个可以包含 High-Efficiency Image Format **HEIF** 图像的容器。在本文中，我们将讨论**如何在 Java 应用程序中提取、更新和删除 HEIF/HEIC 图像的 EXIF 和 XMP 元数据**。

**EXIF**，可交换图像文件格式是定义如何以最常见的图像和音频格式存储元数据属性的标准。 **XMP** 是基于 XML 的元数据标准，可以将任何元数据属性集存储为名称/值对。

下面介绍了以下主题

* [用于 EXIF、XMP 数据的元数据 Java API][2]
* [读取 HEIC/HEIF 图像的 EXIF 数据][3]
* [读取 HEIC/HEIF 图像的 XMP 数据][4]

## 用于 EXIF 和 XMP 元数据的 Java API {#java-api-for-exif-and-xmp-metadata}

[GroupDocs.Metadata][5] 为您的 Java 应用程序提供元数据操作 API。 API 允许读取、更新、添加、清理/删除和遍历许多文件格式的功能。它支持各种元数据标准，如 EXIF、IPTC 和 XMP。文字处理文档、电子表格、演示文稿、电子邮件信息、电子书、图像、AutoCAD 绘图、音频和视频文件、种子文件都属于受支持的文档格式。更准确地说，您可以访问文档以获取[支持的元数据操作文件格式][6] 的完整列表。

### 下载并配置

从 [下载][7] 部分获取元数据库。对于基于 Maven 的 Java 应用程序，只需添加以下 pom.xml 配置。在此之后，您可以尝试本文的示例以及 [GitHub][8] 上提供的更多示例。有关详细信息，您可以访问 [API 参考][9]。

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
        <version>21.4</version> 
</dependency>
```

## 用Java读取HEIF/HEIC图像的EXIF数据 {#read-exif-of-heic-heif-images}

以下是读取和提取 HEIC 和 HEIF 图像的 EXIF 数据的步骤。

* 使用元数据类加载 HEIF 或 HEIC 图像。
* 获取根包。
* 从根包中检索 EXIF 包。
* 从 EXIF 包中，您可以遍历 EXIF 数据属性。
* 此外，您可以从 EXIF 包中获取 IFD（图像文件目录）和 GPS 信息。

以下代码展示了如何使用 Java 获取 HEIC 图像的 EXIF 数据、IFD 和 GPS 元数据信息。

```
// 在 Java 中读取 HEIF / HEIC 图像的 EXIF、EXIF IFD、EXIF GPS 包
Metadata metadata = new Metadata("image.heic");
IExif root = (IExif) metadata.getRootPackage();
if (root.getExifPackage() != null) {
    String pattern = "%s : %s";
    // Get EXIF Package information
    for (TiffTag tag : root.getExifPackage().toList()) {
        System.out.println(String.format(pattern, tag.getName(), tag.getInterpretedValue()));
    }
    // Get EXIF IFD Package Information
    for (TiffTag tag : root.getExifPackage().getExifIfdPackage().toList()) {
        System.out.println(String.format(pattern, tag.getName(), tag.getInterpretedValue()));
    }
    // Get GPS information
    for (TiffTag tag : root.getExifPackage().getGpsPackage().toList()) {
        System.out.println(String.format(pattern, tag.getName(), tag.getInterpretedValue()));
    }
}
```

## 用 Java 读取 HEIC / HEIF 图像的 XMP 数据 {#read-xmp-of-heic-heif-images}

以下步骤读取 HEIC 或 HEIF 图像的 XMP 元数据。

* 使用元数据类加载 HEIF 或 HEIC 图像。
* 使用 getRootPackage 方法获取根包。
* 从根包中，您可以获得 XMP 的基本信息。
* 此外，您可以获得 DCMI 都柏林核心信息。
* 此外，您可以使用 getPhotoshop 方法获取 Photoshop 信息。

以下源代码显示了如何在 Java 中获取 XMP 基本、DCMI 和 Photoshop 信息。

```
// 在 Java 中提取 heic 和 heif 图像的 XMP Basic、DublinCore 和 Photoshop 数据
Metadata metadata = new Metadata("image.heic");
IXmp root = (IXmp) metadata.getRootPackage();

if (root.getXmpPackage() != null) {
    // XMP Basic    
    if (root.getXmpPackage().getSchemes().getXmpBasic() != null) {
        XmpBasicPackage xmpBasicPackage = root.getXmpPackage().getSchemes().getXmpBasic();
	System.out.println("Creator Tool : " + xmpBasicPackage.getCreatorTool());
	System.out.println("Create Date : " + xmpBasicPackage.getCreateDate());
	System.out.println("Modify Date : " + xmpBasicPackage.getModifyDate());
	System.out.println("Label : " + xmpBasicPackage.getLabel());
	System.out.println("Nick Name: " + xmpBasicPackage.getNickname());
	// ...
    }
    // DublinCore information
    if (root.getXmpPackage().getSchemes().getDublinCore() != null) {
	XmpDublinCorePackage xmpDublinCorePackage = root.getXmpPackage().getSchemes().getDublinCore();
	System.out.println("Format : " + xmpDublinCorePackage.getFormat());
	System.out.println("Coverage :" + xmpDublinCorePackage.getCoverage());
	System.out.println("Identifier : " + xmpDublinCorePackage.getIdentifier());
	System.out.println("Source : " + xmpDublinCorePackage.getSource());
	// ...
    }
    // Photoshop Information
    if (root.getXmpPackage().getSchemes().getPhotoshop() != null) {
	XmpPhotoshopPackage xmpPhotoshopPackage = root.getXmpPackage().getSchemes().getPhotoshop();
	System.out.println("Color Mode : " + xmpPhotoshopPackage.getColorMode());
	System.out.println("ICC Profile : " + xmpPhotoshopPackage.getIccProfile());
	System.out.println("Country : " + xmpPhotoshopPackage.getCountry());
	System.out.println("City : " + xmpPhotoshopPackage.getCity());
	System.out.println("Date Created : " + xmpPhotoshopPackage.getDateCreated());
	// ...
    }
}
```

同样，有许多 setter 方法可以设置或更新不同的 XMP 属性。您甚至可以提供自己的键值对来[设置自定义 XMP 包属性][10]。

## 在 Java 中删除 HEIC/HEIF 图像的 EXIF 和 XMP 元数据

您只需将相应的 EXIF 包或 XMP 包设置为 null 即可删除所有元数据属性。

以下代码删除 HEIC 图像的 EXIF 数据。

```
try (Metadata metadata = new Metadata("image.heic")) {
	IExif root = (IExif) metadata.getRootPackage();
	root.setExifPackage(null);
	metadata.save("no-exif-image.heic");
}
```

以下代码删除 HEIC 图像的 XMP 数据。

```
try (Metadata metadata = new Metadata("image.heic")) {
	IXmp root = (IXmp) metadata.getRootPackage();
	root.setXmpPackage(null);
	metadata.save("no-xmp-image.heic");
}
```

## 结论

综上所述，我们已经学会了从 Java 中的 HEIF/HEIC 图像中提取、更新、删除 EXIF 和 XMP 元数据。此外，您还了解了如何从这些图像中获取 IFD 和 GPS 信息。现在您可以轻松获取此信息，并继续构建您自己的应用程序，例如 GroupDocs.Metadata App Product Family 以自动化元数据信息。

有关更多信息、选项和示例，您可以访问 [文档][11] 和 [GitHub][12] 存储库。如需进一步查询，请通过支持 [论坛][13] 联系我们。

## 也可以看看

* [用Java提取WAV文件的RIFF INFO和元数据][14]
* [使用 Java 清理文档和图像的元数据][15]







[1]: https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java
[2]: #java-api-for-exif-and-xmp-metadata
[3]: #read-exif-of-heic-heif-images
[4]: #read-xmp-of-heic-heif-images
[5]: https://products.groupdocs.com/metadata
[6]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/metadata/java
[8]: https://github.com/groupdocs-metadata
[9]: https://apireference.groupdocs.com/metadata/java
[10]: https://docs.groupdocs.com/metadata/java/working-with-xmp-metadata/
[11]: https://docs.groupdocs.com/metadata/
[12]: https://github.com/groupdocs-metadata
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/
[15]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/


