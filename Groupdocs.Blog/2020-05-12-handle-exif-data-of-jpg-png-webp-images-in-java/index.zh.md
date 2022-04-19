---
title: "用 Java 管理 JPEG、PNG、TIFF 和 WebP 图像的 EXIF 数据"
date: Tue, 12 May 2020 07:09:04 +0000
draft: false
url: /zh/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
author: 'Shoaib Khan'
summary: "**EXIF**（_Exchangeable Image File Format_）是指定数码相机和扫描仪主要使用的图像和声音格式的标准。 EXIF 数据包括有关捕获的图像文件的标记和元数据信息。元数据可能包含相机制造商、型号、快门速度、日期和时间、光圈、曝光时间、X 分辨率、Y 分辨率等信息。等等"
tags: ['exif data', 'exif data of jpeg in java', 'exif metadata', 'exif metadata in java', 'extract exif data', 'extract exif data in java', 'remove exif data from images', 'remove exif metadata', 'update exif']
categories: ['GroupDocs.Metadata Product Family']
---

**EXIF**（_Exchangeable Image File Format_）是指定数码相机和扫描仪主要使用的图像和声音格式的标准。 EXIF 数据包括有关捕获的图像文件的标记和元数据信息。元数据可能包含相机制造商、型号、快门速度、日期和时间、光圈、曝光时间、X 分辨率、Y 分辨率等信息。等等

如果您想**以编程方式管理、提取、更新或删除图像的 EXIF 数据**，那么本文适合您。本文将介绍以下在 Java 中处理 EXIF 数据的方法：

* [提取 EXIF 数据 - EXIF 数据查看器][1]
* [从图像中提取所有 EXIF 标签][2]
* [更新 EXIF 属性][3]
* [删除 EXIF 元数据][4]

## Java 元数据操作库



{{< figure align=center src="images/GroupDocs.MetaData_for_Java.png" alt="GroupDocs 的元数据 Java API">}}


[GroupDocs.Metadata for Java][5] 是一个易于使用的元数据管理 Java API。它不仅可以从 JPG、PNG 或 WebP 等图像中提取元数据，还可以通过不同的选项从图像和其他文档中添加、编辑、更新和删除元数据。

我在本文中使用此 API，因此请确保 [下载][6] 或将其集成到您的基于 Maven 的应用程序中，只需将以下配置添加到 pom.xml。

### 存储库```
<repository>
<id>GroupDocsJavaAPI</id>
<name>GroupDocs Java API</name>
<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

### Dependency```
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>20.5</version>
    <classifier>javadoc</classifier>
</dependency>
```

## 从 Java 中的图像中提取 EXIF 数据 - 元数据查看器 {#extract-exif-data-from-images}

您可以通过以下简单步骤读取 EXIF 数据属性。让我们从这张埃菲尔铁塔的图片中提取EXIF数据开始。我选择了一个 JPG 文件作为示例图像，您可以使用任何文件，无论是 PNG、WebP、BMP、GIF 还是 TIFF。



{{< figure align=center src="images/eiffel-tower.jpg" alt="EXIF 数据的埃菲尔铁塔图片">}}


* 使用 [Metadata][7] 类构造函数加载包含 EXIF 数据信息的图像源文件。
* 通过调用 [getRootPackage()][8] 方法获取它的**根包**。
* 从根包中，通过调用 [getExifPackage()][9] 方法获取其**EXIF 包**。
* 获得 EXIF 包后，您可以获得图像 EXIF 属性，如 **Make**、**Model**、**Width**、**Length**、**Date-Time** 等，如图所示在下面的 Java 代码示例中。

```
// Extract EXIF Data Package Information from image in Java
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
	IExif root = (IExif) metadata.getRootPackage();
	if (root.getExifPackage() != null) {
		// Extract EXIF Package
		ExifPackage exifPackage = root.getExifPackage();
		System.out.println("Make : " + exifPackage.getMake());
		System.out.println("Model : " + exifPackage.getModel());
		System.out.println("Width : " + exifPackage.getImageWidth());
		System.out.println("Length : " + exifPackage.getImageLength());
		System.out.println("DateTime : " + exifPackage.getDateTime());					
	} 
}
```

这是您将通过上述代码获得的 EXIF 信息。

```
Make : NIKON CORPORATION
Model : NIKON D3000
Width : 640
Length : 424
DateTime : 2014:08:09 10:35:13
```

如需更多**IFD**（图像文件目录）和**GPS**（全球定位系统）包信息，您只需调用**EXIF包**的相应方法，即[getExifIfdPackage()][10]或 [getGpsPackage()][11]。从这些包中，您可以提取更多信息，例如；

* 图像采集设备**序列号**
* 相机 **机主姓名**
* **用户评论**
* **海拔**
* **纬度**
* **经度**
* ETC。

这是您可以在上述方法中添加的代码，以显示 EXIF 数据以及 IFD 和 GPS 信息。

```
// EXIF IFD Package
ExifIfdPackage exifIfdPackage = exifPackage.getExifIfdPackage();
System.out.println("BodySerialNumber : " + exifIfdPackage.getBodySerialNumber());
System.out.println("CameraOwnerName : " + exifIfdPackage.getCameraOwnerName());
System.out.println("UserComment : " + exifIfdPackage.getUserComment());
// EXIF GPS Information Package
ExifGpsPackage exifGpsPackage = exifPackage.getGpsPackage();
System.out.println("getAltitude : " + exifGpsPackage.getAltitude());
System.out.println("Latitude Ref : " + exifGpsPackage.getLatitudeRef());
System.out.println("LongitudeRef : " + exifGpsPackage.getLongitudeRef());
```

## 使用 Java 读取图像的所有 EXIF 标签 {#extract-all-exif-tags-from-images}

如果您想显示或提取任何图像或文件的所有 EXIF 属性，您可以按照与上述示例类似的步骤进行操作：

* 只需使用 [Metadata][12] 构造函数加载文件。
* 通过调用方法[getRootPackage()][13]获取**EXIF根包**。
* 通过调用 [getExifPackage()][14] 方法获取**EXIF 包**。
* 遍历 EXIF 包以获得所需的名称-值对。
* 同样，获取 IFD 和 GPS 包并显示其键和值。

```
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
	IExif root = (IExif) metadata.getRootPackage();
	if (root.getExifPackage() != null) {
		String pattern = "%s = %s";
		// Reading all EXIF tags.
		for (TiffTag tag : root.getExifPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
		// Extract all EXIF IFD tags.
		for (TiffTag tag : root.getExifPackage().getExifIfdPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
		// Extract all EXIF GPS tags
		for (TiffTag tag : root.getExifPackage().getGpsPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
	}
}
```

## 在 Java 中更新 EXIF 属性 {#update-exif-properties}

您甚至可以轻松更改任何图像或任何文档的现有 EXIF 数据。步骤很简单：

### **更新 EXIF 包**

* 通过调用[getExifPackage()][15]方法获取EXIF包。
* 使用 setter 方法，例如；
    * [setCopyright()][16] - 设置更新的版权信息。
    * [setImageDescription()][17] - 设置图像的描述。
* 同样，您可以设置艺术家、品牌、型号、软件、图像宽度和高度、日期、时间等的值。

### **更新 EXIF IFD 包**

就像更新 EXIF 包一样，您可以更新 EXIF IFD 和 GPS 包的属性。请访问 [ExifIfdPackage][18] 或 [ExifGpsPackage][19] 课程，了解您可以为有价值的图像和文档定制多少。

```
// Update/Set new values in EXIF Data (EXIF Package and EXIF IFD Package).
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    // Set the EXIF package if it's missing
    if (root.getExifPackage() == null) {
        root.setExifPackage(new ExifPackage());
    }
    ExifPackage exifPackage = root.getExifPackage();
    // Setting the desired values in EXIF Package and EXIF IFD Package.
    exifPackage.setCopyright("Copyright (C) 2011-2020 GroupDocs. All Rights Reserved.");
    exifPackage.setImageDescription("Eiffel Tower for EXIF");
    exifPackage.setSoftware("GroupDocs.Metadata");
    exifPackage.getExifIfdPackage().setBodySerialNumber("GD-2020");
    exifPackage.getExifIfdPackage().setCameraOwnerName("GroupDocs");
    exifPackage.getExifIfdPackage().setUserComment("Nice image captured in 2014");
    metadata.save("eiffel-tower-updated.jpg");
}
```

## 从 Java 中的图像中删除 EXIF 元数据 {#remove-exif-metadata}

如果您想从任何文件中删除 EXIF 包，这非常简单，只需通过调用根包的 [setExifPackage(null)][20] 将其 EXIF 包设置为 null。

```
// Removing the EXIF data from an image.
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    root.setExifPackage(null);
    metadata.save("eiffel-tower-no-exif.jpg");
}
```

## 支持的图像和其他格式

以下是 GroupDocs.Metadata 当前支持的文件格式。您可以随时访问 [文档][21] 以获取更新信息。

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td> **文件类型</td><td><strong>文件格式**</strong></td></tr><tr><td><a href="https://wiki.fileformat.com/image/">图片</a></td><td>BMP、GIF、JPG、JPEG、JPE、JP2、PNG、DJVU、DWG、DXF、WebP、TIFF、PSD、EMF、WMF</td></tr><tr><td><a href="https://wiki.fileformat.com/audio">音频</a>和<a href="https://wiki.fileformat.com/video/">视频</a></td><td>MP3、WAV、AVI、MOV/QT、FLV、ASF、DICOM</td></tr></tbody></table></figure>

## 查看有关 GroupDocs.Metadata 的更多信息

* [文档][22]
* 源代码示例。 [爪哇][23] | [.NET][24]
* GroupDocs.Metadata – [元数据管理解决方案][25]

**让我们多谈谈@** [免费支持论坛。][26]

## 相关文章

* [用C#管理图片的EXIF数据][27]







[1]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#update-exif-properties
[2]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#extract-all-exif-tags-from-images
[3]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#update-exif-properties
[4]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#remove-exif-metadata
[5]: https://products.groupdocs.com/metadata/java
[6]: https://downloads.groupdocs.com/metadata/java
[7]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IExif#getExifPackage()
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#getGpsPackage()
[12]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[13]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
[14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#setCopyright(java.lang.String)
[17]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#setImageDescription(java.lang.String)
[18]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[19]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifGpsPackage
[20]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IExif#setExifPackage(com.groupdocs.metadata.core.ExifPackage)
[21]: https://docs.groupdocs.com/display/metadatajava/Supported+File+Formats
[22]: https://docs.groupdocs.com/display/metadatajava/Getting+Started
[23]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
[24]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET
[25]: https://products.groupdocs.com/metadata
[26]: https://forum.groupdocs.com/c/metadata
[27]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/


