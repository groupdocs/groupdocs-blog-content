---
title: 'Introducing a More Optimized and Simplified GroupDocs.Watermark for .NET API'
date: Thu, 17 Oct 2019 04:47:41 +0000
draft: false
url: /2019/10/17/net-api-to-add-search-remove-watermarks-from-documents-in-c/
author: 'Usman Aziz'
summary: ''
tags: ['Document Watermarking', 'GroupDocs.Watermark for .NET Release']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/GroupDocs-Watermark-for-.NET_.png" alt="">}}


It's been quite long since we released the last version of [GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net) API. The reason behind this gap was to introduce a more simplified and optimized watermark manipulation API for the .NET platform. Today, I am excited to announce that the API v2 of _GroupDocs.Watermark for .NET_ has been released as **v19.10** and it is available for [download](https://downloads.groupdocs.com/watermark/net).

## What's new in the latest release?

The major updates have been done at the architecture level of the API to simplify its usage. Furthermore, we have performed major product optimization in the codebase and introduced unified classes to deal with watermarking operations for all the supported document formats. Some key reasons for these updates are listed below:

*   _[Watermarker](https://apireference.groupdocs.com/net/watermark/groupdocs.watermark/watermarker)_ class is introduced as a single entry point to manage watermarks in the document (instead of _Document_ class from previous versions).
*   Adding watermarks has been unified for all supported document formats.
*   The product architecture has been redesigned from scratch in order to simplify the usage of different options to manage the watermarks.
*   Document information and preview generation procedures have been simplified.

## How to migrate?

The legacy API has been moved into _[Legacy](https://apireference.groupdocs.com/watermark/net)_ namespace so you'll have to make a project-wide replacement of namespaces from **GroupDocs.Watermark** to **GroupDocs.Watermark.Legacy** to resolve build issues after upgrading to v19.10. Furthermore, below is a code comparison of how to use the basic features of the API using the old and the latest version.

### **Adding Watermark**  

The following code samples give you a comparison of how to add watermark to the document using old and new API.

#### Old API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "AddWatermarkToDocumentOld.cs" >}}

#### New API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "AddWatermarkToDocumentNew.cs" >}}

### **Searching Watermarks**  

The following code samples show you the comparison of finding watermarks using search criteria.

#### Old API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "SearchWatermarkInDocumentsOld.cs" >}}

#### New API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "SearchWatermarkInDocumentsNew.cs" >}}

### **Removing Watermarks**  

The following code samples demonstrate the comparison of removing all possible watermarks.

#### Old API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "RemoveWatermarkFromDocumentOld.cs" >}}

#### New API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "RemoveWatermarkFromDocumentNew.cs" >}}

### **Getting Document Info**  

The following code samples show how to get document information from the local file.

#### Old API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "GetDocumentInfoOld.cs" >}}

#### New API

{{< gist GroupDocsGists 50d5bd1274a6564091e4e1ee221526be "GetDocumentInfoNew.cs" >}}

For more details, please have a look at the [migration notes](https://docs.groupdocs.com/display/watermarknet/Migration+Notes). Visit the [release notes](https://docs.groupdocs.com/display/watermarknet/GroupDocs.Watermark+for+.NET+19.10+Release+Notes) of v19.10 to see all the changes in the public API. You can download or clone the [examples](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-.NET) project from GitHub to evaluate each feature of the API. In case you would have any question or querie, you can raise it via our [forum](https://forum.groupdocs.com/c/watermark).





