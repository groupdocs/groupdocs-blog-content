---
title: "Java中的图像比较以发现差异"
date: Wed, 16 Jun 2021 14:07:12 +0000
draft: false
url: /zh/2021/06/16/compare-images-in-java/
author: 'Shoaib Khan'
summary: 'Worried! What is the difference? **Better automate the photo comparison.** In this article, we will discuss how to programmatically find differences between two images. After going through this, you will easily compare any images and highlight the identified differences using Java.

以下主题涵盖以下内容：

* 用于比较图像的 Java API
*比较Java中的图像以突出差异

[继续阅读...][1]'
tags: ['compare images in java', 'compare jpg in java', 'compare png in java', 'Image Comparison', 'Image Comparison Java API']
categories: ['GroupDocs.Comparison Product Family']
---

担心！有什么不同？ **更好地自动化照片比较。** 在本文中，我们将讨论如何以编程方式查找两张图像之间的差异。完成此操作后，您会发现使用 Java 比较任何图像并突出显示已识别的差异很容易。



{{< figure align=center src="images/images-for-comparison.jpg" alt="用于比较的相同图像">}}


以下主题涵盖以下内容：

* [比较图像的Java API][2]
* [比较Java中的图像以突出差异][3]

## 图像比较 Java API {#image-comparison-java-api}

在本文中，我将使用 [GroupDocs.Comparison 的 Java API][4] 来比较图像。除了最常用的图像格式（如 PNG、JPG/JPEG 和 GIF）外，还有 [用于比较的广泛支持的文件格式][5]。此外，API 允许比较文字处理文档、电子表格、演示文稿、绘图、网页、电子邮件、源代码文件等等。

### 下载并配置

从 [下载][6] 部分获取图像比较库。对于基于 Maven 的 Java 应用程序，在 pom.xml 中添加以下配置。稍后，您可以尝试本文的示例以及 [GitHub][7] 中的更多示例。有关详细信息，您也可以访问 [API 参考][8]。

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
        <artifactId>groupdocs-comparison</artifactId>
        <version>21.6</version> 
</dependency>
```

## 比较 Java 中的图像以突出显示差异 {#compare-image-and-highlight-differences}

比较图像并获得结果只需 3 行代码。您可以按照这些步骤并使用上述源代码来比较您的任何 JPG、PNG、BMP、DICOM、DjVu、GIF 和其他图像。您可以在 Java 应用程序中识别它们之间的差异或变化。

以下步骤显示了如何比较任意两个图像的差异。

* 使用 [Comparer][9] 类选择要比较的第一张图像。
* 使用适当的 [add][10] 方法添加第二张图片进行比较。
* 调用[compare][11]方法得到两张图片的比较结果。

以下代码显示了如何在 Java 中比较两个图像。它比较两个 JPG 图像并保存突出显示已识别差异的输出。

```
// 比较两个图像并突出 Java 中的差异
Comparer comparer = new Comparer("image-a.jpg")
comparer.add("image-b.jpg");
comparer.compare("result-Image.jpg"); // This will return the path of the resultant image.
```

这是上述代码的输出图像。此外，输出还包括比较的摘要。



{{< figure align=center src="images/compared-image.jpg" alt="图像比较自动化并突出显示差异">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][12] 以便在没有评估限制的情况下使用 API。

## 结论

总结这篇文章，我们学会了在 Java 中比较图像。我们进一步强调了比较后发现的差异。现在，您可以构建自己的照片比较器应用程序或在 Java 应用程序中使用这些功能。

有关更多详细信息、选项和示例，您可以浏览 [documentation][13] 和 [GitHub][14] 存储库。在 [论坛][15] 上与我们联系以获取您的查询。

## 也可以看看

* [比较 C# 中的图像以找出差异][16]
* [使用 Java 比较任何文档][17]







[1]: https://blog.groupdocs.com/2021/06/16/compare-images-in-java/
[2]: #image-comparison-java-api
[3]: #compare-image-and-highlight-differences
[4]: https://products.groupdocs.com/comparison/
[5]: https://docs.groupdocs.com/comparison/java/supported-document-formats/
[6]: https://downloads.groupdocs.com/comparison/java
[7]: https://github.com/groupdocs-comparison
[8]: https://apireference.groupdocs.com/comparison/java
[9]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer
[10]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String)
[11]: https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String)
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/comparison/java/
[14]: https://github.com/groupdocs-comparison
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/
[17]: https://blog.groupdocs.com/2020/07/15/compare-text-word-pdf-files-with-java-difference-library/


