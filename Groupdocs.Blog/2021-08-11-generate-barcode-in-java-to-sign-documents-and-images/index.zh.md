---
title: "在 Java 中生成条码 – 将条码添加到文档和图像"
date: Wed, 11 Aug 2021 17:05:00 +0000
draft: false
url: /zh/2021/08/11/generate-barcode-in-java-to-sign-documents-and-images/
aliases:
- /2017/09/12/groupdocs-signature-for-java-release-v17.6.0/
- /2017/09/12/add-barcode-and-qr-code-signatures-in-java-using-groupdocs-signature/
author: 'Shoaib Khan'
summary: "条形码是以机器可读格式呈现数据的方法之一。条形码通常用作大量物品的标识。在本文中，您将学习**如何在 Java 中生成条形码**。此外，您将看到生成的条形码如何在您的应用程序中使用 Java 签名 API 应用于您的任何**文档和图像**。"
tags: ['Add Barcode in Java', 'Apply Barcode to Images in Java', 'eSigning with Java', 'Generate Barcode in Java', 'Sign Documents in Java', 'Sign Documents with Barcode in Java', 'Sign Images with Barcode in Java']
categories: ['GroupDocs.Signature Product Family']
---

条形码是以机器可读格式呈现数据的方法之一。条形码通常用作大量物品的标识。在本文中，您将学习**如何在 Java 中生成条形码**。此外，您将看到生成的条形码如何在您的应用程序中使用 Java 签名 API 应用到您的任何**文档和图像**。

以下主题涵盖以下内容：

* [Java 条码生成器 API][1]
* [将条形码应用于 Java 文档][2]
* [将条形码应用于 Java 中的图像][3]

## 用于生成条形码的 Java API {#barcode-generator-java-api}

[GroupDocs.Signature][4] 展示了允许对文档、图像或不同文件格式的文件进行签名的 Java API。使用此 API，您可以轻松生成和应用不同类型的签名，如条形码、二维码、文本、图像、元数据、数字签名、图章、表单字段签名等。 API 还允许以多种方式自定义签名。

### 下载或配置

您可以从 [下载部分][5] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

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
        <artifactId>groupdocs-signature</artifactId>
        <version>21.5</version> 
</dependency>
```

## 在 Java 中为文档和图像生成条形码 {#generate-barcode-in-java}

可以使用自定义文本、外观和不同编码类型以编程方式生成条形码。一些受支持的条形码类型包括 Code 32、Code 128、DotCode、GS1、ISBN、PDF417、Postnet、UPCA 等等。这些条码可以应用于大量[支持的文档和图像格式][6]。

以下是将条形码应用于任何文档或图像的主要步骤。

* 加载文档或图像。
* 生成条形码以及文本、外观、编码和其他属性。
* 将生成的条形码附加到所选文件。



{{< figure align=center src="images/generate-barcode-using-java-1024x768.png" alt="在 Java 中生成条形码">}}


## 在 Java 中生成条形码并应用于文档 {#apply-barcode-to-documents}

生成条形码并根据需要对其进行定制并不是一个复杂的过程。无论目标文档是 MS Word 文档、PDF 文件、Excel 电子表格还是演示文稿，添加条形码的步骤对于所有不同格式都是相同的。以下步骤指导如何生成条形码并将其应用/附加到 Java 中的任何文档。

* 使用 [Signature][7] 类加载文档（PDF、Word 文档、电子表格、PPT……）。
* 使用 [BarcodeSignOptions][8] 类定义条形码选项。
* 设置条形码属性，如编码类型、位置、大小、背景或前景色、字体等。
* 调用[sign][9] 方法将生成的条形码附加到加载的文档中。

以下源代码使用 Java 生成条形码并将其附加到 PDF 文档。

```
// 在 Java 中生成条形码并将其应用于文档（DOC、DOCX、PDF、PPT、XLS、XLSX...）
Signature signature = new Signature("path/document.pdf");

// 使用条形码文本创建条形码选项
BarcodeSignOptions options = new BarcodeSignOptions("<00-0-0000-0> 2021-08");
options.setEncodeType(BarcodeTypes.Code128);

// 条码对齐和外观
options.setLeft(205);
options.setTop(170);
options.setHeight(50);
options.setWidth(200);
options.setForeColor(Color.BLUE);
options.setCodeTextAlignment(CodeTextAlignment.Below);

// 将条形码附在文件上
signature.sign(outputFilePath, options);
```

## 在 Java 中生成条形码并应用于图像 {#apply-barcode-to-images}

以非常相似的方式，您可以将条形码应用于图像。无论您有 JPG、PNG、WebP 图像还是任何其他图像格式（如 GIF、TIF、CDR、SVG 或任何其他格式），您都可以将条形码附加到加载的图像上。

以下是使用 Java API 生成条形码并将其应用于任何图像的步骤。

* 使用 [Signature][10] 加载您的图像（JPG、PNG、WebP……）。
* 使用 [BarcodeSignOptions][11] 准备条形码选项。
* 通过设置文本、编码类型、位置、大小、外观等自定义条码。
* 使用 [sign][12] 方法应用条形码对图像进行签名。

以下源代码生成条形码并将其附加到 Java 中的 JPG 图像。

```
// // 生成条形码并将其应用于 Java 中的图像（JPG、PNG、BMP、...）
Signature signature = new Signature("path/image.jpg");

// 使用条形码文本创建条形码选项
BarcodeSignOptions options = new BarcodeSignOptions("<00-0-0000-0> 2021-08");
options.setEncodeType(BarcodeTypes.Code128);

// 条码对齐和外观
options.setLeft(100);
options.setTop(100);
options.setHeight(50);
options.setWidth(200);
options.setForeColor(Color.BLUE);
options.setCodeTextAlignment(CodeTextAlignment.Above);

// 附上图片的条形码
signature.sign(outputFilePath, options);
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][13] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您已经学习了如何在 Java 中生成条形码。此外，您还了解了如何将这些生成的条形码添加到您的图像和文档中。现在您可以开发自己的条形码生成器 Java 应用程序。

您可以使用 [文档][14] 或通过 [GitHub][15] 上提供的示例了解有关 Java 签名 API 的更多信息。在 [论坛][16] 上与我们联系。

## 也可以看看

* [用Java生成图像和文档的二维码][17]
* [在 C# 中为文档和图像生成二维码][18]







[1]: #barcode-generator-java-api
[2]: #apply-barcode-to-documents
[3]: #apply-barcode-to-images
[4]: https://products.groupdocs.com/signature/
[5]: https://downloads.groupdocs.com/signature
[6]: https://docs.groupdocs.com/signature/java/supported-document-formats/
[7]: https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature
[8]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.sign/BarcodeSignOptions
[9]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#sign(java.io.OutputStream,%20com.groupdocs.signature.options.sign.SignOptions)
[10]: https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature
[11]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature.options.sign/BarcodeSignOptions
[12]: https://apireference.groupdocs.com/signature/java/com.groupdocs.signature/Signature#sign(java.io.OutputStream,%20com.groupdocs.signature.options.sign.SignOptions)
[13]: https://purchase.groupdocs.com/temporary-license
[14]: https://docs.groupdocs.com/signature/java/
[15]: https://github.com/groupdocs-signature
[16]: https://forum.groupdocs.com/
[17]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
[18]: https://blog.groupdocs.com/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/


