---
title: "'在 Java 中将 AutoCAD DWG 工程图转换为 PDF'"
date: Tue, 08 Feb 2022 16:48:40 +0000
draft: false
url: /zh/2022/02/08/convert-cad-drawings-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "**CAD** 代表计算机辅助设计。它用于创建 2D 和 3D 建筑设计、计算机动画、电影中的特殊效果、技术图纸等等。 **PDF** 是最著名的文件格式之一，因其可移植性而闻名。当要将此类技术图纸传输给没有配备支持 CAD 图纸的技术软件的普通用户时，需要将 CAD 文件转换为 PDF 格式。本文将帮助程序员在 Java** 应用程序中添加该功能以将**转换**不同的 **CAD 格式**（如 **DWG、DGN 或 DWF) 转换为 PDF。"
tags: ['convert cad to pdf in java', 'convert dgn to pdf in java', 'convert dwf to pdf', 'convert dwg to pdf', 'convert dwg to pdf in java', 'dwg to pdf', 'DWG to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

**CAD** 代表计算机辅助设计。它用于创建 2D 和 3D 建筑设计、计算机动画、电影中的特殊效果、技术图纸等等。 **PDF** 是最著名的文件格式之一，因其可移植性而闻名。当要将此类技术图纸传输给没有配备支持 CAD 图纸的技术软件的普通用户时，需要将 CAD 文件转换为 PDF 格式。本文指导程序员如何**转换**不同的 **CAD 格式**，如 **DWG 到 Java 中的 PDF**。



{{< figure align=center src="images/convert-cad-drawings-to-pdf-using-java.png" alt="在 Java 中将 CAD 绘图转换为 PDF">}}


以下主题涵盖以下内容：

* [CAD 图纸转换 Java 库](#cad-conversion-java-lib)
* [将 DWG 转换为 PDF](#dwg-to-pdf)

## CAD 图纸转换 Java 库 {#cad-conversion-java-lib}



{{< figure align=center src="images/groupdocs-conversion-java.png" alt="使用 Java 转换文档和图像">}}


[GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java) 是基于Java 应用程序的文档和图像转换库。它支持从一种格式转换为另一种格式的各种文件格式，包括文字处理文档、电子表格、演示文稿、图像、便携式文档、网页、photoshop 格式、Microsoft Project 文件、电子邮件、Microsoft Visio 的矢量图形、CAD 绘图、页面描述语言等

在下面的示例中，我将使用此 API 来**将 CAD 图纸转换为 Java 中的 PDF**。最好先下载库并准备好开发环境。您可以从 [下载](https://downloads.groupdocs.com/conversion/java) 部分或通过基于 maven 的 Java 应用程序中的以下配置获取 API。

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

## 在 Java 中将 DWG 转换为 PDF {#dwg-to-pdf}

让我们开始快速转换绘图。通过这些步骤，您可以轻松地将 AutoCAD DWG 工程图转换为 Java 中的 PDF 文件，其中包含许多自定义选项。

* 使用 [CadLoadOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions) 类设置**加载选项**。
* 使用 [setLayoutNames()](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/CadLoadOptions#setLayoutNames(java.lang.String%5B%5D)) 方法指定布局。
* **使用 [Conveter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions) 类加载** DWG 图形。
* 指定**转换选项**，例如**宽度**、**高度**和**格式**。
* 使用适当的 [convert()](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)) 方法转换为 PDF。

这是演示上述步骤并将 DWG 文件转换为 PDF 格式的完整 Java 代码。

```
// 在 Java 中将 CAD 绘图 - DWG 转换为 PDF

// CAD 文件加载选项
CadLoadOptions loadOptions = new CadLoadOptions();
loadOptions.setLayoutNames(new  String[]{ "Layout1"});

// PDF 转换选项
PdfOptions pdfOptions = new PdfOptions();
pdfOptions.setGrayscale(true);

PdfConvertOptions options = new PdfConvertOptions();
options.setRotate(Rotation.On90);
options.setPdfOptions(pdfOptions);
/*
options.setDpi(300);
options.setWidth(800);
options.setHeight(600);
*/
// 转换
Converter converter = new Converter("filePath/CAD-Drawing.dwg", loadOptions);
converter.convert("filePath/cadToPDF-Java.pdf", options);
```

只需稍加更改代码，您还可以相应地转换 DGN 和 DWF 文件。对于不支持布局的文件格式，我们不会使用 **setLayoutNames** 方法。

## 结论

最后，我们学会了将 CAD 文件转换为 PDF 格式。具体来说，我们使用 Java API 将 AutoCAD DWG 图纸转换为 PDF 格式。您现在可以尝试使用 [GroupDocs.Conversion](https://products.groupdocs.com/conversion/) 构建您的在线 CAD 到 PDF 转换器 Java 应用程序。如有任何疑问，您可以联系**免费支持团队**，在 [论坛](https://forum.groupdocs.com/) 上为您提供帮助总是很愉快。

## 也可以看看

* [使用 Java 查看 CAD 文档](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
* [如何在 Java 中重新排列 PDF 页面](https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/)
* [Java 中的水印 PDF 文件](https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/)
* [Java中PDF文件的密码保护](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
* [Java 中拆分 PDF 文件的不同方法](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
* [在 C# 中将 CAD 绘图转换为 PDF](https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/)





