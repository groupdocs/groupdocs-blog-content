---
title: "'将演示文稿转换为 Java 中的图像'"
date: Tue, 18 Jan 2022 09:02:01 +0000
draft: false
url: /zh/2022/01/18/convert-presentations-to-images-in-java/
author: 'Shoaib Khan'
summary: '欢迎开发者！您希望在这里以编程方式将您的一些演示幻灯片转换为图像格式。当我们想要将特定幻灯片共享为图像或者您想要从演示文稿中创建缩略图时，可能需要这样做。在本文中，您将学习**如何在 Java 中将 PPT 或 PPTX 演示幻灯片转换为 JPG 和 PNG 图像**。

本文讨论了以下主题：

* 用于表示转换的 Java API
* 将 PPT/PPTX 转换为 JPG 图片
* 将 PPT/PPTX 转换为 PNG 图像'
tags: ['Convert PPT', 'Convert PPT to JPG in Java', 'Convert PPT to PNG in Java', 'Convert PPTX', 'PPT to JPG in Java', 'PPT to PNG in Java']
categories: ['GroupDocs.Conversion Product Family']
---

欢迎开发者！您希望在这里以编程方式将您的一些演示幻灯片转换为图像格式。当我们想要将特定幻灯片共享为图像或者您想要从演示文稿中创建缩略图时，可能需要这样做。在本文中，您将学习**如何在 Java 中将 PPT 或 PPTX 演示幻灯片转换为 JPG 和 PNG 图像**。



{{< figure align=center src="images/convert-ppt-to-jpg-png-image-in-java.jpg" alt="在 Java 中将 PPT 转换为 JPG 或 PNG 图像">}}


此处讨论了以下主题：

* [用于表示转换的Java API](#ppt-convert-java-api)
* [PPT/PPTX转JPG图片](#ppt-to-jpg)
* [PPT/PPTX转PNG图片](#ppt-to-png)
* [转换为带效果的图像](#convert-to-image-with-effects)

## 用于转换演示文稿的 Java API {#ppt-convert-java-api}

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/) 提供了允许将演示文稿转换为图像的 Java API。今天，我们将使用它的 [GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/net/) 将 PPT 和 PPTX 格式的演示文稿转换为 JPG 和 PNG 图像。 API 进一步支持 [文档](https://docs.groupdocs.com/conversion/java/supported-document-formats) 中提到的许多其他转换文字处理文档、电子表格、演示文稿、电子书、图像等/)。

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
        <version>21.10.1</version> 
</dependency>
```

## 在 Java 中将演示文稿转换为 JPG 图像 {#ppt-to-jpg}

让我们通过将演示文稿转换为 JPG 图像格式来实现目标。以下步骤指导如何将 Powerpoint PPT/PPTX 转换为 Java 中的 JPG 图像格式。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) 类加载演示文稿。
* 准备 [图片转换选项](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions)。
* 定义转换文件格式为**JPG**。
* 提供要转换的幻灯片编号。
* 使用 **convert()** 方法将演示幻灯片转换为 JPG 图像。

以下 Java 源代码将 PowerPoint 演示文稿转换为 JPG 格式。

```
// 将 PPT、PPTX 演示文稿转换为 Java 中的 JPG 图像
Converter converter = new Converter("path/presentation.pptx");            

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
options.setPageNumber(1);

converter.convert("path/ppt-to-image.jpg", options);
```

## 在 Java 中将演示文稿转换为 PNG 图像 {#ppt-to-png}

同样，您可以转换为其他流行的图像格式，例如 PNG。让我们将演示文稿的任何幻灯片转换为 PNG。以下步骤展示了如何在 Java 中将 PPT/PPTX 演示幻灯片转换为 PNG 图像格式。

* 使用 [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter) 类加载演示文件。
* 准备 [图片转换选项](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions)。
* 将转换文件格式设置为**PNG**。
* 定义要转换的选定幻灯片编号。
* 使用 **convert()** 方法将幻灯片转换为 PNG 图像。

以下 Java 源代码示例将 PowerPoint 演示文稿转换为 PNG 格式。

```
// 在 Java 中将 PPT、PPTX 演示文稿转换为 PNG 图像
Converter converter = new Converter("path/presentation.pptx");

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Png);
options.setPagesCount(1);

converter.convert("path/ppt-to-image.png", options);
```

## 转换为带效果的图像 {#convert-to-image-with-effects}

在转换幻灯片时，您可以对输出图像文件应用许多变体。您可以从以下任何文章中了解更多信息：

* [使用 Java 中的高级选项转换为图像](https://blog.groupdocs.com/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/)
* [高级图像转换的 API 文档](https://docs.groupdocs.com/conversion/java/convert-to-image-with-advanced-options/)

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

最后，我们了解了如何在 Java 中将演示幻灯片转换为 JPG 和 PNG 图像。要构建您的转换应用程序，您可以从 [文档](https://docs.groupdocs.com/conversion/java/) 和 [GitHub](https://github.com/groupdocs) 上的运行示例中了解更多信息-转换) 。如有任何疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [在 Java 中将演示文稿转换为 PDF](https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/)
* [在 Java 中将图像转换为 PDF](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)
* [Java 中 Excel 电子表格到 PDF 的转换](https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/)





