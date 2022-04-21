---
title: "Java中的水印密码保护文档"
date: Fri, 26 Nov 2021 09:36:00 +0000
draft: false
url: /zh/2021/11/26/watermark-password-protected-documents-in-java/
author: 'Shoaib Khan'
summary: ''
tags: ['Document Watermarking', 'Watermark Protected Documents using Java', 'Watermark Protected Files', 'Watermark Protected Files using Java', 'watermark using java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/watermark-protected-files-using-java.jpg" alt="使用 Java 的水印保护文档">}}


水印可用于保护内容并声明文档的所有权。同样，这些也可用于将您的文档标记为草稿或标记。本文讨论了**如何在 Java 中为受密码保护的文件添加水印**。我们将使用代码示例将文本和图像水印添加到受保护的文件中。

此处讨论了以下主题：

* [Java API 到水印密码保护文件][1]
* [使用 Java 为受保护的文件添加水印][2]
    * [插入文字水印][3]
    * [插入图片水印][4]

## 用于水印密码保护文件的 Java API {#watermarking-java-api}

[GroupDocs.Watermark][5] 在您的应用程序中展示了[允许使用水印的水印 Java API][6]。我们将使用此 API 将文本和图像水印插入到受密码保护的文档中。

您可以从 [下载部分][7] 下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][8] 配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## 使用 Java 向受密码保护的文件添加水印 {#add-watermark-to-protected-files}

只需几行代码，您就可以根据需要自定义水印并将其应用于您的文件。按照以下步骤添加两种类型的水印。

* **加载**受保护的文件。
* **应用**水印。
* **保存**带水印的文件。

现在，我们将一一添加文本水印，然后添加图像水印。

## 在 Java 中为受保护的文件添加文本水印 {#text-watermark-to-protected-files}

文本水印可用于将文档提及为 DRAFT 或 CONFIDENTIAL；或出于类似目的。以下步骤展示了如何在 Java 中将文本水印添加到受密码保护的文档中。

* 使用现有密码准备[加载选项][9]。
* 使用加载选项加载具有 [Watermarker][10] 类的受保护文件。
* 使用 [TextWatermark][11] 类定义水印。
* 设置水印的文字、外观、旋转、不透明度、颜色等属性。
* 使用 [add()][12] 方法将水印添加到文档中。
* 使用[save()][13]方法保存水印文件。

以下 Java 代码片段将文本水印插入到受保护的 PDF 文档中。

```
/*
 * Apply Text Watermark to document (PDF, Word, PPT, Excel, ...) in Java
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("P@$$w0rd");

String filePath = "path/document.pdf";
Watermarker watermarker = new Watermarker(filePath, loadOptions);

TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 36));
watermark.setForegroundColor(Color.getRed());
watermark.setOpacity(0.3);
watermark.setRotateAngle(-45);

watermarker.add(watermark);
watermarker.save("path/watermark-document.pdf");
```

## 在 Java 中为受保护的文件添加图像水印 {#image-watermark-to-protected-files}

您还可以插入任何图像或徽标作为水印。要添加图像，请使用 **ImageWatermark** 类。以下步骤允许将图像水印添加到 Java 中受密码保护的文档中。

* 使用现有密码为受保护文件准备[加载选项][14]。
* 使用 [Watermarker][15] 类和**加载选项**加载文件。
* 使用 [ImageWatermark][16] 类加载图像文件。
* 设置水印的外观、对齐方式、坐标、旋转、不透明度等属性。
* 现在，使用 [add()][17] 方法为文档添加水印。
* 最后，使用[save()][18]方法保存水印文件。

以下 Java 代码示例将图像水印插入到受保护的 PDF 文件中。

```
/*
 * Apply Image Watermark to document (PDF, Word, PPT, Excel, ...) in Java
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("P@$$w0rd");

String filePath = "path/document.docx";
Watermarker watermarker = new Watermarker(filePath, loadOptions);

ImageWatermark watermark = new ImageWatermark("path/watermark-image.png");
watermark.setOpacity(0.7);
watermark.setX(70);
watermark.setY(350);

watermarker.add(watermark);
watermarker.save("path/watermark-document.docx");
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证][19] 免费使用这些 API。

## 结论

总而言之，我们讨论了在 Java 应用程序中向受密码保护的文件添加文本水印和图像水印。此外，我们在将水印应用于文档时自定义了水印的外观。

类似地，您可以将水印分别插入到特定的**页面、幻灯片和文档表**、**演示文稿**和**工作簿**。

有关详细信息，请参阅 [相关文章][20]，并从其 [文档][21] 中了解更多信息。如有疑问，请通过 [论坛][22] 联系我们。

## 相关文章 {#releated-articles}

* [在 Java 文档中查找并**删除水印**][23]
* [在Java中为**图像**添加水印][24]
* [Java 中的密码保护演示文稿][25]
* [使用 Java 将水印添加到**演示幻灯片**][26]
* [水印**PDF** Java 文件][27]







[1]: #watermarking-java-api
[2]: #add-watermark-to-protected-files
[3]: #text-watermark-to-protected-files
[4]: #image-watermark-to-protected-files
[5]: https://products.groupdocs.com/watermark/
[6]: https://products.groupdocs.com/watermark/java/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[9]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/LoadOptions
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/LoadOptions
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[16]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[19]: https://purchase.groupdocs.com/temporary-license
[20]: #releated-articles
[21]: https://docs.groupdocs.com/watermark/
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[24]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[25]: https://blog.groupdocs.com/2022/02/10/lock-unlock-ppt-pptx-files-with-password-in-java/
[26]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[27]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/


