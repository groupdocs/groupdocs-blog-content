---
title: "'在 Java 中将 PDF 转换为灰度'"
date: Wed, 02 Mar 2022 15:53:00 +0000
draft: false
url: /zh/2022/03/02/convert-pdf-to-grayscale-jpg-png-images-in-java/
author: 'Shoaib Khan'
summary: "几乎任何文档或图像格式（包括图像) 都可以转换为黑白或灰度单色图像。在本文中，我们将讨论如何在 Java 中将彩色 PDF 文档转换为**灰度 JPG 和 PNG 图像格式**。"
tags: ['convert document to image', 'convert to grayscale', 'Convert to Grayscale in Java', 'PDF to Grayscale', 'PDF to Grayscale in Java', 'PDF to JPG Grayscale', 'PDF to PNG Grayscale']
categories: ['GroupDocs.Conversion Product Family']
---

几乎任何文档或图像格式（包括图像) 都可以转换为黑白或灰度图像。在本文中，我们将讨论如何将彩色 PDF 文档转换为 Java 中的**灰度 JPG 和 PNG 图像格式**。



{{< figure align=center src="images/Converted-Colored-PDF-to-Grayscale-1024x577.jpg" alt="将 PDF 转换为灰度">}}


## 将文档转换为灰度的 Java API

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/net/) 提供 Java API，用于在多种[支持的文件格式和图像类型](https://docs.groupdocs.com/conversion/net/supported-document-formats/)之间转换文档。 可以使用多个高级选项自定义转换结果。 我将使用这个 [GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java/) API 将 PDF 文档转换为灰度 JPG 和 PNG 图像。

### 下载或配置

您可以从 [下载部分](https://downloads.groupdocs.com/conversion) 下载 **JAR** 文件，或者只获取基于 **maven 的 pox.xml 的存储库和依赖项配置** Java 应用程序。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>22.3</version> 
</dependency>
```

## 在 Java 中将 PDF 转换为灰度 JPG 图像

从转换彩色 PDF 文档并将其转换为图像格式开始。以下步骤展示了如何在 Java 中将 PDF 转换为灰度 JPG。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) 类加载 PDF 文档。
* 准备[图片转换选项](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions)。
* 设置转换文件格式为**JPG**。
* 将灰度选项设置为 true。
* 使用带有选项的适当 **convert()** 方法转换为图像。

以下 Java 源代码将 PDF 文档转换为灰度 JPG 图像。

```
// 在 Java 中将 PDF 转换为灰度 PNG
Converter converter = new Converter("path/document.pdf");

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
options.setGrayscale(true);
/*
options.setFlipMode(ImageFlipModes.FlipY);
options.setBrightness(50);
options.setContrast(50);
options.setGamma(0.5F);
*/
converter.convert("path/grayscaleDocument.jpg", options);
```

此外，还有许多其他选项可以自定义高度、宽度、水平和垂直翻转、文档旋转以及亮度、伽玛和对比度等属性。此外，您可以将具有不同设置的水印应用于输出图像。

## 在Java中将PDF转换为灰度PNG图像

同样，彩色 PDF 文档也可以转换为其他灰度图像格式。以下步骤展示了如何在 Java 中将 PDF 文件转换为灰度 PNG。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) 类加载 PDF 文档。
* 使用 [ImageConvertOptions](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions) 准备转换选项。
* 将转换文件格式设置为**PNG**。
* 将灰度选项设置为 true。
* 使用 **convert()** 方法转换为 PNG 图像。

以下 Java 源代码将 PDF 文档转换为灰度 PNG 图像。

```
// 在 Java 中将 PDF 转换为灰度 PNG
Converter converter = new Converter("path/document.pdf");

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Png);
options.setGrayscale(true);

converter.convert("path/grayscaleDocument.png", options);
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

综上所述，我们学习了如何在 Java 中将 PDF 文档转换为 PNG 或 JPG 图像格式。尝试构建自己的转换应用程序，您可以从 [文档](https://docs.groupdocs.com/conversion/net/) 中了解更多关于低代码和高代码 Java API 的信息，以实现文档转换的自动化。

最简单的方法是体验 [GitHub](https://github.com/groupdocs-conversion) 中的示例。如有任何疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [使用 C# 将 PDF 转换为灰度](https://blog.groupdocs.com/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/)
* [将演示文稿转换为 Java 中的图像](https://blog.groupdocs.com/2022/01/18/convert-presentations-to-images-in-java/)
* [在 Java 中将图像转换为 PDF](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)





