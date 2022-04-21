---
title: "使用 C# 管理 HEIF/HEIC 图像的 XMP 和 EXIF 数据"
date: Sat, 17 Jul 2021 17:58:00 +0000
draft: false
url: /zh/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/
author: 'Shoaib Khan'
summary: "**HEIC** (High-Efficiency Image Container) 是一个可以包含 High-Efficiency Image Format **HEIF** 图像的容器。 **XMP** 是一种基于 XML 的元数据标准，可以将元数据属性存储为名称/值对。但是，**EXIF**（可交换图像文件格式）是标准，它定义了如何以最常见的图像和音频格式存储元数据属性。在本文中，我们将学习**如何在 .NET 应用程序中使用 C# 提取、更新和删除 HEIF/HEIC 图像的 XMP 和 EXIP 元数据**。"
tags: ['exif data', 'exif data in CSharp', 'EXIF data of HEIC in CSharp', 'XMP data in CSharp', 'XMP data of HEIC in CSharp', 'XMP metadata']
categories: ['GroupDocs.Metadata Product Family']
---

**HEIC** (High-Efficiency Image Container) 是一个可以包含 High-Efficiency Image Format **HEIF** 图像的容器。 **XMP** 是一种基于 XML 的元数据标准，可以将元数据属性存储为名称/值对。但是，**EXIF**（可交换图像文件格式）是标准，它定义了如何以最常见的图像和音频格式存储元数据属性。在本文中，我们将学习**如何在 .NET 应用程序中使用 C# 提取、更新和删除 HEIF/HEIC 图像的 XMP 和 EXIP 元数据**。

以下主题涵盖以下内容：

* [用于 EXIF、XMP 元数据的 .NET API][1]
* [读取 HEIC/HEIF 图像的 EXIF 数据][2]
* [读取 HEIC/HEIF 图像的 XMP 数据][3]

## 用于 XMP 和 EXIF 元数据的 .NET API {#dotnet-api-for-exif-and-xmp-metadata}

[GroupDocs.Metadata][4] 提供 .NET API 来自动化 .NET 应用程序中的元数据管理。 API 允许读取、更新、添加、清理/删除和遍历许多文件格式的元数据。 API 支持各种元数据标准，如 EXIF、IPTC 和 XMP。您还可以访问文档以获取 [支持的元数据操作文件格式][5] 的完整列表。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Metadata
```

## 在 C# 中读取 HEIC / HEIF 图像的 EXIF 数据 {#read-exif-of-heic-heif-images}

以下是读取和提取 HEIC 和 HEIF 图像的 EXIF 数据的步骤。

* 使用元数据类加载 HEIF 或 HEIC 图像。
* 获取根包。
* 从根包中检索 EXIF 包。
* 遍历 EXIF 数据属性。
* 此外，您可以从 EXIF 包中获取 IFD（图像文件目录）和 GPS 信息。

以下代码展示了如何使用 C# 获取 HEIC 图像的 EXIF 数据、IFD 和 GPS 元数据信息。

```
// 在 C# 中读取 HEIF / HEIC 图像的 EXIF、EXIF IFD、EXIF GPS 包
using (Metadata metadata = new Metadata(@"image.heic"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        const string pattern = "{0} = {1}";

        foreach (TiffTag tag in root.ExifPackage.ToList())
        {
            Console.WriteLine(pattern, tag.TagID, tag.Value);
        }

        foreach (TiffTag tag in root.ExifPackage.ExifIfdPackage.ToList())
        {
            Console.WriteLine(pattern, tag.TagID, tag.Value);
        }

        foreach (TiffTag tag in root.ExifPackage.GpsPackage.ToList())
        {
            Console.WriteLine(pattern, tag.TagID, tag.Value);
        }
    }
}
```

## 在 C# 中读取 HEIC / HEIF 图像的 XMP 数据 {#read-xmp-of-heic-heif-images}

以下步骤读取 HEIC 或 HEIF 图像的 XMP 元数据。

* 使用元数据类加载 HEIF 或 HEIC 图像。
* 使用 getRootPackage 方法获取根包。
* 从根包中，可以得到 XMP 的基本信息。
* 此外，您可以获得 DCMI 都柏林核心信息。
* 此外，您可以使用 getPhotoshop 方法获取 Photoshop 信息。

以下源代码显示了如何在 C# 中获取 XMP 基本、DCMI 和 Photoshop 信息。

```
// 在 C# 中提取 HEIC 和 HEIF 图像的 XMP Basic、DublinCore 和 Photoshop 数据
using (Metadata metadata = new Metadata(@"xmp.heic"))
{
    IXmp root = metadata.GetRootPackage() as IXmp;
    if (root != null && root.XmpPackage != null)
    {
        if (root.XmpPackage.Schemes.XmpBasic != null)
        {
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.CreatorTool);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.CreateDate);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.ModifyDate);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.Label);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.Nickname);
            // ...
        }
        if (root.XmpPackage.Schemes.DublinCore != null)
        {
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Format);
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Coverage);
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Identifier);
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Source);
            // ...
        }
        if (root.XmpPackage.Schemes.Photoshop != null)
        {
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.ColorMode);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.IccProfile);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.Country);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.City);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.DateCreated);
            // ... 
        }
        // ...
    }
}
```

同样，有许多 setter 方法可以设置或更新不同的 XMP 属性。您甚至可以[提供您自己的键值对来设置自定义 XMP 包属性][8]。

## 在 C# 中删除 HEIC/HEIF 图像的 EXIF 和 XMP 元数据

您只需将相应的 EXIF 包或 XMP 包设置为 null 即可删除所有元数据属性。

以下代码在 C# 中删除 HEIC 图像的 EXIF 数据。

```
using (Metadata metadata = new Metadata("image.heic"))
{
	IExif root = metadata.GetRootPackage() as IExif;
	if (root != null)
	{
		root.ExifPackage = null;
		metadata.Save("no-exif-image.heic");
	}
}
```

以下代码在 C# 中删除 HEIC 图像的 XMP 数据。

```
using (Metadata metadata = new Metadata("image.heic"))
{
	IXmp root = metadata.GetRootPackage() as IXmp;
	if (root != null)
	{
		root.XmpPackage = null;
		metadata.Save("no-xmp-image.heic");
	}
}
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][9] 以便在没有评估限制的情况下使用 API。

## 结论

综上所述，我们已经学会了在 C# 中从 HEIF/HEIC 图像中提取、更新、删除 EXIF 和 XMP 元数据。此外，您还了解了如何从这些图像中获取 IFD 和 GPS 信息。现在您可以轻松获取这些信息并开始构建您自己的应用程序，例如 [GroupDocs.Metadata App Product Family][10] 以自动化元数据信息。

有关更多信息、选项和示例，您可以访问 [文档][11] 和 [GitHub][12] 存储库。如需进一步查询，请通过支持 [论坛][13] 联系我们。

## 也可以看看

* [在 C# 中提取 WAV 文件的 RIFF INFO 和元数据][14]
* [使用 C# 从文档和图像文件中删除元数据][15]







[1]: #dotnet-api-for-exif-and-xmp-metadata
[2]: #read-exif-of-heic-heif-images
[3]: #read-xmp-of-heic-heif-images
[4]: https://products.groupdocs.com/metadata
[5]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/metadata
[7]: https://www.nuget.org/packages/groupdocs.metadata
[8]: https://docs.groupdocs.com/metadata/net/working-with-xmp-metadata/
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://products.groupdocs.app/metadata/family
[11]: https://docs.groupdocs.com/metadata/
[12]: https://github.com/groupdocs-metadata
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
[15]: https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/


