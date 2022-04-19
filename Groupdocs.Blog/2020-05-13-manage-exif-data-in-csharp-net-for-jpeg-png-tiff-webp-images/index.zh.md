---
title: "在 C# .NET 中管理 JPEG、PNG、TIFF 和 WebP 图像的 EXIF 数据"
date: Wed, 13 May 2020 21:06:49 +0000
draft: false
url: /zh/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
author: 'Shoaib Khan'
summary: "在 [上一篇][1] 中，我们讨论了如何在 Java 中处理图像的 EXIF 数据。 在这里，今天我们将研究如何在 C# 中实现相同的目标。 如果您还没有访问过上一篇文章，但您想在 C#** 中以编程方式**提取、更新、添加或删除图像的 EXIF 数据，那么本文将指导您完成此操作。"
tags: ['change exif data of images', 'extract exif data', 'extract exif data in csharp', 'extract metadata from images', 'remove exif data from images']
categories: ['GroupDocs.Metadata Product Family']
---

在 [上一篇][2] 中，我们讨论了如何在 Java 中处理图像的 EXIF 数据。在这里，今天我们将研究如何在 C# 中实现相同的目标。如果您还没有访问过上一篇文章，但您想在 C#** 中以编程方式**提取、更新、添加或删除图像的 EXIF 数据，那么本文将指导您完成此操作。我们将介绍以下在 C# 中处理 EXIF 数据的方法：

* [读取EXIF数据][3]
* [从图像中读取所有 EXIF 标签][4]
* [更新EXIF属性][5]
* [删除EXIF元数据][6]

## 元数据管理 C# 库



{{< figure align=center src="images/GroupDocs.MetaData_for_NET.png" alt="GroupDocs 的元数据 .NET API">}}


[GroupDocs.Metadata for .NET][7] 是元数据管理 .NET API。它为各种受支持的文件格式提供了很长的 [功能][8] 列表。它不仅可以从图像中提取元数据，还可以通过各种选项从图像和文档中添加、编辑、更新和删除元数据。

在本文中，我们将使用此 API，因此请确保 [下载][9] 其二进制文件或从 [NuGet][10] 安装 API。

## 在 C# 中从图像中读取 EXIF 数据 {#extract-exif-data-from-images}

您可以按照上述步骤轻松读取 EXIF 数据属性。从这张图片中提取EXIF数据开始，93m高的自由女神像。在这里，我们将使用 JPG 文件作为示例图像，但是，我们可以使用任何文件，无论是 PNG、WebP、BMP、GIF、TIFF 或任何其他 [支持的文件格式][11] 末尾提到的本文。



{{< figure align=center src="images/statue-of-liberty.jpg" alt="EXIF 数据的 Liberty JPG 图像">}}


* 使用 [Metadata][12] 类构造函数加载包含 EXIF 数据信息的图像源文件。
* 通过调用 [GetRootPackage()][13] 方法获取它的**根包**。
* 从根包中，从其 [ExifPackage 属性][15] 中获取其 [ExifPackage][14]。
* 获得 EXIF 包后，您现在可以访问图像的 EXIF 属性；如 **Make**、**Model**、**Width**、**Length**、**DateTime**、版权、软件等，如下面的 C# 代码示例所示。

```
// Extract EXIF Data Package Information from image in C#
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        Console.WriteLine(root.ExifPackage.Make);
        Console.WriteLine(root.ExifPackage.Model);
        Console.WriteLine(root.ExifPackage.ImageWidth);
        Console.WriteLine(root.ExifPackage.ImageLength);
        Console.WriteLine(root.ExifPackage.DateTime);
     }
}
```

上面的代码将显示提供的 JPG 图像的以下可用 EXIF 信息。

```
Make : NIKON CORPORATION
Model : NIKON D7200 
Width : 640
Length : 384
DateTime : 2018:07:06 19:31:05
```

### 读取图像的 EXIF IFD 和 GPS 信息

EXIF 数据还包括 Exif **IFD**（图像文件目录）和**GPS**（全球定位系统）信息。现在对于 IFD 和 GPS 包信息，您只需访问 **EXIF 包** 的相应属性，即 [ExifIfdPackage][16] 或 [GpsPackage][17]。从这些包中，您可以提取比下面提到的更多的信息：

* 设备序列号
* 相机所有者姓名
* CFA模式
* 速度
* 图像方向
* 日期戳
* 地区信息
* 海拔高度
* 纬度
* 经度
* ETC。

下面提到的代码可以添加到上述方法中，以显示 EXIF 数据以及 IFD 和 GPS 信息。

```
// Display EXIF IFD Package Properties like Serial Number and Camera Owner.
Console.WriteLine(root.ExifPackage.ExifIfdPackage.BodySerialNumber);
Console.WriteLine(root.ExifPackage.ExifIfdPackage.CameraOwnerName);
Console.WriteLine(root.ExifPackage.ExifIfdPackage.UserComment);
// Display EXIF GPS Information like Latitude, Longitude, etc.
Console.WriteLine(root.ExifPackage.GpsPackage.Altitude);
Console.WriteLine(root.ExifPackage.GpsPackage.LatitudeRef);
Console.WriteLine(root.ExifPackage.GpsPackage.LongitudeRef);
```

## 在 C# 中读取图像的所有 EXIF 标签 {#extract-all-exif-tags-from-images}

您可以提取任何图像的所有 EXIF 属性，您可以以与上述几乎相似的方式进行操作：

* 使用 [Metadata][18] 构造函数加载图像。
* 通过调用方法 [GetRootPackage()][19] 获取**根包**。
* 从根包的[ExifPackage 属性][20] 中获取**EXIF 包**。
* 迭代 EXIF 包并获得所需的名称-值对。
* 同样，获取 IFD 和 GPS 包以显示其键和值。

```
// Extract all EXIF Metadata from the image
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        const string pattern = "{0} = {1}";
        // Read all EXIF Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
        // Read all EXIF IFD Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.ExifIfdPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
         // Read all EXIF GPS Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.GpsPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
    }
}
```

## 在 C# 中更新 EXIF 属性 {#update-exif-properties}

您可以轻松更改任何图像的现有 EXIF 数据。以下是您可以遵循的步骤：

### **更新 EXIF 包**

* 通过调用方法[GetRootPackage()][21]获取**根包**。
* 通过将新值分配给相应的属性来设置 ExifPackage 属性，例如将新值分配给：
    * **root.ExifPackage.Copyright** - 设置更新的版权信息。
* 同样，您可以设置艺术家、品牌、型号、软件、图像宽度和高度、日期时间等的值。

### **更新 EXIF IFD 包**

与EXIF包的设置属性类似，我们可以更新EXIF IFD和GPS包的属性。

* 为 **root.ExifPackage.ExifIfdPackage.CameraOwnerName** 赋值以设置相机所有者。

您可以访问 [ExifIfdPackage][22] 或 [ExifGpsPackage][23] 类来了解您可以为图像自定义多少。

```
// Update or change new values in EXIF Data (EXIF Package & EXIF IFD Package).
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null)
    {
        // Set the EXIF package if it is missing
        if (root.ExifPackage == null) {
            root.ExifPackage = new ExifPackage();
        }
       // Setting the desired values in EXIF Package and EXIF IFD Package.
        root.ExifPackage.Copyright = "Copyright (C) 2011-2020 GroupDocs. All Rights Reserved.";
        root.ExifPackage.ImageDescription = "Statue of Liberty for EXIF Data";
        root.ExifPackage.Software = "GroupDocs.Metadata for .NET"; 
        root.ExifPackage.ExifIfdPackage.BodySerialNumber = "GD-2020";
        root.ExifPackage.ExifIfdPackage.CameraOwnerName = "GroupDocs";
        root.ExifPackage.ExifIfdPackage.UserComment = "Nice image captured in 2018";
        metadata.Save("statue-of-liberty-updated.jpg");
    }
}
```

## 从 C# 中的图像中删除 EXIF 元数据 {#remove-exif-metadata}

如果要从任何文件中删除 EXIF 包，只需将其 ExifPackage 属性设置为 **null**。

```
// Removing the EXIF data from an image.
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null)
    {
        root.ExifPackage = null;
        metadata.Save("statue-of-liberty-no-exif.jpg");
    }
}
```

## 支持的图像和其他格式 {#exif-supported-formats}

这些是 GroupDocs.Metadata 当前支持的文件格式，用于图像、音频和视频的 EXIF 数据信息。您可以随时访问 [文档][24] 以获取更新信息。

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td> **文件类型</td><td><strong>文件格式**</strong></td></tr><tr><td><a href="https://wiki.fileformat.com/image/">图片</a></td><td>BMP、GIF、JPG、JPEG、JPE、JP2、PNG、DJVU、DWG、DXF、WebP、TIFF、PSD、EMF、WMF</td></tr><tr><td><a href="https://wiki.fileformat.com/audio">音频</a>和<a href="https://wiki.fileformat.com/video/">视频</a></td><td>MP3、WAV、AVI、MOV/QT、FLV、ASF、DICOM</td></tr></tbody></table></figure>

## 查看有关 GroupDocs.Metadata 的更多信息

* 文档 ([.NET][25] | [Java][26]
* [源代码示例][27]
* [API 参考][28]
* GroupDocs.Metadata – [元数据管理解决方案][29]

**让我们多谈谈@** [免费支持论坛。][30]

## 相关文章

* [用Java管理图像的EXIF数据][31]







[1]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[2]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[3]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#extract-exif-data-from-images
[4]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#extract-all-exif-tags-from-images
[5]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#update-exif-properties
[6]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#remove-exif-metadata
[7]: https://products.groupdocs.com/metadata/net
[8]: https://docs.groupdocs.com/display/metadatanet/Features+Overview
[9]: https://downloads.groupdocs.com/metadata/net
[10]: https://www.nuget.org/packages/groupdocs.metadata
[11]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#exif-supported-formats
[12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage
[15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/iexif/properties/exifpackage
[16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage/properties/exififdpackage
[17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage/properties/gpspackage
[18]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[19]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[20]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/iexif/properties/exifpackage
[21]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[22]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exififdpackage
[23]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifgpspackage
[24]: https://docs.groupdocs.com/display/metadatanet/Supported+File+Formats
[25]: https://docs.groupdocs.com/display/metadatanet/Getting+Started
[26]: https://docs.groupdocs.com/display/metadatajava/Getting+Started)
[27]: https://github.com/groupdocs-metadata/
[28]: https://apireference.groupdocs.com/metadata
[29]: https://products.groupdocs.com/metadata
[30]: https://forum.groupdocs.com/c/metadata
[31]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


