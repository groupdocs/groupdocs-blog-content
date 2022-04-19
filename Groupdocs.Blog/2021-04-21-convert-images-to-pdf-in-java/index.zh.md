---
title: "在 Java 中将图像转换为 PDF"
date: Wed, 21 Apr 2021 10:57:00 +0000
draft: false
url: /zh/2021/04/21/convert-images-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "As PDF is the most common portable document format used to exchange files, there arises the requirement to convert documents as well as images to PDF format without losing the quality. In this article, we will learn to programmatically convert images to PDF format in Java."
tags: ['Convert Image to PDF in Java', 'Image Conversion Java API', 'Image to PDF in Java', 'JPG to PDF in Java', 'PNG to PDF in Java', 'WebP to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

由于 PDF 是用于交换文件的最常见的便携式文档格式，因此需要在不损失质量的情况下将文档和图像转换为 PDF 格式。在本文中，我们将学习使用 Java 以编程方式将 JPG、PNG、GIF 和其他图像转换为 PDF 格式。



{{< figure align=center src="images/convert-images-to-pdf-in-java.jpg" alt="使用 Java 将图像转换为 PDF">}}


以下是以下简要讨论的主题：

* [图像转换 Java API][2]
* [将JPG图像转换为PDF][3]
* [将PNG、GIF、BMP图像转换为PDF][4]
* [使用选项将图像转换为 PDF][5]

## 图像转换 Java API {#java-image-conversion-api}

为了在您的 Java 应用程序中转换图像和文档，GroupDocs 提供了原生的、专门的 [GroupDocs.Conversion for Java][6] API。它甚至可以在受密码保护的文件上转换整个文档、特定页面、应用旋转、水印。 API 有一长串文档和图像[支持的文件格式][7]，可以来回转换。

### 下载并配置

[获取转换库][8] 从下载或在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置。之后，您可以尝试本文的示例以及 [GitHub][9] 上的更多可用示例。有关详细信息，您可以访问 [API 参考][10]。

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
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.4</version> 
</dependency>
```

## 在 Java 中将 JPG 转换为 PDF {#jpg-to-pdf}



{{< figure align=center src="images/mount-everest.jpg" alt="山 JPG 图片">}}


要将图像转换为 PDF 格式，有一种简单的方法。让我们从 JPG 图像开始，按照步骤将 JPG 图像转换为 PDF 文档。

* 使用 [Converter][11] 类加载 JPG 图像。
* 使用 [convert][12] 方法将提供的图像转换为 PDF。
* 从保存位置获取转换后的 PDF 图像。

以下代码示例展示了如何使用 Java 仅用 2 行代码将 JPG 图像转换为 PDF。

```
// 在 Java 中将 JPG 图像转换为 PDF。
Converter converter = new Converter("path/image.jpg");
converter.convert("output/convertedJpg.pdf", new PdfConvertOptions());
```

## 在 Java 中将 PNG、GIF、BMP 图像转换为 PDF {#png-gif-bmp-to-pdf}

API 不仅限于 JPG 图像。它支持多种图像格式，以同样的方式将其转换为 PDF。无论是PNG转PDF、GIF转PDF、BMP转PDF，还是其他任何转换，都可以同样进行。

以下是将任何图像转换为 PDF 文档的步骤。

* 使用 [Converter][13] 类加载任何图像。
* 使用 [convert][14] 方法将提供的图像转换为 PDF。

以下代码示例显示了如何以相同的方式将 PNG 图像转换为 PDF。

```
// 在 Java 中将图像转换为 PDF。 PNG、WebP、GIF、BMP、TGA 等等...
Converter converter = new Converter("path/image.png");
converter.convert("output/convertedImage.pdf", new PdfConvertOptions());
```

## 带有选项的 Java 中的图像到 PDF 转换 {#image-to-pdf-advanced}

以下是将图像转换为 PDF 文档的步骤，并根据需要进行一些自定义。在将图像转换为 PDF 格式时，您可以调整 **margins**、**height**、**width**、**DPI**、应用 **watermark** 和一些其他选项。



{{< figure align=center src="images/image-to-pdf-with-watermark-and-margin.png" alt="将JPG转换为PDF">}}


* 使用 [Converter][15] 类加载图像。
* 使用 [PdfConvertOptions][16] 初始化 PDF 转换选项。
* 使用各自的方法设置边距、高度、宽度。
* 使用 [WatermarkOptions][17] 应用水印。
* 使用 [convert][18] 方法将提供的图像转换为带有设置选项的 PDF。

以下代码示例显示了如何使用 Java 将 JPG 图像转换为 PDF 文档，其中包含以下选项：设置 **margins**、特定 **size**、应用 **watermark** 与 **rotation** 和 **transparency**。

```
// 在 Java 中将 JPG、PNG 或其他图像转换为 PDF。应用水印、调整大小、设置 DPI 和设置边距。
Converter converter = new Converter("path/image.jpg", new ImageLoadOptions());
// 设置 PDF 转换选项
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(200);
// 设置边距
options.setMarginBottom(10);
options.setMarginLeft(10);
options.setMarginRight(10);
options.setMarginTop(10);
//options.setRotate(Rotation.On90); // 回转
options.setWidth(640);
options.setHeight(426);
// 将水印应用于 PDF 中的图像 
WatermarkOptions watermarkOptions = new WatermarkOptions();
watermarkOptions.setText("Watermark");
watermarkOptions.setColor(Color.WHITE);
watermarkOptions.setRotationAngle(-45);
watermarkOptions.setTransparency(0.1);
watermarkOptions.setLeft(10);
watermarkOptions.setTop(75);
options.setWatermark(watermarkOptions);
// 保存转换后的 PDF 文件
converter.convert("output/convertedJpgToPdfAdv.pdf", options);
```

## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以[获得免费的临时许可证][19] 使用 API 而不受评估限制。

## 结论

在本文中，您学习了如何将图像转换为 PDF 格式。具体来说，我们讨论了使用 Java 将 JPG、PNG、BMP 图像转换为 PDF。此外，您还了解了如何在转换图像 PDF 时设置边距、大小、应用水印。

要探索有关 Java Conversion API 的更多信息，您可以查阅 [文档][20]。如有任何疑问，请通过 [论坛][21] 联系我们。

## 也可以看看

* [使用 C# 将图像转换为 PDF][22]
* [在 Java 中将电子表格（XLS、XLSX）转换为 PDF][23]







[1]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[2]: #java-image-conversion-api
[3]: #jpg-to-pdf
[4]: #png-gif-bmp-to-pdf
[5]: #image-to-pdf-advanced
[6]: https://products.groupdocs.com/conversion/java
[7]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[8]: https://downloads.groupdocs.com/conversion/java
[9]: https://github.com/groupdocs-conversion
[10]: https://apireference.groupdocs.com/conversion/java
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[15]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[19]: https://purchase.groupdocs.com/temporary-license
[20]: https://docs.groupdocs.com/conversion/
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[23]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/


