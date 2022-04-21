---
title: 'Introducing a More Optimized and Simplified Electronic Signature API'
date: Fri, 30 Aug 2019 05:56:29 +0000
draft: false
url: /2019/08/30/introducing-a-more-optimized-and-simplified-electronic-signature-api/
author: 'Usman Aziz'
summary: ''
tags: ['digital signature', 'electronic signature', 'esign']
categories: ['GroupDocs.Signature for .NET', 'GroupDocs.Signature Product Family']
---

Why change is considered as a hard but yet good thing to occur? Why the updates are important? This is because if there is no change there is no progress and staying the same over the time makes the things die. The updates in the software components are also similar when a new version of the same software replaces the old one. A software that remains the same and doesn't introduce any improvements or new features becomes obsolete. This is the reason the updates are always welcomed. And today, I am going to tell you about some major updates we have provided for our electronic signature API - [GroupDocs.Signature for .NET](https://products.groupdocs.com/signature/net).

After a having gap of approx. two months, we have now released an improved and more simplified version of API - **v19.8**. The primary objective behind this release was to make the usage of API's features simpler and introduce a unified approach to handle all the supported document formats. The revamping of the architecture and the major optimizations have made the API more efficient in terms of resource consumption, especially memory utilization.

Let's dig it further and check out what are the key reasons to upgrade to the latest release.

*   In the previous versions of the API, we had a separate class to deal with each supported document format. Since it was difficult to work with multiple classes, we have now introduced a unified approach. The signature options, verification options, and search options are now related to signature types only and not the document formats. For example, _PdfSignTextOptions_ and _WordsSignTextOptions_ were used to specify different options for text signatures in PDF and Word Processing document respectively. Now, a single class, [_TextSignOptions_](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsignoptions)  will be used for both the document formats.
*   The single _[Signature](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature)_ class is introduced to sing the document with various signature types and perform verification and search operations for all the supported document formats.  
    
*   The overall document related classes which were used to deal with different document formats have been unified to common classes.  
    
*   The API's architecture is redesigned from scratch in order to simplify the usage of options and classes to manipulate all the signature types.
*   The procedures of getting the document's information and generating the previews for the documents are also simplified.

Let me now show you how these updates have affected and optimized the code. The following is the code sample that signs the PDF document with a text signature using the previous version of the API.

{{< gist GroupDocsGists 4a7557ad2b26d344f2fd97f3f0bd55d8 "SignPDFWithText_Old.cs" >}}

Now, have a look at how you would perform the same operation after upgrading to the latest release.

{{< gist GroupDocsGists 4a7557ad2b26d344f2fd97f3f0bd55d8 "SignPDFWithText_New.cs" >}}

See, the code is more simplified as well as optimized in the new API. Not only this, but it also consumes fewer resources as compared to the previous versions.

So if you are already using GroupDocs.Signature for .NET then it is the right time to upgrade to the latest release. In case you are afraid of the breaking changes that you may face after upgrading to a version with major changes, we have made the things much easier for you. In the latest version, the legacy API has been moved into the **Legacy** namespace. Therefore, after you upgrade to version 19.8, it is required to make project-wide replacement of namespaces only. This means that the namespaces will be changed from **GroupDocs.Signature.\*** to **GroupDocs.Signature.Legacy.\*** to resolve build issues. And that’s it!

Just have a look at our [documentation](https://docs.groupdocs.com/display/signaturenet/Introducing+GroupDocs.Signature+for+.NET) to check out how easy we have made the document signing process. Download or clone the new source code samples from the [GitHub repository](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET) to know about the working of the API.

If you would face any issue while using or upgrading to the latest release, just post it on our [forum](https://forum.groupdocs.com/categories) and we would love to assist you.




