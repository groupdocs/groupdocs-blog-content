---
title: "在 Java 中生成 QR 码以签署文档和图像"
date: Fri, 19 Feb 2021 11:45:00 +0000
draft: false
url: /zh/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
aliases:
- /2020/11/17/esign-documents-and-images-with-qr-code-in-java/
author: 'Shoaib Khan'
summary: "**QR code** (**Q**uick **R**esponse code) is the type of 2D Barcodes or matrix barcode. It is the machine-readable label that contains information about the attached item. This article will guide you about programmatically adding QR codes to electronically sign your documents and images using Java."
tags: ['Add QR Code in Java', 'Attach QR Code with Images in Java', 'generate QR Code in Java', 'QR codes in Java', 'Sign docs with QR code in Java', 'Sign Images with QR code in Java']
categories: ['GroupDocs.Signature Product Family']
---

**QR 码**（**Q**uick **R**响应码）是二维条码或矩阵条码的类型。它是机器可读的标签，包含有关附加项目的信息。本文将指导您以编程方式在 Java 中生成 QR 码以对您的文档和图像进行电子签名。



{{< figure align=center src="images/add-qr-code-to-docs-and-images-using-java.png" alt="将二维码添加到 Java 中的文档和图像">}}


以下是涵盖主题的快速链接：

* [二维码生成Java API][2]
* [用Java生成二维码并添加到文档][3]
* [用Java生成并添加二维码到JPG、PNG或WebP图像][4]

## 用于生成 QR 码的 Java API {#java-api-for-qr-codes}



{{< figure align=center src="images/groupdocs-signature-java.png" alt="GroupDocs.Signature for Java">}}


在本文中，我使用 [GroupDocs.Signature for Java][5] API 生成 QR 码并将其附加到 PDF 文件、Word 文档、电子表格、演示文稿和图像中。此 API 支持多种文件格式的不同类型的电子签名。在二维码类型中，API 支持如下：

* 阿兹特克代码
* 数据矩阵码
* GS1 数据矩阵
* GS1 二维码
* 二维码

### 下载并配置

您可以从 [downloads][6] 部分获取 JAR 文件，或者在继续示例之前在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置。有关详细信息，您可以访问 [API 参考][7]。

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
        <version>21.2</version> 
</dependency>
```

## 用 Java 生成二维码 - 添加到 PDF、Word、Excel、PPT {#add-qr-code-to-documents-in-java}

**Signature** 和 **QrCodeSignOptions** 类可以快速创建不同类型的二维码并将其添加到 Java 文档和图像中。

1. 使用源文档创建 **Signature** 类对象。
2. 使用 **QrCodeSignOptions** 类设置 QR 码属性。
3. 最重要的是，从二维码类型中选择合适的。
4. 使用 Signature 对象调用 **sign** 方法，传递生成的文档路径和 QR 码选项。

以下 Java 代码将生成二维码并将其附加到提供的 PDF 文档中。

\[gist id="4c70c60f1f5bdfce19da18f8b9f6ca11" 文件="SignDocsWithQRCode.java"\]

生成的 PDF 文件显示在此处，其中包含使用上述代码添加的 QR 代码。同样，您可以提供任何 Word 文档、电子表格、演示文稿或任何其他 [支持的文档格式][8] 来附加二维码。



{{< figure align=center src="images/Added-QR-Code-in-PDF-using-GroupDocs.Signature-APIs.png" alt="使用 Signature API 添加到 PDF 的 QR 码" caption="使用 GroupDocs.Signature for Java API 添加二维码的 PDF 文件">}}


## 在 Java 中生成 QR 码 - 添加到 JPG、PNG 或 WebP 图像 {#add-qr-code-to-images-in-java}



{{< figure align=center src="images/image-with-qr-code.png" alt="带有二维码的图片">}}


现在，您可能会认为将 QR 码添加到图像中会有不同的策略。答案是不。您可以使用上述相同的代码生成二维码并将其添加到图像中。该 API 允许您将二维码添加到 JPG/JPEG、PNG、WebP、BMP、GIF、SVG、CMX 和 TIFF 图像。

您还可以更改 QR 码的外观，例如背景颜色、前景色、透明度等。在这里，我将黑色背景颜色和前景色设置为白色。

\[gist id="31c41589bda73b4310db679300628cb2" 文件="ChangeQRCodeAppearance.java"\]

## 结论

现在，您应该有足够的信心在 Java 应用程序中生成 QR 码，以便使用 GroupDocs.Signature 对文档和图像进行电子签名。要消除 [文档][9] 上的任何歧义或任何未解决的情况，请随时联系 [论坛][10] 上的**支持团队**。 [GitHub][11] 上还提供了许多其他示例。

## 也可以看看

* [在 C# 中为文档和图像生成二维码][12]






[1]: https://products.groupdocs.com/signature/java
[2]: #java-api-for-qr-codes
[3]: #add-qr-code-to-documents-in-java
[4]: #add-qr-code-to-images-in-java
[5]: https://products.groupdocs.com/signature/java
[6]: https://downloads.groupdocs.com/signature/java
[7]: https://apireference.groupdocs.com/signature/java
[8]: https://docs.groupdocs.com/signature/java/supported-document-formats/
[9]: https://docs.groupdocs.com/signature/java/
[10]: https://forum.groupdocs.com/c/signature
[11]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java
[12]: https://blog.groupdocs.com/2020/11/18/sign-documents-and-images-with-qr-code-in-csharp/


