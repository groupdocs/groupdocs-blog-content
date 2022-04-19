---
title: "从 Java 中的 EPUB、FB2、CHM 电子书中提取图像"
date: Mon, 15 Mar 2021 15:01:00 +0000
draft: false
url: /zh/2021/03/15/extract-images-from-ebooks-in-java/
author: 'Shoaib Khan'
summary: "**各种格式的电子书**在日常使用中非常普遍。电子书可以包含文本和图像。如果您想在其他地方使用任何电子书的图像，您可以在 Java 应用程序中以编程方式轻松提取这些图像。在本文中，您将学习自动化，**如何从电子书**文件中提取图像，例如 **Java** 中的 **EPUB、PDF、FB2、CHM**。"
tags: ['Extract Images from CHM in Java', 'Extract Images from eBooks in Java', 'Extract Images from FB2 in Java', 'extract images in Java', 'Parse eBooks in Java', 'Parse eBooks to Extract Images in Java']
categories: ['GroupDocs.Parser Product Family']
---

**各种格式的电子书**在日常使用中非常普遍。电子书可以包含文本和图像。如果您想在其他地方使用任何电子书的图像，您可以在 Java 应用程序中以编程方式轻松提取这些图像。在本文中，您将学习自动化，**如何从电子书**文件中提取图像，例如 **Java** 中的 **EPUB、PDF、FB2、CHM**。

下面将介绍以下主题：

* [Java API - 从电子书中提取图像][2]
* [用 Java 从 EPUB 电子书中提取图像][3]
* [用 Java 从 PDF、FB2、CHM 电子书中提取图像][4]

## 用于从电子书中提取图像的 Java API {#image-extraction-java-api-for-ebooks}

[GroupDocs.Parser for Java][5] API 是一个功能丰富的自动化 API，用于从 Java 中的电子书和文档中提取图像。除此之外，API 还支持从文字处理文档、电子表格、PDF、演示文稿、电子邮件、ZIP 档案和许多其他 [支持的文档格式][6] 中解析和提取图像、文本和元数据。

### 下载并配置

从 [downloads][7] 部分获取 JAR 文件，或者在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置以尝试以下示例。有关详细信息，您可以访问 [API 参考][8]。

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
	<artifactId>groupdocs-parser</artifactId>
	<version>21.2</version> 
</dependency>
```

## 用 Java 从 EPUB 电子书中提取图像 {#extract-images-from-epub-in-java}

让我们从 EPUB 电子书开始解析它的图像。以下步骤解析 EPUB 电子书并使用 Java 代码从中提取所有图像。

* 使用电子书创建 [Parser][9] 类对象。
* 使用 [getImages][10] 方法提取 EPUB 电子书的所有图像。
* 遍历提取的图像并将它们保存到磁盘。



{{< figure align=center src="images/alice.png" alt="带图像的 EPUB 电子书" caption="Adobe 的 EPUB 电子书 [示例电子书库][11]">}}


下面的 Java 代码解析 EPUB 电子书，并将电子书的图像一张一张地保存到磁盘中。

```
// 解析电子书以从 Java 中的 PDF、EPUB、FB2、CHM 文件中提取图像并保存到磁盘。
Parser parser = new Parser("ebook.epub");
// 从电子书中提取图像并以 JPEG 格式保存。
Iterable<PageImageArea> images = parser.getImages();
ImageOptions options = new ImageOptions(ImageFormat.Jpeg);
int imageNumber = 0;
// 迭代提取的图像
for (PageImageArea image : images) {
    image.save(Constants.getOutputFilePath(String.format("%d.jpeg", imageNumber)), options);
    imageNumber++;
}
```



{{< figure align=center src="images/alice-image-from-epub.jpg" alt="从 EPUB 电子书中提取的图像">}}


结果，所有图像都将保存到提供的位置。这是作为示例显示的图像之一。

图像可以保存为以下任何图像文件格式：

* JPG
* PNG
* WEBP
* 动图
* BMP

## 用 Java 从 PDF、FB2、CHM 电子书中提取图像 {#extract-images-from-pdf-fb2-chm-in-java}

除了 EPUB 格式，如果您有 PDF、FB2、CHM 或其他格式的电子书，您可以以相同的方式提取它们的图像。只需在创建对象时将您的电子书传递给 **Parser** 构造函数。之后，**getImages** 方法将使用相同的 Java 代码从您提供的电子书中提取图像。

```
// Provide different eBook formats to the Parser constructor to extract the images.
// Parser parser = new Parser("ebook.epub");
Parser parser = new Parser("ebook.pdf");
// Parser parser = new Parser("ebook.fb2");
// Parser parser = new Parser("ebook.chm");

Iterable<PageImageArea> images = parser.getImages();
```

## 结论

在本文中，您学习了在 Java 应用程序中以编程方式从 PDF、EPUB、FB2、CHM 电子书中获取所有图像。现在您可以尝试使用 [GroupDocs.Parser for Java][12] API 构建您自己的图像提取 Java 应用程序。

有关 API 的更多信息，您可以访问 [文档][13] 或 [GitHub][14] 上的开源示例。对于任何其他问题，您可以在 [论坛][15] 上联系快速支持。

## 也可以看看

* [用 C# 从 EPUB、FB2、CHM 电子书中提取图像][16]
* [用Java从发票和收据中提取数据][17]







[1]: https://blog.groupdocs.com/2021/03/15/extract-images-from-ebooks-in-java/
[2]: #image-extraction-java-api-for-ebooks
[3]: #extract-images-from-epub-in-java
[4]: #extract-images-from-pdf-fb2-chm-in-java
[5]: https://products.groupdocs.com/parser/java
[6]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/parser/java
[8]: https://apireference.groupdocs.com/parser/java
[9]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[10]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getImages()
[11]: https://www.adobe.com/solutions/ebook/digital-editions/sample-ebook-library.html
[12]: https://products.groupdocs.com/parser/net
[13]: https://docs.groupdocs.com/parser/java
[14]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java
[15]: https://forum.groupdocs.com/c/parser/
[16]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[17]: https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/


