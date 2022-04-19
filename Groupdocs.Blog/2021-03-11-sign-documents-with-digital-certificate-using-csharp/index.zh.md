---
title: "使用 C# 使用数字证书签署文档"
date: Thu, 11 Mar 2021 07:36:00 +0000
draft: false
url: /zh/2021/03/11/sign-documents-with-digital-certificate-using-csharp/
author: 'Shoaib Khan'
summary: "**数字签名**是用于验证文件真实性的可靠方案。数字签名通常用于实现电子签名。在本文中，您将学习如何使用 C# 使用数字证书对 PDF 和 Word 文档进行电子签名。"
tags: ['Digital Certificate in CSharp', 'Digital Signature in CSharp', 'Sign PDF in CSharp', 'Sign with Digital Certificate in CSharp', 'Sign Word in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

**数字签名**是用于验证文件真实性的可靠方案。数字签名通常用于实现电子签名。在本文中，您将学习如何使用 C# 使用数字证书对 PDF 和 Word 文档进行电子签名。

## 用于数字签名和证书的 .NET API

对于使用数字证书签署文档，我将在本文的 C# 示例中使用 [GroupDocs.Signature for .NET][2] API。除了签署 PDF 文档外，此 API 还支持文字处理文档和电子表格格式的数字签名。

从 [下载部分][3] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][4] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Signature
```

## 在 C# 中使用数字证书签署 PDF

设置好环境后，您离成功签署文件只需几行代码。按照以下步骤使用 C# 使用可用的数字证书对文档进行签名。

* 使用要签名的文档初始化 [Signature][5] 对象。
* 使用证书文件初始化 [DigitalSignOptions][6] 对象。
* 设置所需的签名选项，例如密码和位置。
* 调用[Sign][7]方法用数字证书对文档进行签名。

以下代码示例使用 C# 中的证书对 PDF 文档进行签名。

```
// 在 C# 中使用数字证书签署 PDF
using (Signature signature = new Signature("document.pdf"))
{
    DigitalSignOptions options = new DigitalSignOptions("certificate.pfx");
    {
        ImageFilePath = "sampleImage.jpg", // Optional - Set image file path
        Left = 50,                    // Set signature position
        Top = 50,
        Password = "GroupDocs"       // Set Password
    };
    signature.Sign("signedDocument.pdf", options);
}
```

## 使用 C# 中的自定义外观使用数字签名进行签名

可以自定义数字签名以具有不同的表示形式。对于个性化的外观，可以使用 [PdfDigitalSignatureAppearance][8] 类自定义以下选项。

* 背景
* 联系方式
* 签署日期
* 数字签名
* 地点
* 原因
* 字体系列
* 字体大小

此外，您可以更改以下属性：

* 高度
* 宽度
* 边框样式
* 显示在 **All Pages** 或 **Not**



{{< figure align=center src="images/programmatically-sign-pdf-with-digital-certificate.jpg" alt="使用数字证书签署 PDF" caption="<em>在 C# 中使用 GroupDocs.Signature for .NET 签署带有数字证书的 PDF 文档</em>">}}


在以下示例中，我使用了几乎所有上述属性。此示例使用 C# 自定义 PDF 文档中数字签名的外观。

```
// 在 C# 中使用具有自定义外观和设置的数字证书签署 PDF
using (Signature signature = new Signature("document.pdf"))
{
    DigitalSignOptions options = new DigitalSignOptions("certificate.pfx")
    {
        Password = "GroupDocs",
        // digital certificate details
        Reason = "Approved",
        Location = "New York",

        // Custom PDF signature appearance
        Appearance = new PdfDigitalSignatureAppearance()
        {
            // Do not show contact details
            ContactInfoLabel = string.Empty,
            // Simplify Reason Label
            ReasonLabel = "?",
            // Change Location Label
            LocationLabel = "From",
            DigitalSignedLabel = "By",
            DateSignedAtLabel = "On",
            Background = Color.Red
        },
        AllPages = true,
        Width = 160,
        Height = 80,
        // Set signature border
        Border = new Border()
        {
            Visible = true,
            Color = Color.Red,
            DashStyle = DashStyle.DashDot,
            Weight = 2
        }
    };
    SignResult signResult = signature.Sign("signedDocument.pdf", options);
}
```

## 在 C# 中使用数字证书签署 Word 文档

同样，您可以使用证书签署 Word 文档。当您开始初始化 Signature 对象时，只需提供正确的文档。

* 使用要签名的 Word 文档初始化 [Signature][9] 对象。
* 使用证书文件初始化 [DigitalSignOptions][10] 对象。
* 设置签名选项，例如密码和位置。
* 使用 [Sign][11] 方法使用数字证书对文档进行签名。

该示例使用 C# 中的证书对 Word 文档进行签名。

```
// 在 C# 中使用数字证书签署 Word 文档
using (Signature signature = new Signature("document.docx"))
{
    DigitalSignOptions options = new DigitalSignOptions("certificate.pfx");
    {
        ImageFilePath = "sampleImage.jpg", // Optional - Set image file path
        Left = 50,                    // Set signature position
        Top = 50,
        Password = "GroupDocs"       // Set Password
    };
    signature.Sign("signedDocument.docx", options);
}
```

## 结论

在本文中，您学习了使用 C# 使用数字证书对 PDF 和 Word 文档进行电子签名。此外，您可以轻松自定义签名的外观。现在，您可以尝试构建自己的 .NET 应用程序，以使用具有 C# 自定义外观的数字证书对 PDF 和 Word 文档进行签名。

## 有关 Signature API 的更多信息的快速链接

* [GitHub][12] 上的示例
* [开发者指南和文档][13]
* [论坛][14] 快速支持

## 也可以看看

* [使用 C# 验证文档中的数字签名][15]
* [使用 Java 验证文档中的数字签名][16]







[1]: https://blog.groupdocs.com/2021/03/11/sign-documents-with-digital-certificate-using-csharp/
[2]: https://products.groupdocs.com/signature/net
[3]: https://downloads.groupdocs.com/signature/net
[4]: https://www.nuget.org/packages/groupdocs.signature
[5]: https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature
[6]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/digitalsignoptions
[7]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign/index
[8]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options.appearances/pdfdigitalsignatureappearance
[9]: https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature
[10]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/digitalsignoptions
[11]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign/index
[12]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET
[13]: https://docs.groupdocs.com/signature/net
[14]: https://forum.groupdocs.com/c/signature
[15]: https://blog.groupdocs.com/2019/09/25/verify-digital-signature-in-documents-using-csharp/
[16]: https://blog.groupdocs.com/2020/10/06/verify-digital-signature-in-documents-using-java/


