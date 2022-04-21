---
title: 'Introducing Z-Order for Text Signatures in GroupDocs.Signature for .NET 19.9'
date: Wed, 09 Oct 2019 11:24:53 +0000
draft: false
url: /2019/10/09/introducing-z-order-for-text-signatures-in-groupdocs.signature-for-.net-19.9/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Signature for .NET Releases', 'GroupDocs.Signature Product Family']
---



{{< figure align=center src="images/groupdocs-signature-net.png" alt="">}}


We are back with another monthly release of our **eSign API** - [**GroupDocs.Signature for .NET**](https://products.groupdocs.com/signature/net). This release includes three new features, three improvements, and a bug fix. So in this article, I'll give you a walk-through of the latest release.

## Support of Z-Order for Text Signatures

Z-order determines the order for the overlapping, two-dimensional objects in an x-y plane. Put it simply, if X-axis represents the width and Y-axis represents the height then Z-order will represent the depth of the object. An object with a higher Z-order value will appear in front of all the other overlapping objects. This option has now been added to our eSignature API for the text signatures. For now, this property is supported for the following document formats:

*   PDF documents
*   Word processing documents
*   Spreadsheets

We have added the [ZOrder](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsignoptions/properties/zorder) property in the [TextSignOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsignoptions) class and this property is responsible for ordering the overlapping text signatures. Let's understand the usage of this property with the help of a code sample.

{{< gist GroupDocsGists 52d64011519d40a6126d55437c49490d "TextSignatureWithZOrder.cs" >}}

## Improvements

The following is the list of improvements we have made in v19.9.

*   Improved the feature of saving signed .djvu files
*   Improved saving word processing documents to various formats
*   Implemented the transparent background for stamps

## Bug Fix

In the previous versions, the [Signature](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/digitalsignoptions/properties/signature) property of [DigitalSignOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/digitalsignoptions) class was not affecting the signing process. An exception was thrown if [CertificateStream](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/digitalsignoptions/properties/certificatestream) or [CertificateFilePath](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/digitalsignoptions/properties/certificatefilepath) is not set. This issue has now been resolved and its fix is available in v19.9.

You can download the latest release from our [downloads](https://downloads.groupdocs.com/signature/net) section or install it in your project using [NuGet](https://www.nuget.org/packages/GroupDocs.Signature). For more details, consult the product [documentation](https://docs.groupdocs.com/display/signaturenet/Introducing+GroupDocs.Signature+for+.NET). Let us know your suggestions or concerns via our [forum](https://forum.groupdocs.com/c/signature).




