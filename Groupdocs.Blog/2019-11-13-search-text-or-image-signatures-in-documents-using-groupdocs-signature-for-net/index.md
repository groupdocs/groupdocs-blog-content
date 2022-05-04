---
title: 'Search Text or Image Signatures in Documents using GroupDocs.Signature for .NET 19.10'
date: Wed, 13 Nov 2019 07:33:44 +0000
draft: false
url: /2019/11/13/search-text-or-image-signatures-in-documents-using-groupdocs-signature-for-net/
author: 'Usman Aziz'
summary: ''
tags: ['API', 'dotnet', 'electronic signature', 'GroupDocs.Signature for .NET']
categories: ['GroupDocs.Signature Product Family']
---



{{< figure align=center src="images/groupdocs-signature-net.png" alt="C# .NET Digital Signature API">}}


With the release of version **19.10** of our **electronic signature API** - [**GroupDocs.Signature for .NET**](https://products.groupdocs.com/signature/net), we have introduced the features of searching text signatures and image signatures in the supported document formats. Not only this, the API now supports [**.NET Standard 2.0**](https://docs.microsoft.com/en-us/dotnet/standard/net-standard) which makes it compatible with any .NET implementation that targets .NET Standard specifications. So let's have a brief overview of what is new, improved or fixed in the latest release.

## Searching Text or Image Signatures

Text and image signatures are among the popular types of signatures for digital documents. GroupDocs.Signature supports adding text and image signatures in the supported document formats. However, there could be the case when you need to scan a document to search if a document is signed with a particular text or image. The manual inspection of the whole document or a bunch of documents is not an efficient way. To deal with such a case, we have introduced the feature of searching text or image signatures.

### **Searching Text Signature**

GroupDocs.Signature for .NET provides various options in [TextSearchOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsearchoptions) class for searching the text signatures including:

*   [Text](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsearchoptions/properties/text) - The signature text to match on searching.
*   [AllPages](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/searchoptions/properties/allpages) - Flag to search on each page of the document.
*   [MatchType](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsearchoptions/properties/matchtype) - Specifies the match types such as exact match, contains, starts with and ends with.
*   [PageNumber](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/searchoptions/properties/pagenumber) - For searching on a specific page.
*   [PagesSetup](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/searchoptions/properties/pagessetup) - To specify if you want to search on even/odd pages, first/last page or on the arbitrary page numbers.

The following code sample shows how to search a text signature in a document.

{{< gist GroupDocsGists 4c2db27e6a13326c84fd18d33be62e80 "SearchTextSignatureInDocuments.cs" >}}

### **Searching Image Signature**

For searching image signatures, the API provides [ImageSeachOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/imagesearchoptions) class which contains the following options:

*   [AllPages](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/searchoptions/properties/allpages) - Flag to search on each page of the document.
*   [PageNumber](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/searchoptions/properties/pagenumber) - For searching on a specific page.
*   [PagesSetup](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/searchoptions/properties/pagessetup) - To specify if you want to search on even/odd pages, first/last page or on the arbitrary page numbers.

The following code sample shows how to search the image signature in a document.

{{< gist GroupDocsGists 4c2db27e6a13326c84fd18d33be62e80 "SearchImageSignatureInDocuments.cs" >}}

For more details on the search feature, please visit [this](https://docs.groupdocs.com/display/signaturenet/Searching) documentation section.

## Support of .NET Standard 2.0

We received a number of requests from our customers for the support of [.NET Core](https://en.wikipedia.org/wiki/.NET_Core). Therefore, we have added the support of .NET Standard 2.0 in our latest release. Now, you can use the API in .NET Framework as well as in .NET Core for the cross-platform development.

## Bug Fix

The memory leaks were found in the previous versions of the API while previewing the documents. This issue has now been fixed in v19.10.

You can [download](https://downloads.groupdocs.com/signature/net) the latest version of the API to avail the above-mentioned features and fix. For running code samples, download or clone the examples project from the GitHub [repository](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET). You can also get in touch with us via our [forum](https://forum.groupdocs.com/c/signature).





