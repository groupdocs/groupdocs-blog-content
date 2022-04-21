---
title: 'Remove or Delete Pages from Documents in C#'
date: Tue, 29 Oct 2019 08:54:56 +0000
draft: false
url: /2019/10/29/delete-pages-from-documents-in-csharp/
aliases:
    - /2019/10/29/delete-one-or-more-pages-from-a-document-in-c/
author: 'Atir Tahir'
summary: ''
tags: ['delete pages', 'delete pages in csharp', 'remove pages', 'remove pages in csharp']
categories: ['GroupDocs.Merger Product Family']
---

We'll see how to remove a single page or a collection of specific page numbers from the source document in C# using [GroupDocs.Merger for .NET](https://products.groupdocs.com/merger/net). This is a back-end API that can be integrated into any new or existing .NET application without any dependency.

## **Does it require any software installation?**

Absolutely not. It doesn't matter if MS Office or any PDF reader is installed on your computer. Using a single GroupDocs.Merger for .NET [DLL](https://downloads.groupdocs.com/merger/net) you can develop a web, console, or desktop application to delete the pages.

## **Remove Selected Page from PDF using C#**

Below are the steps to remove the document page(s) from a PDF document with C# code. Just by changing the document name and extension, we can perform the same operation for the [supported document formats](https://docs.groupdocs.com/merger/net/supported-document-formats/).

*   Initialize RemoveOptions class with page numbers to remove.
*   Instantiate Merger object with source document path or stream.
*   Call RemovePages method and pass RemoveOptions object to it.
*   Call Save method and pass desired file path to save the resultant document.

{{< gist GroupDocsGists f1bb9b5f075b0ffa76183b96a7799c91 "removepages.cs" >}}

Explore API [documentation](https://docs.groupdocs.com/merger/net/) to learn more about the supported features. You can download or clone [this](https://github.com/groupdocs-merger/GroupDocs.Merger-for-.NET) open-source example project for API evaluation. If you face any issue, post it on the [forum](https://forum.groupdocs.com/c/merger).




