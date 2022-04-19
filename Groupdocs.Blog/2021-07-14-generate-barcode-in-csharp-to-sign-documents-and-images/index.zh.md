---
title: "在 C# 中生成条形码 - 将条形码添加到文档和图像"
date: Wed, 14 Jul 2021 17:25:00 +0000
draft: false
url: /zh/2021/07/14/generate-barcode-in-csharp-to-sign-documents-and-images/
author: 'Shoaib Khan'
summary: 'Barcode is way to present the data in machine readable format. Barcodes are normally used for quick identification of large number of items. In this article, you will learn how to generate barcodes within .NET applications. Futher you will see, how the generated barcodes can be applied to any of your documents and images using C#.

本文涵盖以下主题：

* .NET 的条码生成器 API
* 在 C# 中生成和应用条形码到文档
* 在 C# 中生成和应用条形码到图像'
tags: ['Apply Barcode to Images in C#', 'Apply Barcode to PDF in C#', 'Generate Barcode in C#', 'Sign Documents with Barcode in C#', 'Sign Images with Barcode in C#']
categories: ['GroupDocs.Signature Product Family']
---

条形码是一种以机器可读格式呈现数据的方式。条形码通常用于快速识别大量物品。在本文中，您将了解如何在 .NET 应用程序中生成条形码。此外，您将看到如何使用 C# 将生成的条形码应用于您的任何文档和图像。

以下主题涵盖以下内容：

* [适用于 .NET 的条码生成器 API][1]
* [在 C# 中生成和应用条码到文档][2]
* [在 C# 中生成和应用条形码到图像][3]

## 用于生成条形码的 .NET API {#barcode-generator-dotnet-api}

[GroupDocs.Signature][4] 具有 .NET API，允许您对文档、图像或不同文件格式的文件进行签名。使用此 API，您可以轻松应用不同类型的签名，如 QR 码、条形码、文本、图像、元数据、数字签名、印章、电子签名。此外，您可以通过多种方式自定义签名的外观。

您可以从 [下载部分][5] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][6] 为您的 .NET 应用程序安装 API。您也可以使用包管理器中的以下命令。

```
PM> Install-Package GroupDocs.Signature
```

## 使用 C# 的文档和图像的条形码 {#generate-barcode-in-csharp}

可以使用自定义文本、外观和不同编码类型以编程方式生成条形码。一些受支持的条形码类型包括 Code 32、Code 128、DotCode、GS1、ISBN、PDF417、Pharmacode、Postnet、UPCA 等等。这些条码可以应用于大量[支持的文档和图像格式][7]。

以下是在任何文档或图像上应用条形码的主要步骤。

* 加载文档或图像。
* 生成条形码以及文本、外观、编码和其他属性。
* 将其应用于加载的文件。



{{< figure align=center src="images/Generate-Barcode-using-GroupDocs.jpg" alt="在 C# 中生成条形码">}}


## 在 C# 中生成条形码并应用于文档 {#apply-barcode-to-documents}

以下是生成条形码并将其应用于任何文档的步骤。无论目标文档是 MS Word 文档、PDF 文件、Excel 电子表格还是演示文稿，添加条形码的步骤对于所有不同格式都是相同的。

* 使用 [Signature][8] 类加载文档（PDF、Word Doc、Spreadsheet、PPT...）。
* 使用 [BarcodeSignOptions][9] 类设置条形码选项。
* 设置条码属性，如编码类型、位置、大小等。
* 调用[Sign][10]方法应用条码并对加载的文档进行签名。

以下源代码使用 C# 生成条形码并将其附加到 PDF 文档。

```
// 生成条形码并将其应用于文档（DOC、DOCX、PDF、PPT、XLS、XLSX、...）
using (Signature signature = new Signature("path/document.pdf"))
{
    // Create barcode options with the barcode text
    BarcodeSignOptions options = new BarcodeSignOptions("Signed by GroupDocs using GroupDocs.Signature.")
    {
        // Set the Barcode Encoding Ttype
        EncodeType = BarcodeTypes.Code128,

        // Set Signature Position
        Left = 205,
        Top = 170,
        Width = 200,
        Height = 50
    };
    // Apply Barcode on document to Sign.
    SignResult result = signature.Sign("path/document-with-barcode.pdf", options);
}
```

## 在 C# 中生成条形码并应用于图像 {#apply-barcode-to-images}

同样，在图像上应用条形码的方式也没有什么不同。只需加载正确的图像，其余步骤和代码将与将条形码应用于上述文档的相同。

以下是生成条形码并将其应用于任何图像的步骤。

* 使用 [Signature][11] 加载图像 (JPG, PNG, WebP, ...)。
* 使用 [BarcodeSignOptions][12] 准备条形码选项。
* 通过设置文本、编码类型、位置、大小、外观等自定义条码。
* 使用 [Sign][13] 方法应用条形码对图像进行签名。

以下源代码使用 C# 生成条形码并将其附加到 JPG 图像。

```
// 生成条形码并将其应用于图像（JPG、PNG、BMP...）
using (Signature signature = new Signature("path/image.jpg"))
{
    // Create barcode options with the barcode text
    BarcodeSignOptions options = new BarcodeSignOptions("Signed by GroupDocs using GroupDocs.Signature.")
    {
        // Set the Barcode Encoding Ttype
        EncodeType = BarcodeTypes.Code128,

        // Set Signature Position
        Left = 20,
        Top = 150,
        Width = 160,
        Height = 30
    };
    // Apply Barcode on document to Sign.
    SignResult result = signature.Sign("path/document-with-barcode.jpg", options);
}
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][14] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您学习了如何在 C# 中生成条形码。此外，您还了解了如何将这些生成的条形码添加到您的图像和文档中。现在您可以开发自己的条形码生成器 .NET 应用程序。

您可以使用 [文档][15] 或通过 [GitHub][16] 上提供的示例了解有关 .NET 签名 API 的更多信息。在 [论坛][17] 上与我们联系。

## 也可以看看

* [在C#中生成二维码并应用于文档和图像作为签名][18]
* [在 Java 中生成和应用二维码在图像和文档上][19]







[1]: #barcode-generator-dotnet-api
[2]: #apply-barcode-to-documents
[3]: #apply-barcode-to-images
[4]: https://products.groupdocs.com/signature/
[5]: https://downloads.groupdocs.com/signature
[6]: https://www.nuget.org/packages/groupdocs.signature
[7]: https://docs.groupdocs.com/signature/net/supported-document-formats/
[8]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature
[9]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/barcodesignoptions
[10]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign
[11]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature
[12]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/barcodesignoptions
[13]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://docs.groupdocs.com/signature/net/
[16]: https://github.com/groupdocs-signature
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/
[19]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/


