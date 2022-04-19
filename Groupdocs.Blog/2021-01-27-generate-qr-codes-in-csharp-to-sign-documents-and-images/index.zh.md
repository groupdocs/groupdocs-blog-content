---
title: "在 C# 中生成 QR 码以对文档和图像进行签名"
date: Wed, 27 Jan 2021 22:39:00 +0000
draft: false
url: /zh/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/
aliases:
- /2019/09/07/sign-documents-with-qr-code/
- /2019/09/07/sign-documents-with-qr-code-in-csharp-and-java
- /2019/09/07/sign-documents-with-qr-code-in-csharp-and-java/
- /2020/11/18/sign-documents-and-images-with-qr-code-in-csharp/
author: 'Shoaib Khan'
summary: "在本文中，我们将了解**如何使用 C# 以编程方式添加 QR 码以对文档和图像进行电子签名**。 GroupDocs.Signature for .NET 是用于在 PDF 文件、文字处理文档、电子表格、演示文稿和图像中添加二维码的 API。它支持大量支持的文件格式的各种电子签名。二维码中，支持Aztec Code、DataMatrix Code、GS1 DataMatrix、GS1 QR、QR类型。 API 允许我们将二维码添加到 JPG/JPEG、PNG、WebP、BMP、GIF、SVG、CMX 和 TIFF 图像以及更多图像文件格式。"
tags: ['Add QR code in CSharp', 'Attach QR code with Images in CSharp', 'eSign in CSharp', 'generate qr code in csharp', 'Sign documents with QR code in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

二维码近年来越来越受欢迎。作为开发人员，让我们看看**如何在 C# 中以编程方式生成 QR 码** 以对文档和图像进行电子签名。在之前的文章中，我们讨论了[使用 Java 将 QR 码与文档和图像附加][1]。



{{< figure align=center src="images/add-qr-code-to-docs-and-images-using-dotnet.png" alt="在 C# .NET 中生成 QR 码以使用 GroupDocs 对文档和图像进行签名。">}}


本文将转换以下主题：

* [用于生成二维码和签名的.NET API][2]
* [生成二维码 - 用 C# 签署文档][3]
* [生成二维码 - 在 C# 中添加到 JPG、PNG 或 WebP 图像][4]

## 用于 QR 码生成的 .NET API {#dotnet-api-for-qr-codes}



{{< figure align=center src="images/groupdocs-signature-net-90x90-no-border.png" alt=".NET 的 GroupDocs.Signature">}}


在本文中，我将使用 [GroupDocs.Signature for .NET][5] API 来生成二维码。此 API 支持 Aztec Code、DataMatrix Code、GS1 DataMatrix、GS1 QR、QR 类型。它还支持 PDF 文件、文字处理文档、电子表格、演示文稿、图像等 [添加 QR 码的文档文件格式][6]。

对于下面的示例，我建议您从 [NuGet][7] 包管理器安装 API，或者从 [下载][8] 部分获取 MSI 安装程序和 DLL。您也可以在包管理器控制台中使用以下命令。

```
PM> Install-Package GroupDocs.Signature
```

有关详细信息，您可以访问 [API 参考][9]。

## 在 C# 中生成二维码 - 添加到 PDF、Word、Excel、PPT 文件 {#add-qr-code-to-documents-in-csharp}

**Signature** 和 **QrCodeSignOptions** 类有助于在 .NET 应用程序中快速创建不同类型的 QR 码并签署文档和图像。以下步骤展示了如何使用 C# 生成 QR 码，然后将它们附加到 PDF 文档：

1. 使用源文档初始化 **Signature** 类对象。
2. 使用 **QrCodeSignOptions** 类设置 QR 码属性。
3. 最重要的是，从可用的二维码类型中选择合适的。 （阿兹台克、DataMatrix、GS1 DataMatrix、GS1 QR、QR）
4. 调用 **Sign** 方法，传递生成的文档路径和 QR 码选项。

以下 C# 代码实现了上述步骤。同样，您可以提供 Word 文档、电子表格、演示文稿或任何其他 [支持的文档格式][10] 来附加生成的二维码。

```
// 使用 GroupDocs.Signature for .NET API 对 PDF、Excel、PPT、Word 文档和带有 QR 码的图像进行电子签名
using (Signature signature = new Signature("filePath/document.pdf")) // Provide any DOC, PDF, XLS, PPT, PNG, JPG, WebP file.
{
    // Create QR Code option with predefined text
    QrCodeSignOptions options = new QrCodeSignOptions("Signed by GroupDocs")
    {
        EncodeType = QrCodeTypes.QR,
        // Set QR Code position & appearance
        Left = 50,
        Top = 50,
        Width = 90,
        Height = 90
    };
    // Sign document and save file
    SignResult result = signature.Sign("filePath/document-with-qr-code.pdf", options);
}
```

这是带有 QR 码的 PDF 文件，作为上述代码的输出。



{{< figure align=center src="images/Added-QR-Code-in-PDF-using-GroupDocs.Signature-APIs.png" alt="使用 Signature API 将生成的 QR 码添加到 PDF" caption="使用 GroupDocs.Signature for .NET API 添加二维码的 PDF 文件">}}


## 在 C# 中生成 QR 码 - 附加 JPG、PNG 或 WebP 图像 {#add-qr-code-to-images-in-csharp}



{{< figure align=center src="images/image-with-qr-code.png" alt="将生成的二维码添加到 Image。">}}


您也可以使用上述相同的代码将生成的二维码附加到图像中。该 API 允许您将二维码添加到 JPG/JPEG、PNG、WebP、BMP、GIF、SVG、CMX 和 TIFF 图像以及其他一些图像文件格式。

在生成二维码时，您还可以更改背景颜色、前景色、透明度和其他一些属性来改变它们的外观。下面的 C#code 将 QR 码的背景颜色更改为 **black** 并将前景色设置为 **white**。

```
// 在 C# 中更改 QR 码的外观
// 设置背景色、前景色、透明度等。
Background = new Background()
{
    Color = Color.Black,
    Transparency = 0.5
},
//设置文本颜色和字体
ForeColor = Color.White
```

## 结论

我相信，现在您已经熟悉如何在 C# 中创建 QR 码，以便在 .NET 应用程序中对文档和图像进行电子签名。您可以进一步更改适合您品牌的二维码外观。

## 也可以看看

* [生成二维码以在 Java 中签署文档和图像][11]

* [文档][12]
* [免费支持团队][13]
* [GitHub上的示例][14]







[1]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
[2]: #dotnet-api-for-qr-codes
[3]: #add-qr-code-to-documents-in-csharp
[4]: #add-qr-code-to-images-in-csharp
[5]: https://products.groupdocs.com/signature/net
[6]: https://docs.groupdocs.com/signature/net/supported-document-formats/
[7]: https://www.nuget.org/packages/groupdocs.signature
[8]: https://downloads.groupdocs.com/signature/net
[9]: https://apireference.groupdocs.com/signature/net
[10]: https://docs.groupdocs.com/signature/net/supported-document-formats/
[11]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
[12]: https://docs.groupdocs.com/signature/net/
[13]: https://forum.groupdocs.com/c/signature
[14]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET


