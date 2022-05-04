---
title: "Sign Documents with Digital Certificate using C#"
seoTitle: "Sign Documents with Digital Certificate using C# | Word & PDF"
description: "Electronically sign Word & PDF files with digital certificate in C# using .NET API for electronic signatures. Change the appearance of digital signatures."
date: Thu, 11 Mar 2021 07:36:00 +0000
draft: false
url: /2021/03/11/sign-documents-with-digital-certificate-using-csharp/
author: 'Shoaib Khan'
summary: "The **digital signature** is a trustworthy scheme for verifying the authenticity of your documents. Digital signatures are often used to implement electronic signatures. In this article, you will learn how to electronically sign PDF and Word documents with digital certificates using C#."
tags: ['Digital Certificate in CSharp', 'Digital Signature in CSharp', 'Sign PDF in CSharp', 'Sign with Digital Certificate in CSharp', 'Sign Word in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

The **digital signature** is a trustworthy scheme for verifying the authenticity of your documents. Digital signatures are often used to implement electronic signatures. In this article, you will learn how to electronically sign PDF and Word documents with digital certificates using C#.

## .NET API for Digital Signatures and Certificates

For signing documents with the digital certificate, I will be using [GroupDocs.Signature for .NET][2] API in the C# examples of this article. In addition to the signing of PDF documents, this API supports digital signatures for word-processing documents and spreadsheet formats.

Download the DLLs or MSI installer from the [downloads section][3] or install the API in your .NET application via [NuGet][4].

```
PM> Install-Package GroupDocs.Signature
```

## Sign PDF with Digital Certificate in C#

After setting up the environment, you are few lines away from the successful signing of your documents. Follow the following steps to get your document signed with the available digital certificate using C#.

*   Initialize [Signature][5] object with the document to sign.
*   Initialize [DigitalSignOptions][6] object with the certificate file.
*   Set required sign options such as password, and position.
*   Call [Sign][7] method to sign the document with the digital certificate.

The following code example signs the PDF documents with the certificate in C#.

{{< gist GroupDocsGists ce12fd1c7f9f4c857413b1001586079d "SignWithCertificate.cs" >}}

## Sign with Digital Signature using custom Appearance in C#

The digital signature can be customized to have different presentations. For the personalized appearance, the following options can be customized using the [PdfDigitalSignatureAppearance][8] class.

*   Background
*   Contact Info
*   Date signed at
*   Digital signed
*   Location
*   Reason
*   Font Family
*   Font Size

Further, you can alter following properties:

*   Height
*   Width
*   Border Style
*   Show on **All Pages** or **Not**



{{< figure align=center src="images/programmatically-sign-pdf-with-digital-certificate.jpg" alt="Sign PDF with Digital Certificate" caption="<em>Signed PDF document with digital certificate using GroupDocs.Signature for .NET in C#</em>">}}


In the following example, I am using almost all of the above-mentioned properties. This example customizes the appearance of the digital signature in a PDF document using C#.

{{< gist GroupDocsGists ce12fd1c7f9f4c857413b1001586079d "SignWithCertificateAndAppearance.cs" >}}

## Sign Word Docs with Digital Certificate in C#

Similarly, you can sign Word documents using the certificate. Just provide the right document when you start with initializing the Signature object.

*   Initialize [Signature][9] object with the Word document to sign.
*   Initialize [DigitalSignOptions][10] object with the certificate file.
*   Set sign options such as password, and position.
*   Sign the document with the digital certificate using the [Sign][11] method.

The example signs the Word documents using the certificate in C#.

{{< gist GroupDocsGists ce12fd1c7f9f4c857413b1001586079d "SignWordWithCertificate.cs" >}}

## Conclusion

In this article, you have learned to electronically sign PDF and Word documents with the digital certificate using C#. Further, you can easily customize the appearance of the signature. Now you can try building your own .NET application for signing PDF and Word documents with digital certificates having a custom appearance in C#.

## Quick Links for more about Signature API

*   Examples on [GitHub][12]
*   [Developer Guide and Documentation][13]
*   [Forum][14] for Quick Support

## See Also

*   [Verify Digital Signature in Documents using C#][15]
*   [Verify Digital Signature in Documents using Java][16]







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

