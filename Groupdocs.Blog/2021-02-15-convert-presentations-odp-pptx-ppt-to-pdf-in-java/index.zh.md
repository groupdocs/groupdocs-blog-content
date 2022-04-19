---
title: "在 Java 中将演示文稿转换为 PDF"
date: Mon, 15 Feb 2021 17:30:00 +0000
draft: false
url: /zh/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
author: 'Shoaib Khan'
summary: 'As PDF is the popular portable document format, so there comes the need to convert documents of other formats to PDF. Today, we will see **different ways to convert PPT, PPTX, or ODP presentations to PDF in Java**. In an earlier post, we have seen [how to convert presentations using C#][1].

[继续阅读...][2]'
tags: ['Convert ODP to PDF in Java', 'Convert PPT to PDF in Java', 'Convert PPTX to PDF in Java', 'Convert Presentation to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

由于 PDF 是流行的便携式文档格式，因此需要将其他格式的文档转换为 PDF。今天，我们将看到**用 Java 将 PPT、PPTX 或 ODP 演示文稿转换为 PDF 的不同方法**。在之前的一篇文章中，我们看到了[如何使用 C# 转换演示文稿][3]。本文将介绍以下场景：

* [演示转换Java API][4]
* [用 Java 将 PPT、PPTX 或 ODP 演示文稿转换为 PDF][5]
* [将演示文稿的特定幻灯片转换为 PDF][6]
* [将演示文稿的连续幻灯片转换为 PDF][7]
* [将受密码保护的演示文稿转换为 PDF][8]



{{< figure align=center src="images/convert-ppt-to-pdf-in-java.jpg" alt="Java 中的 PPTX 到 PDF">}}


## 表示转换 Java API {#presentation-conversion-java-api}

对于将演示文稿转换为 PDF 格式，我将在本文的示例中使用 [GroupDocs.Conversion for Java][9]。除了这一特性，API 还支持很长的 [在 Java 中相互转换的文件格式列表][10]。其中包括转换**电子书、文字处理文档、电子表格、图像、网页、电子邮件、CAD** 和许多其他文档格式。

### 下载或配置



{{< figure align=center src="images/groupdocs-conversion-java.png" alt="使用 Java 转换文档和图像">}}


[下载 JAR][11] 从下载或在基于 Maven 的 Java 应用程序的情况下，在 pom.xml 中添加以下存储库和依赖项配置。

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
        <version>21.1</version> 
</dependency>
```

## 在 Java 中将 PPT、PPTX 或 ODP 演示文稿转换为 PDF {#convert-presentations-to-pdf-in-java}

在您的项目中配置库后，您现在可以使用多种选项将演示文稿转换为可移植的 PDF 格式。让我们从最简单、最快捷的方式开始转换整个演示文件。

* 使用源文档创建 [Converter][12] 类对象。
* 实例化 [PdfConvertOptions][13] 对象。
* 调用 Converter 类的 **convert** 方法。传递输出文件路径和创建的 PdfConvertOptions。

这是将 PowerPoint PPTX 演示文稿文件转换为 PDF 的 3 行 Java 代码。

```
// 使用 Document Conversion API 在 Java 中将演示文稿转换为 PDF
Converter converter = new Converter("presentation.pptx");
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("pptxToPDF.pdf", options);
```

同样，您可以使用本文相同的示例将 Microsoft PowerPoint PPT 格式或 OpenOffice Impress ODP 格式的演示文稿转换为 PDF。

## 在 Java 中将演示文稿的特定幻灯片转换为 PDF {#convert-ppt-slides-to-pdf-in-java}

如果您想从演示文稿中跳过几张幻灯片，或者只想将某些特定幻灯片转换为 PDF 而不是转换整个演示文稿，**setPages** 是您正在搜索的方法。

下面的代码将 PPTX 演示文稿的选定页面转换为 Java 中的 PDF。

```
// 在 Java 中将指定的演示文稿幻灯片转换为 PDF
Converter converter = new Converter("presentation.pptx");
PdfConvertOptions options = new PdfConvertOptions();
options.setPages(Arrays.asList( 2, 4));
converter.convert("PptSpecificSlidesToPDF.pdf", options);
```

## 在 Java 中将演示文稿的连续幻灯片转换为 PDF {#convert-ppt-consecutive-slides-to-pdf}

您还可以按顺序选择特定的幻灯片集以将它们转换为 PDF。只需提及起始幻灯片编号，然后是前面序列中的幻灯片数量。

* 从使用演示文件初始化 [Converter][14] 对象开始。
* 设置起始页码。
* 设置连续页数。
* 使用 **convert** 方法将幻灯片转换为 PDF。

这是显示上述步骤的 Java 代码，并将 PPTX 演示文稿的 3 张连续幻灯片从第 2 张幻灯片开始转换为 PDF。

```
// 在 Java 中将演示文稿的连续幻灯片转换为 PDF
Converter converter = new Converter("presentation.pptx");
PdfConvertOptions options = new PdfConvertOptions();
options.setPageNumber(2);
options.setPagesCount(3);
converter.convert("PptConsecutiveSlidesToPDF.pdf", options);
```

## 在 Java 中将受密码保护的演示文稿转换为 PDF {#convert-password-protected-ppt-to-pdf-in-java}

加载任何演示文稿时都有许多加载选项。您可以使用 **setPassword** 方法为受保护的演示文稿提供**密码**。使用密码加载演示文稿后，您可以像我们之前转换的任何其他演示文稿一样转换它。

以下代码在加载时提供密码后，将受密码保护的 PPTX 演示文稿转换为 Java 中的 PDF。

```
// 在 Java 中将受密码保护的演示文稿转换为 PDF
PresentationLoadOptions loadOptions = new PresentationLoadOptions();
loadOptions.setPassword("GroupDocs");

Converter converter = new Converter("presentation.pptx", loadOptions);
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("pwdPptToPDF.pdf", options);
```

此外，您可以设置以下加载选项：

* 指定演示文稿**格式**，但是，它是自动检测的。
* 显示或隐藏**评论**。
* 显示或隐藏**隐藏的幻灯片**。
* 指定缺失字体的替代字体。

## 结论

在尝试了上述示例之后，您必须有信心在 Java 应用程序中以编程方式将演示文稿和幻灯片转换为 PDF。您可以尝试使用上面强调的 MS PowerPoint 和 OpenOffice Impress 演示格式（如 PPT、PPTX、ODP 等）的功能构建自己的应用程序。

## 需要帮忙？

首先，从 [documentation][15] 中查看更多关于 API 转换功能的信息。我们将在 [论坛][16] 上帮助您解决任何进一步面临的问题。

## 也可以看看

* [在 C# 中将演示文稿（PPT、PPTX）转换为 PDF][17]







[1]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[2]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
[3]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[4]: #presentation-conversion-java-api
[5]: #convert-presentations-to-pdf-in-java
[6]: #convert-ppt-slides-to-pdf-in-java
[7]: #convert-ppt-consecutive-slides-to-pdf
[8]: #convert-password-protected-ppt-to-pdf-in-java
[9]: https://products.groupdocs.com/conversion/java
[10]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[11]: https://downloads.groupdocs.com/conversion/java
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://docs.groupdocs.com/conversion/java
[16]: https://forum.groupdocs.com/c/conversion
[17]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/


