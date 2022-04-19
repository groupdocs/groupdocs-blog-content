---
title: "在 C# 中搜索 Word、Excel、PowerPoint、PDF 文档中的图像签名"
date: Mon, 06 Apr 2020 02:26:52 +0000
draft: false
url: /zh/2020/04/06/search-image-signatures-in-word-excel-ppt-pdf-using-csharp/
aliases:
- /2020/04/06/search-image-signatures-in-word-excel-ppt-pdf-documents/
author: 'Shoaib Khan'
summary: "**电子签名**是附加到电子传输文件的数字数据。 它验证发件人签署文件的意图。"
tags: ['Search Barcode in CSharp', 'Search Electronic Signature in CSharp', 'Search QR code in CSharp', 'Search Signatures in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

**电子签名**是附加到电子传输文件的数字数据。它验证发件人签署文件的意图。



{{< figure align=center src="images/groupdocs-signature-net-90x90-no-border.png" alt=".NET 的 GroupDocs.Signature。在文档中搜索图像签名">}}


作为开发人员，您可以以编程方式对文档进行签名，还可以验证文档是否使用正确的签名正确签名。 [**GroupDocs.Signature for .NET**][1] API 提供了许多此类功能，让您可以完全控制电子签名过程。它提供了不同的电子签名实现，例如：

* 文字签名（文字、注释、水印、贴纸）
* 图像签名 - 带有图像效果和旋转等选项。
* 数字签名 - 基于数字证书。
* 条码签名
* 二维码签名
* 盖章签名
* 元数据签名
* 表单域签名

本文展示了开发人员如何使用适用于 .NET 的 GroupDocs.Signature API 在任何使用 C# 的文档中搜索各种类型的电子签名。

## 在 C# 中搜索二维码签名

以下是显示如何在 PDF 文档中搜索二维码签名的最简单搜索方法。您可以使用同一行代码在任何受支持的文件格式中进行搜索。

```
// Search QR Code Signatures in PDF document using C#
using (Signature signature = new Signature("signed.pdf"))
{
    // search for signatures in document
    List<QrCodeSignature> signatures = signature.Search<QrCodeSignature>(SignatureType.QrCode);
 
    Console.WriteLine($"\\nSource document contains following signatures.");
    foreach (var qrCodeSignature in signatures)
    {
        Console.WriteLine($"QRCode signature found at page {qrCodeSignature.PageNumber} with type {qrCodeSignature.EncodeType.TypeName} and text {qrCodeSignature.Text}");
    }
}
```

## 在 C# 中搜索条形码、二维码和其他签名

在文档中查找条形码签名、二维码签名、文本签名甚至隐藏的元数据签名都非常简单。下面提到的代码显示了如何从 C# 中的任何文档中提取不同的签名类型。

```
using (Signature signature = new Signature("signed.pdf"))
{
    // search for signatures in document
    SearchResult result = signature.Search(SignatureType.Text, SignatureType.Barcode, SignatureType.QrCode, SignatureType.Metadata);
    if (result.Signatures.Count > 0)
    {
        Console.WriteLine($"\\nSource document contains following signatures.");
        foreach (var resSignature in result.Signatures)
        {
            Console.WriteLine($"Signature found at page {resSignature.PageNumber} with type {resSignature.SignatureType} and Id#: {resSignature.SignatureId}");
        }
    }
    else
    {
        Console.WriteLine("No signature was found.");
    }                
}
```

## 在 PDF 中搜索图像签名并在 C# 中抓取内容

.NET 签名 API 不仅允许获取各种类型的所有签名，还可以获取演示文稿、电子表格、文字处理和 PDF 文档的图像数据内容。以下是显示如何在 C# 中从 PDF 文档中成功搜索图像签名后获取图像内容的源代码。

```
using (Signature signature = new Signature("signed.pdf"))
{
    // setup search options
    ImageSearchOptions searchOptions = new ImageSearchOptions()
    {
        // enable grabbing image content feature
        ReturnContent = true,
        // set minimum size if needed
        MinContentSize = 0,
        // set maximum size if needed
        MaxContentSize = 0,                    
        // specify exact image type to be returned
        ReturnContentType = FileType.JPEG,                                   
    };
    // search document
    List<ImageSignature> signatures = signature.Search<ImageSignature>(searchOptions);
    Console.WriteLine($"\\nSource document contains following image signature(s).");
    // output signatures
    foreach (ImageSignature imageSignature in signatures)
    {
        Console.Write($"Found Image signature at page {imageSignature.PageNumber} and size {imageSignature.Size}.");
        Console.WriteLine($"Location at {imageSignature.Left}-{imageSignature.Top}. Size is {imageSignature.Width}x{imageSignature.Height}.");
    }
    //Save signature images
    string outputPath = "Output";
    if (!Directory.Exists(outputPath))
    {
        Directory.CreateDirectory(outputPath);
    }
    foreach (ImageSignature imageSignature in signatures)
    {
        Console.Write($"Found Image signature at page {imageSignature.PageNumber} and size {imageSignature.Size}.");
        Console.WriteLine($"Location at {imageSignature.Left}-{imageSignature.Top}. Size is {imageSignature.Width}x{imageSignature.Height}.");
        string outputFilePath = System.IO.Path.Combine(outputPath, $"image{i}{imageSignature.Format.Extension}");
        using (FileStream fs = new FileStream(outputFilePath, FileMode.Create))
        {
            fs.Write(imageSignature.Content, 0, imageSignature.Content.Length);
        }
    }
}
```

## GroupDocs.Signature for .NET 的关键资源

探索有关 .NET API 的 GroupDocs.Signaure 的更多信息。如果您需要任何帮助，您可以自由联系支持人员：

* [文档][2]
* [源代码示例][3] - GitHub
* [论坛][4]







[1]: https://products.groupdocs.com/signature/net
[2]: https://docs.groupdocs.com/display/signaturenet/Home
[3]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET
[4]: https://forum.groupdocs.com/c/signature


