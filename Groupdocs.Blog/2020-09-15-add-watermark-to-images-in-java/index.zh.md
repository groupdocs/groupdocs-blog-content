---
title: "在 Java 中为图像添加水印"
date: Tue, 15 Sep 2020 14:16:12 +0000
draft: false
url: /zh/2020/09/15/add-watermark-to-images-in-java/
author: 'Shoaib Khan'
summary: "在本文中，我们将学习**使用 Java 为图像添加文本和图像水印**。有两种方法可以为图像添加水印。您想要添加带有个性化文本的水印或在源图像上添加图像水印。我们将看到这两种情况。目前，除了 JPG 和 PNG，此 Java API 还支持 BMP、GIF、JP2、TIFF 和 WebP 图像格式，以便在其上添加水印。我们还可以更改水印文本的样式、方向和外观。"
tags: ['add text and image watermarks java', 'add text to images in Java', 'image watermarks in Java', 'text watermarks in Java']
categories: ['GroupDocs.Watermark Product Family']
---

担心如何使用 Java 以编程方式在图像上写入文本？在本文中，我们将学习**使用 Java 为图像添加文本和图像水印**。以前，我们已经在另一个 [post][1] 中看到了使用 C# 的相同内容。



{{< figure align=center src="images/text-watermark-on-png-using-java.png" alt="使用Java将文本水印添加到PNG图像">}}


有两种方法可以为图像添加水印。您想要添加带有个性化文本的水印或在源图像上添加图像水印。我们将看到这两种情况。

* [在图像中插入**文本水印**][2]
* [在图像中插入**图像水印**][3]

## Java 文本和图像水印 API

在下面的示例中，我们将使用 [GroupDocs.Watermark for Java][4] API 为 JPG 和 PNG 图像添加基于文本和图像的水印。如果您从下载部分 [下载][5] 水印 API 或使用同一页面中提到的配置将其集成到基于 Maven 的应用程序中会更好。

## 使用 Java 将文本添加到图像作为水印 {#add-text-watermark-to-images-in-java}

按照下面提到的步骤和 java 代码，我们可以快速将文本添加到任何图像文件中作为水印。我使用相同的步骤和下面提到的代码为以下 JPG 和 PNG 图像添加了水印。



{{< figure align=center src="images/text-watermark-on-jpg-using-java.jpg" alt="使用 Java 将文本水印添加到 JPG 图像">}}


目前，除了显示的 **JPG** 和 **PNG** 之外，此 Java API 还支持 **BMP、GIF、JP2、TIFF 和 WebP** 图像格式，以便为其添加水印。

* 使用个性化的文本和样式实例化 [TextWatermark][6] 对象。
* 调整文字水印设置。
* 使用源图像实例化 [Watermarker][7]。
* 使用 [add][8] 方法在图片中插入水印。
* 使用 [save][9] 方法保存输出图像。

这是将文本水印添加到 JPG 图像的 Java 源代码。如果我们需要将水印应用到 JPG 以外的图像上，则不需要大的改动。只需为该图像提供 _Watermarker_ 和 _save_ 方法的扩展名。就是这样。

我们还可以更改水印文本的**样式**、**方向**和**外观**。

```
// 使用 Java 将文本水印添加到 PNG
TextWatermark watermark = new TextWatermark("GroupDocs", new Font("Arial", 30, FontStyle.Bold | FontStyle.Italic));

// 设置水印属性
watermark.setForegroundColor(Color.getBlack());
watermark.setTextAlignment(TextAlignment.Right);
watermark.setRotateAngle(-30);
watermark.setOpacity(0.4);
watermark.setX(70);
watermark.setY(70);

// 将水印添加到源 PNG 图像
Watermarker watermarker = new Watermarker(Constants.PNG_GD);
watermarker.add(watermark);
watermarker.save(Constants.OUTPUT_PNG_PATH);
watermarker.close();
```

## 使用 Java 在图像上插入图像水印 {#add-image-watermark-to-images-in-java}



{{< figure align=center src="images/image-watermark-on-jpg-image-using-java.jpg" alt="使用 Java 将图像水印添加到 JPG 图像">}}


除了向图像添加文本外，我们还可以在源图像上添加图像作为水印。按照上面提到的类似步骤，但现在您必须使用 **[ImageWatermark][10]** 类而不是之前使用的 _TextWatermark_ 在 JPG 和 PNG 图像上添加文本。

这个 [image][11] 是使用下面提到的 Java 源代码创建的，它显示了我们如何在源 JPG 图像上添加 PNG 图像水印：

```
// 使用Java将PNG图像水印添加到JPG
ImageWatermark watermark = new ImageWatermark(Constants.Watermark_PNG);
watermark.setX(20);
watermark.setY(80);
// 将水印添加到源 JPG 图像并保存输出
Watermarker watermarker = new Watermarker(Constants.JPG_IMAGE);
watermarker.add(watermark);
watermarker.save(Constants.JPG_IMAGE_OUTPUT);
watermark.close();
watermarker.close();
```

## 结论

我们已经了解了如何使用 Java 以编程方式在任何图像上添加文本和图像作为水印。此外，我们更改了水印文本的文本样式和方向。

您可以浏览 [documentation][12] 以了解 GroupDocs.Watermark for Java 的更多功能。如有不明之处，可直接联系【免费支持】【13】快速回复，

## 也可以看看

* [使用 C# 为图像添加水印][14]
* [Java 中的水印 Excel 工作表][15]
* [从Java文档中去除水印][16]







[1]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/#add-text-watermark-to-images-in-java
[3]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/#add-image-watermark-to-images-in-java
[4]: https://products.groupdocs.com/watermark/java
[5]: https://downloads.groupdocs.com/watermark/java
[6]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[7]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[8]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[9]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[11]: https://blog.groupdocs.com/wp-content/uploads/sites/4/2020/09/image-watermark-on-jpg-image-using-java.jpg
[12]: https://docs.groupdocs.com/watermark/java/
[13]: https://forum.groupdocs.com/c/watermark
[14]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[15]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[16]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/


