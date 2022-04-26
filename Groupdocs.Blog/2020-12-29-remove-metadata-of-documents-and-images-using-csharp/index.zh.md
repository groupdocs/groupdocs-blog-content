---
title: "使用 C# 的文档和图像的元数据删除器"
date: Tue, 29 Dec 2020 14:14:00 +0000
draft: false
url: /zh/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/
author: 'Shoaib Khan'
summary: "今天，我们将学习一些方法来**以编程方式删除或完全清除文档的元数据以及使用 C#** 的图像。在 [较早的帖子][1] 中，我们讨论了使用 Java 从文档和图像中删除选择性以及所有可用的元数据属性。有时向接收者隐藏个人信息很重要，这些信息附在文件中。以下主题将帮助您使用 C# 从元数据中清除文件。"
tags: ['metadata cleaner using csharp', 'remove metadata from documents in csharp', 'remove metadata from images in csharp', 'remove metadata using csharp']
categories: ['GroupDocs.Metadata Product Family']
---

今天，我们将学习一些方法来**以编程方式删除或完全清除文档的元数据以及使用 C#** 的图像。在 [较早的帖子][2] 中，我们讨论了使用 Java 从文档和图像中删除选择性以及所有可用的元数据属性。有时向接收者隐藏个人信息很重要，这些信息附在文件中。以下主题将帮助您使用 C# 从元数据中清除文件。

* [.NET 元数据清理 API][3]
* [使用 C# 从文档中删除元数据][4]
* [使用 C# 清除图像中的元数据][5]
* [使用 C# 从文档和图像中删除选择性元数据][6]

## .NET 元数据删除 API {#dotnet-metadata-removal-api}

为了实现计划，我将使用 [GroupDocs.Metadata for .NET][7] API，它允许 .NET 开发人员从许多 [支持的格式][8] 文档中添加、修改、提取、删除或完全元数据，图像和其他文件。 API 支持 EXIF、XMP、IPTC、ID3 标签等元数据标准。您可以[下载][9] DLL 或 MSI 安装程序，或通过 [NuGet][10] 安装它。

```
Install-Package GroupDocs.Metadata
```

## 使用 C# 从文档中删除元数据 {#remove-documents-metadata-using-csharp}

为了在不应用任何特定过滤器的情况下删除所有元数据属性，请使用 **Sanitize** 方法。以下是使用 GroupDocs.Metadata for .NET 从 DOCX、PDF、XLSX 等文档中清除元数据的步骤。

* 首先创建 [Metadata][11] 类对象，并将目标文档的路径作为参数传递。
* 使用 [Sanitize][12] 方法清除所有可用的元数据。它返回已删除的元数据属性的数量。
* 调用 [Save][13] 方法保存已删除元数据的输出文件。

以下 C# 代码示例展示了如何从 PDF 文档中删除和清除元数据。

```
/*
* 从 Word、Excel 中清除所有检测到的元数据属性， 
* PowerPoint、PDF 和其他使用 C# 的文档
*/
using (Metadata metadata = new Metadata("filePath/document.pdf"))
{
	var affected = metadata.Sanitize();
	metadata.Save("filePath/output.pdf");
}
```

## 使用 C# 从图像中删除元数据 {#remove-images-metadata-using-csharp}

无论您是想从文档中还是从图像文件中删除元数据，过程都将保持不变。只有源文档会相应更改。

* 创建 [Metadata][14] 类的对象，并将文档路径作为参数传递。
* 调用 [Sanitize][15] 方法删除任何可用的元数据属性。
* 使用[Save][16]方法保存输出文件。

以下 C# 代码示例展示了如何从 JPG 图像中删除元数据。

```
/*
* 从 PNG、JPG/JPEG 中清除或删除所有检测到的元数据属性，
* WebP、BMP、GIF、TIFF等图片使用C#
*/
using (Metadata metadata = new Metadata("filePath/document.jpg"))
{
	var affected = metadata.Sanitize();
	metadata.Save("filePath/output.jpg");
}
```

## 使用 C# 从文档和图像中删除选择性元数据 {#remove-selective-metadata-using-csharp}

如果不需要从文件中删除所有可用的元数据，我们只想删除选择性元数据属性。以下步骤允许您使用属性的特定名称来定位和删除目标元数据属性。

* 创建一个 [Metadata][17] 类的对象来加载源文档或图像文件。
* 创建个性化规范以查找元数据属性。
* 使用创建的个性化规范调用 [RemoveProperties][18] 方法。
* 使用[Save][19]方法保存输出文件。

```
// 使用 C# 从满足自定义过滤器的文档和图像中删除元数据属性
using (Metadata metadata = new Metadata("filePath/document.docx"))
{
	// Remove all the properties that:
	// contains the name of the document author OR
	// it refers to the last editor OR 
	// the property value is a string AND equal to the given string "GroupDocs"
	var affected = metadata.RemoveProperties(
		p => p.Tags.Contains(Tags.Person.Creator) ||
			 p.Tags.Contains(Tags.Person.Editor) ||
			 p.Value.Type == MetadataPropertyType.String && p.Value.ToString().Contains("GroupDocs"));
	Console.WriteLine("Properties removed: {0}", affected);

	metadata.Save("outputPath/document.docx");
}
```

## 结论

我们学习了使用 C# 从文档和图像中删除元数据的方法。阅读完本文后，您会觉得使用 .NET 构建自己的元数据清理器应用程序会很自在。它可以支持从 MS Word 文档格式、电子表格、演示文稿、PDF 文件、图像、电子邮件、电子书、绘图、zip 文件等 [API 支持的文件格式][20] 中删除元数据。

您可以从 [documentation][22] 进一步探索 [.NET Metadata Manipulation API][21]。

## 也可以看看

* [在Java中删除文档和图像的元数据][23]
* [用C#管理图片的EXIF数据][24]
* [使用Java管理图像的EXIF数据][25]







[1]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[2]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[3]: #dotnet-metadata-removal-api
[4]: #remove-documents-metadata-using-csharp
[5]: #remove-images-metadata-using-csharp
[6]: #remove-selective-metadata-using-csharp
[7]: https://products.groupdocs.com/metadata/net
[8]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[9]: https://downloads.groupdocs.com/metadata/net
[10]: https://www.nuget.org/packages/groupdocs.metadata
[11]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/sanitize
[13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/sanitize
[16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[18]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/removeproperties
[19]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[20]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[21]: https://products.groupdocs.com/metadata/net
[22]: https://docs.groupdocs.com/metadata/net/
[23]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[24]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
[25]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


