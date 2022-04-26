---
title: 'Verify Digital Signature in Documents using C#'
date: Wed, 25 Sep 2019 16:37:11 +0000
draft: false
url: /2019/09/25/verify-digital-signature-in-documents-using-csharp/
aliases:
    - /2019/09/25/verify-digital-signature-in-documents-using-c/
author: 'Usman Aziz'
summary: ''
tags: ['c# electronic signature']
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

**Digital Signatures** in documents look similar to the paper-based signatures, however, being certificate-based **electronic signatures** they contain the identity of the signer in encrypted form. The certificates are issued by trusted and authorized Certificate Authorities. These authorities identify the person the certificates are issued to. This is why the digitally signed documents can be verified at any time. In this article, I'll show you how to programmatically verify the digital signature in **PDF**, **Word**, and **Excel**, **documents** by using [**GroupDocs.Signature for .NET**](https://products.groupdocs.com/signature/net) **API** with **C#**.

## Steps to verify digitally signed PDF document

For demonstration, I am using a PDF document for digital signature verification. However, the same code will work for MS Word and Excel document formats.

**1.** Download _[GroupDocs.Signature for .NET](https://downloads.groupdocs.com/signature/net)_ or install it using [NuGet](https://www.nuget.org/packages/GroupDocs.Signature/).

**2.** Add the following namespaces in your code.

{{< gist GroupDocsGists 4b6047f897d21ce8d268f4b7972a8ad6 "DigitalSignatureNamespaces.cs" >}}

**3.** Load digitally signed PDF document using an instance of [_Signature_](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature) class.

{{< gist GroupDocsGists 4b6047f897d21ce8d268f4b7972a8ad6 "LoadDigitallySignedPDF.cs" >}}

**4.** Instantiate the _[DigitalVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/digitalverifyoptions)_ object and specify verification options.

{{< gist GroupDocsGists 4b6047f897d21ce8d268f4b7972a8ad6 "DigitalVerifyOptions.cs" >}}

**5.** Call _[Verify](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature/methods/verify)_ method of _Signature _class' instance and pass _DigitalVerifyOptions _to it. 

{{< gist GroupDocsGists 4b6047f897d21ce8d268f4b7972a8ad6 "VerifyDigitalSignature.cs" >}}

**6.** Check verification results from _[VerificationResult](https://apireference.groupdocs.com/net/signature/groupdocs.signature.domain/verificationresult)_ object.

{{< gist GroupDocsGists 4b6047f897d21ce8d268f4b7972a8ad6 "VerificationResult.cs" >}}

**Complete code**

{{< gist GroupDocsGists 4b6047f897d21ce8d268f4b7972a8ad6 "VerifyDigitalSignatureInPDFDocument.cs" >}}

Thus, you can determine whether the digital signature in the PDF document meets the specified criteria or not. Finally, you can mark the document as valid or invalid. Read more about _GroupDocs.Signature for .NET_ API [here](https://docs.groupdocs.com/display/signaturenet/Introducing+GroupDocs.Signature+for+.NET).




