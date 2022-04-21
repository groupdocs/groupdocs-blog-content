---
title: "Java中的水印PDF文件"
date: Sat, 26 Jun 2021 09:48:16 +0000
draft: false
url: /zh/2021/06/26/add-watermark-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "无论您是想将品牌应用于您的文档，还是想保护我们的文件免受任何非法使用，水印都可以为您完成工作。在本文中，您将学习使用 Java 以编程方式将水印添加到 PDF 文件中。"
tags: ['Image Watermark PDF in Java', 'Text Watermark PDF in Java', 'Watermark in Java', 'Watermark PDF in Java', 'Watermarking Java API']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-pdf-in-java.jpg" alt="在 Java 中将水印应用于 PDF">}}


无论您是想将品牌应用于您的文档，还是想保护文件免遭任何非法使用，水印都可以为您完成工作。在本文中，您将学习使用 Java 以编程方式将水印添加到 PDF 文件中。

以下主题涵盖以下内容：

* [Java 水印 API][1]
* [将文本水印应用到 PDF][2]
* [将图像水印应用于 PDF][3]

## Java的水印API {#java-watermarking-api}

[GroupDocs.Watermark for Java][4] 是一个水印 API，允许处理 PDF 文件中的文本和图像水印。除了 PDF 文件，API 还允许为文字处理文档、电子表格、演示文稿、电子邮件、图像、Visio 绘图和许多其他格式添加、删除和提取水印。从[文档][5]，您可以进一步检查功能和[支持的文件格式][6]。

### 下载并配置

从 [下载][7] 部分获取 PDF 水印库。对于基于 Maven 的 Java 应用程序，在 pom.xml 中添加以下配置。稍后，您可以尝试本文的示例以及 [GitHub][8] 中的更多示例。有关详细信息，您也可以访问 [API 参考][9]。

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
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## 使用 Java 将文本水印添加到 PDF {#text-watermark-to-pdf}

通过在所有页面或设置位置的任何选择性页面上添加格式化文本，可以将文本水印应用于 PDF 文件。

以下步骤显示如何将文本添加到 PDF 文件作为水印。

* 使用 [Watermarker][10] 类加载 PDF 文档。
* 使用 [TextWatermark][11] 类初始化文本水印。
* 通过改变旋转角度、xy 位置、不透明度、前景色和背景色等设置外观。
* 设置目标页面索引（可选）。如果不设置索引，水印会默认应用到所有页面。
* 添加文字水印到水印。
* 使用适当的 [save][12] 方法保存带水印的文件。

源代码展示了如何在 Java 中为 PDF 文件添加文本水印。

```
// 在Java中将文本水印应用于PDF文件的所有页面
PdfLoadOptions loadOptions = new PdfLoadOptions();
Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions);

// 在所有页面的中心添加文本
TextWatermark textWatermark = new TextWatermark("Watermark", new Font("Arial", 80));
textWatermark.setRotateAngle(-45);
textWatermark.setOpacity(0.3);
textWatermark.setForegroundColor(Color.getDarkBlue());
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);

// PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
// imageWatermarkOptions.setPageIndex(0);
watermarker.add(textWatermark);

// 保存带水印的 PDF
watermarker.save("path/text-watermark.pdf");
watermarker.close();
```

上述源代码的输出在给定 PDF 文件的两个页面上都显示了文本水印。



{{< figure align=center src="images/text-watermark-to-pdf-in-java-1024x585.png" alt="文字水印转PDF">}}


## 使用 Java 将图像水印添加到 PDF {#image-watermark-to-pdf}

同样，您可以将图像添加到任何位置的任何 PDF 文件，就像文本水印选项一样。

以下步骤显示如何将图像添加到 PDF 文件作为水印。

* 使用 [Watermarker][13] 类加载 PDF 文档。
* 使用 [ImageWatermark][14] 类初始化图像水印。
* 通过调整旋转角度、xy 位置、不透明度和其他选项来设置外观。
* 设置目标页面索引。 （选修的）
* 将图像水印添加到水印。
* 使用适当的 [save][15] 方法保存带水印的文件。

源代码展示了如何使用 Java 为 PDF 文件添加图像水印。

```
// 在Java中将图像水印应用于PDF文件的第二页
PdfLoadOptions loadOptions = new PdfLoadOptions();
Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions);

// 加载图像并设置外观
ImageWatermark imageWatermark = new ImageWatermark(Constants.LockPng);
imageWatermark.setOpacity(0.7);
imageWatermark.setX(130);
imageWatermark.setY(390);

// 将图像添加到 PDF 文件的第二页
PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
imageWatermarkOptions.setPageIndex(1);
watermarker.add(imageWatermark, imageWatermarkOptions);
imageWatermark.close();

// 保存带水印的 PDF
watermarker.save("path/image-watermark.pdf");
watermarker.close();
```

上述源代码的输出显示了给定 PDF 文件第二页上的图像水印。



{{< figure align=center src="images/image-watermark-to-pdf-in-java-1024x585.png" alt="图片水印转PDF">}}


## 获取免费 API 许可证

您可以[获得免费的临时许可证][16] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，您学会了使用 Java 将水印应用于 PDF 文件。我们讨论了在 PDF 文件上添加文本和图像作为水印。有关 API 的更多详细信息或了解，请访问 [文档][17]。如有疑问，请通过 [论坛][18] 联系我们。

## 也可以看看

* [在Java中为图像添加水印][19]
* [Java 水印 Excel 表格][20]
* [在Java演示文稿中添加水印][21]







[1]: #java-watermarking-api
[2]: #text-watermark-to-pdf
[3]: #image-watermark-to-pdf
[4]: https://products.groupdocs.com/watermark/java
[5]: https://docs.groupdocs.com/watermark/java/
[6]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/comparison/java
[8]: https://github.com/groupdocs-comparison
[9]: https://apireference.groupdocs.com/comparison/java
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/watermark/
[18]: https://forum.groupdocs.com/
[19]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[20]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[21]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/


