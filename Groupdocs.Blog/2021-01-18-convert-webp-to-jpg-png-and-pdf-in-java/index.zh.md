---
title: "在 Java 中将 WebP 转换为 JPG、PNG 和 PDF"
date: Mon, 18 Jan 2021 22:52:00 +0000
draft: false
url: /zh/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/
aliases:
- /2020/01/26/convert-webp-to-png-jpg-and-pdf-in-java/
- /2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
author: 'Shoaib Khan'
summary: "WebP 图像**提供像 PNG 一样的透明度**，**像 GIF 一样的动画**，对于任何 Web 开发人员来说，最重要的是 **比比较质量的 JPG 格式更小**。但是，由于不兼容问题或任何其他要求，有时需要将 WebP 图像转换为 JPG、PNG 或其他格式。"
tags: ['convert WebP to JPG in java', 'Convert WebP to PNG in Java', 'Java Convert WebP', 'Java WebP to JPG', 'Java WebP to PDF', 'Java WebP to PNG']
categories: ['GroupDocs.Conversion Product Family']
---

WebP 是 [Google][1] 引入的图像格式，可为网络上的图像提供无损和有损压缩。与众所周知且广泛使用的图像格式（如 PNG 和 JPG）相比，WebP 图像的尺寸更小，因此提供了更快的 Web 体验。



{{< figure align=center src="images/webp-to-jpg-converter-free-online.jpg" alt="免费在线 WebP 到 JPG 转换器">}}


_如果您只是为了在线将 WebP 文件转换为 JPG、PNG 或 PDF 文档，请使用使用 GroupDocs.Conversion API 开发的 [GroupDocs 提供的免费在线 WebP 转换工具][2]。但是，如果您想在 Java 中以编程方式实现确切的目标，请继续阅读。_

WebP 图像**提供像 PNG 一样的透明度**，**像 GIF 一样的动画**，对于任何 Web 开发人员来说，最重要的是 **比比较质量的 JPG 格式更小**。但是，由于不兼容问题或任何其他要求，有时需要将 WebP 图像转换为 JPG、PNG 或其他格式。

* [Java API 转换 WebP 图像][3]
* [在 Java 中将 WebP 转换为 JPG][4]
* [使用 Java 中的高级选项将 WebP 转换为 JPG、PNG、TIFF][5]
* [Java 中 WebP 到 PDF 的转换][6]



{{< figure align=center src="images/convert-webp-to-jpg-png-tiff-with-options.jpg" alt="在 Java 和 C# 中将 WebP 图像转换为 JPG、PNG 或 PDF 格式" caption="**原始 WebP 图像通过颜色调整和选项更改为 JPG 格式。** 使用的图像：[花中的野樱桃 (Prunus avium)][7]。图片作者：本杰明·吉梅尔。根据 [Creative Commons][8] [Attribution-Share Alike 3.0 Unported][9] 许可获得许可的照片。">}}


## 用于转换 WebP 图像的 Java API {#image-conversion-java-api}

GroupDocs 提供 [解决方案][10] 来转换 50 多种文档和图像文件格式。作为 Java 开发人员，您可以使用 [GroupDocs.Conversion for Java][11] 在基于 Java 的应用程序中转换 WebP 图像。

您可以从 [下载部分][12] 下载 **JAR** 文件，或者只需在 **基于 maven 的** Java 应用程序的 pox.xml 中添加以下存储库和依赖项配置。

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
        <version>20.10.3</version> 
</dependency>
```

在使用 GroupDocs.Conversion API 时，您可以使用 [Converter][14] 类的 [getPossibleConversions()][13] 方法获取源文档或图像可能的转换格式。有几种方法可以获得可能的转换，您可以访问[文档][15]或[API参考][16]。

## 在 Java 中将 WebP 转换为 JPG {#convert-webp-to-jpg-in-java}

以下步骤可帮助您将 WebP 图像转换为 JPG 或其他格式：

* 用WebP图像文件初始化[Converter][17]类对象。
* 使用 [ImageConvertOptions][18] 的 **setFormat** 方法将转换格式设置为 JPG。
* 使用 convert 方法将 WebP 转换为 JPG。

下面的 Java 源代码显示了将 WebP 转换为 JPG 格式是多么容易。要转换为其他一些支持的格式，您只需通过设置适当的 ImageFileType 来更改图像的输出格式。例如，要将 WebP 转换为 PNG，只需将下面的 ImageFileType 从 JPG 更改为 PNG。

```
// 使用 GroupDocs.Conversion API 在 Java 中将 WebP 转换为 JPG
Converter converter = new Converter("filePath/WebPImage.webp");
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
converter.convert("path/WebPToJPG.jpg", options);
```

## 使用 Java 中的高级选项将 WebP 转换为 JPG、PNG、TIFF {#convert-webp-with-advanced-options-in-java}

在将 WebP 转换为 JPG、PNG 或其他格式时，您还可以对输出图像应用颜色调整。您可以更改生成图像的对比度、亮度和伽玛值。图像可以翻转、旋转、加水印，或者得到灰度图像作为输出。

上面，我展示了使用下面提到的 Java 代码应用不同变体后从 WebP 转换为 JPG 格式的结果图像。

```
// 在 Java 中将 WebP 转换为 JPG、PNG、GIF、TIFF 并应用翻转、亮度、对比度、伽玛、旋转、水印等过滤器 
Converter converter = new Converter("filePath/WebPImage.webp");

// 设置图像转换选项。您可以一次应用一个过滤器。
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
options.setFlipMode(ImageFlipModes.FlipX);
options.setBrightness(50);
options.setContrast(50);
options.setGamma(0.5F);
options.setGrayscale(true);
options.setRotateAngle(90);

// 设置水印文字和外观 
WatermarkOptions watermark = new WatermarkOptions();
watermark.setText("GroupDocs");
watermark.setFont(new Font("Arial", Font.BOLD, 130));
watermark.setColor(Color.WHITE);
watermark.setBackground(false);
watermark.setRotationAngle(-45);
watermark.setTop(70);
watermark.setLeft(150);
watermark.setTransparency(0.2);
options.setWatermark(watermark);

converter.convert("filePath/WebPToJPG.jpg", options);
```

## Java中的WebP到PDF转换 {#webp-to-pdf-conversion-in-java}

除了将 WebP 转换为其他图像格式外，GroupDocs.Conversion API 还允许将 WebP 转换为 PDF 等文档格式。以下示例展示了如何快速将 WebP 图像转换为 PDF（可移植文档格式）。您可以使用相关的 [转换选项][19] 对生成的 PDF 文件进一步应用不同的自定义。

```
// 使用 GroupDocs.Conversion API 在 Java 中将 WebP 转换为 PDF
Converter converter = new Converter("filePath/WebPImage.webp");
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("filePath/WebPToPDF.pdf", options);
```

[GitHub 存储库][20] 上还有许多其他开源示例可供公开获得。下载源代码并使用 [入门][21] 指南快速运行示例。如有任何困难，请查看 [文档][22] 或随时在 [论坛][23] 上与我们联系。

## 结论

我认为，作为一名 Java 开发人员，您现在有信心以编程方式将 WebP 图像转换为 JPG、PNG、GIF、TIFF、PDF 和其他 Java 格式。您现在可以轻松地将颜色调整（对比度亮度、伽玛、灰度）更改为转换后的格式，并翻转、旋转或应用水印。

为什么不创建自己的基于 Java 的应用程序？它可以转换支持的图像格式并应用不同的滤镜和颜色变化。

祝您编码愉快！

## 也可以看看

* [在 C# 中将 WebP 转换为 JPG、PNG、TIFF 和 PDF][24]







[1]: https://developers.google.com/speed/webp
[2]: https://products.groupdocs.app/conversion/webp-to-jpg
[3]: #image-conversion-java-api
[4]: #convert-webp-to-jpg-in-java
[5]: #convert-webp-with-advanced-options-in-java
[6]: #webp-to-pdf-conversion-in-java
[7]: http://commons.wikimedia.org/wiki/File:Fr%C3%BChling_bl%C3%BChender_Kirschenbaum.jpg
[8]: http://en.wikipedia.org/wiki/en:Creative_Commons
[9]: http://creativecommons.org/licenses/by-sa/3.0/deed.en
[10]: https://products.groupdocs.com/conversion
[11]: https://products.groupdocs.com/conversion/java
[12]: https://downloads.groupdocs.com/conversion/java
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#getAllPossibleConversions()
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://docs.groupdocs.com/conversion/java/get-possible-conversions/
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#getPossibleConversions()
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions
[19]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/package-frame
[20]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java
[21]: https://docs.groupdocs.com/display/conversionjava/Getting+Started
[22]: https://docs.groupdocs.com/display/conversionjava/Home
[23]: https://forum.groupdocs.com/c/conversion
[24]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/


