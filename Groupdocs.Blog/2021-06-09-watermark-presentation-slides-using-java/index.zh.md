---
title: "使用 Java 的水印演示幻灯片"
date: Wed, 09 Jun 2021 17:36:49 +0000
draft: false
url: /zh/2021/06/09/watermark-presentation-slides-using-java/
author: 'Shoaib Khan'
summary: "为了保护文件和演示文稿不被非法使用，我们可以使用水印。在本文中，我们将学习以编程方式将基于文本和图像的水印应用于演示文稿或 Java 演示文稿的特定幻灯片。在另一篇文章中，我们讨论了[使用 C# 将水印应用于演示文稿][1]。"
tags: ['Add Watermark to Presentation in Java', 'Image Watermark to PPT in Java', 'Text Watermark to PPT in Java', 'Watermark PPT in Java', 'Watermark PPTX in Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-presentations-in-java.jpg" alt="在 Java 中将水印应用于演示文稿">}}


为了保护文件和演示文稿不被非法使用，我们可以使用水印。在本文中，我们将学习以编程方式将基于文本和图像的水印应用于演示文稿或 Java 演示文稿的特定幻灯片。在另一篇文章中，我们讨论了[使用 C# 将水印应用于演示文稿][2]。

下面将介绍以下主题：

* [Java 水印 API][3]
* [为演示幻灯片添加文字水印][4]
* [为演示幻灯片添加图像水印][5]

## 用于演示的 Java 水印 API {#java-watermarking-api}

[GroupDocs.Watermark][6] 提供用于水印的 Java API，它允许将文本和图像水印添加到应用程序中的演示文稿中。

除了演示之外，API 还支持从文字处理文档、电子表格、电子邮件、PDF 文件、图像和许多其他格式中添加、删除和提取水印。

在演示文件格式中，它支持[PPT][7]、[PPTX][8]、[PPS][9]、[PPTM][10]、[PPSX][11]等。从[文档][12]，您可以进一步检查功能和[支持的文件格式][13]。

### 下载并配置

您可以从 [下载部分][14] 获取水印库。对于基于 Maven 的 Java 应用程序，只需添加以下 pom.xml 配置。之后，您可以尝试本文的水印示例以及 [GitHub][15] 中的更多示例。有关详细信息，您可以访问 [API 参考][16]。

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

## 在 Java 中向演示文稿幻灯片添加文本水印 {#text-watermark-to-slides}

使用 API，您可以在将文本作为水印添加到演示文稿幻灯片时应用自定义。以下步骤显示了如何将水印应用于 Java 应用程序中的演示文稿。

* 使用 [Watermarker][17] 加载演示文稿。
* 使用 [TextWatermark][18] 设置水印文本和样式。
* 设置水印属性，如大小、位置、不透明度、旋转和颜色。
* 提供要应用水印的幻灯片索引。 _（选修的）_
* 使用[add][19]方法添加格式化文本水印。
* 通过调用 [save][20] 方法保存带水印的演示文稿。

以下代码示例显示了如何使用 Java 在所有带有旋转的幻灯片上添加 PPT 或 PPTX 中的文本水印。

```
/*
* 示例：如何在 Java 中向演示幻灯片添加文本水印
*/
Watermarker watermarker = new Watermarker("path/presentation.pptx");

// 准备文本及其大小、位置和外观
TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 36));
watermark.setRotateAngle(-45);
watermark.setX(100);
watermark.setY(100);
watermark.setHeight(400);
watermark.setWidth(400);
watermark.setOpacity(0.3);
watermark.setForegroundColor(Color.getDarkBlue());
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);

// PresentationWatermarkSlideOptions imageWatermarkOptions = new PresentationWatermarkSlideOptions();
// imageWatermarkOptions.setSlideIndex(0);

// 向演示文稿添加文本水印
watermarker.add(watermark);
watermarker.save("path/text-watermarked-presentation.pptx");

watermarker.close();
```

如果没有设置幻灯片索引，默认情况下，水印将应用于演示文稿的所有幻灯片。上面的代码还展示了如何提及幻灯片索引。以下是 PPTX 演示文稿的所有幻灯片上带有文本水印的输出。



{{< figure align=center src="images/text-watermark-to-slide-in-Java.png" alt="演示幻灯片的文本水印">}}


## 使用 Java 将图像水印添加到 PPT 幻灯片 {#image-watermark-to-slides}

您也可以使用类似的方法在演示文件上添加图像水印。只需使用 [ImageWatermark][21] 类而不是 TextWatermark。

以下步骤指导如何将图像水印添加到 Java 应用程序中的演示幻灯片。

* 使用 [Watermarker][22] 加载演示文件。
* 使用 [ImageWatermark][23] 加载图像、徽标或照片。它将用作图像水印。
* 设置图像水印属性，如旋转、大小、不透明度、颜色和位置。
* 设置将应用水印的幻灯片索引。
* 使用 [add][24] 方法将图像水印添加到演示文稿中。
* 使用 [save][25] 方法保存带有图像水印的演示文稿。

以下代码示例将图像水印添加到 Java PPTX 演示文稿的第二张幻灯片中。

```
/*
* 示例：如何在 Java 中为演示幻灯片添加图像水印
*/
Watermarker watermarker = new Watermarker("path/presentation.pptx");

// 准备图像、大小、位置和外观
ImageWatermark imageWatermark = new ImageWatermark("path/watermarkImage.png");
imageWatermark.setX(80);
imageWatermark.setY(110);
imageWatermark.setOpacity(0.7);
// 设置水印的幻灯片索引
PresentationWatermarkSlideOptions imageWatermarkOptions = new PresentationWatermarkSlideOptions();
imageWatermarkOptions.setSlideIndex(1);

// 将图像水印添加到演示文稿
watermarker.add(imageWatermark, imageWatermarkOptions);
watermarker.save("path/image-watermarked-presentation.pptx");

watermarker.close();
imageWatermark.close();
```

以下是仅在 PPT/PPTX 的第二张幻灯片上带有图像水印的代码的输出。



{{< figure align=center src="images/image-watermark-to-slide-in-Java.png" alt="图像水印到演示幻灯片">}}


## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][26] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您已经学习了如何在 Java 中为演示文稿添加水印。更准确地说，我们讨论了如何在基于 Java 的应用程序的演示文稿中插入文本水印和图像水印。您可以将水印应用于所有幻灯片以及演示文稿的任何特定幻灯片。

使用 [文档][27] 了解有关 API 的更多信息。示例可在 [GitHub][28] 上找到。如有疑问，请通过 [论坛][29] 联系我们。

## 也可以看看

* [Java 中的水印 Excel 工作表][30]
* [在Java中为图像和照片添加水印][31]
* [在Java文档中查找和删除水印][32]
* [使用 C# 的水印演示幻灯片][33]







[1]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[2]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[3]: #java-watermarking-api
[4]: #text-watermark-to-slides
[5]: #image-watermark-to-slides
[6]: https://products.groupdocs.com/watermark/
[7]: https://docs.fileformat.com/presentation/ppt/
[8]: https://docs.fileformat.com/presentation/pptx/
[9]: https://docs.fileformat.com/presentation/pps/
[10]: https://docs.fileformat.com/presentation/pptm/
[11]: https://docs.fileformat.com/presentation/ppsx/
[12]: https://docs.groupdocs.com/watermark/java/
[13]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[14]: https://downloads.groupdocs.com/watermark
[15]: https://github.com/groupdocs-watermark
[16]: https://apireference.groupdocs.com/conversion/java
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[19]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[20]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[21]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[22]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[23]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[24]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[25]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String,%20com.groupdocs.watermark.options.SaveOptions)
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/watermark/
[28]: https://github.com/groupdocs-watermark
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[31]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[32]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[33]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/


