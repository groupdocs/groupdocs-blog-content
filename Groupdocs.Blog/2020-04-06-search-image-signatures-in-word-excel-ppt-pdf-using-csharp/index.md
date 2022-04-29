---
seoTitle: "Search Image Signature in C# in Word, Excel, PowerPoint, PDF"
title: 'Search Image Signatures in Word, Excel, PowerPoint, PDF Documents in C#'
date: Mon, 06 Apr 2020 02:26:52 +0000
draft: false
url: /2020/04/06/search-image-signatures-in-word-excel-ppt-pdf-using-csharp/
aliases:
    - /2020/04/06/search-image-signatures-in-word-excel-ppt-pdf-documents/
author: 'Shoaib Khan'
description: "Search Barcode, QR Code, digital, or electronic signature with image data content from any document (DOC, XLS, PPT, PDF) in C# using .NET Signature API."
summary: "**Electronic Signature** is the digital data that is attached to an electronically transmitted document. It verifies the sender's intention to sign the document."
tags: ['Search Barcode in CSharp', 'Search Electronic Signature in CSharp', 'Search QR code in CSharp', 'Search Signatures in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

**Electronic Signature** is the digital data that is attached to an electronically transmitted document. It verifies the sender's intention to sign the document.



{{< figure align=center src="images/groupdocs-signature-net-90x90-no-border.png" alt="GroupDocs.Signature for .NET. Search Image Signatures in Documents">}}


As a developer, you can programmatically sign documents and also verify if the document is properly signed with the right signature. [**GroupDocs.Signature for .NET**][1] API provides many such features and gives you complete control over the electronic signing process. It provides different electronic signature implementations, like:

*   Text Signatures (text, annotations, watermarks, stickers)
*   Image Signature - with options like image effects and rotation.
*   Digital Signature - based on digital certificates.
*   Barcode Signature
*   QR code Signature
*   Stamp Signature
*   Metadata Signature
*   FormField Signature

This article shows how developers can search electronic signatures of various types within any document with C# using GroupDocs.Signature API for .NET.

## Search QR code signatures in C#

Following is the simplest search method that shows how to search QR Code Signatures within a PDF document. You can use the same line of code to search in any of the supported file formats.

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

## Search barcode, QR code, and other signatures in C#

It is quite simple to find barcode signature, QR Code signature, Text signature, or even the hidden Metadata signature in the document. The below-mentioned code shows how different signature types can be extracted from any document in C#.

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

## Search image signature in PDF and grab content in C#

The .NET Signature API not only allows getting all the signatures of various types, but it also grabs the image data content for presentations, spreadsheets, word processing, and PDF documents. Following is the source code showing how to grab the image content after the successful image signature search from a PDF document in C#.

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

## Key Resources for GroupDocs.Signature for .NET

Explore more about the GroupDocs.Signaure for .NET API. You can freely contact support if you need any help:

*   [Documentation][2]
*   [Source Code Examples][3] - GitHub
*   [Forum][4]







[1]: https://products.groupdocs.com/signature/net
[2]: https://docs.groupdocs.com/display/signaturenet/Home
[3]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET
[4]: https://forum.groupdocs.com/c/signature

