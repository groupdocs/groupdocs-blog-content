---
title: 'Lock Watermarks in Word Documents using C#'
date: Fri, 01 Nov 2019 13:51:07 +0000
draft: false
url: /2019/11/01/lock-watermarks-in-word-documents-programmatically-using-csharp/
author: 'Usman Aziz'
summary: ''
tags: ['API', 'Document Watermarking', 'dotnet', 'GroupDocs.Watermark for .NET']
categories: ['GroupDocs.Watermark Product Family']
---

Watermarking is a famous way of adding labels to the documents that may indicate the state of the document such as draft, confidential, etc. It can be used to add a company's logo behind the text of the document to avoid the ownership dispute. In some cases, people add watermarks to the documents to protect the content. But, are you sure that the content is protected and no one can remove those watermarks? There is no guarantee because various third-party tools are available that can wipe out the watermarks from the documents.

In such scenarios, you need some way to lock the watermarks to restrict the editing. In this article, I'll show you how to **protect** your **Word** documents and prevent the editing of the watermarks programmatically in **C#** using **[GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net)** API.

## Locking Watermark in Word Document

GroupDocs.Watermark provides [**5** variants](https://apireference.groupdocs.com/net/watermark/groupdocs.watermark.options.wordprocessing/wordprocessinglocktype) of locking Word document when adding watermark.

### **Allowing Revisions Only**

In this case, the user will only be able to add revision marks to the Word document. The content of the document as well as the watermark will be read-only.

### **Allowing Comments Only**

If this type of restriction is applied then the user will only be able to modify the comments in the document.

### **Allowing Form Fields Only**

With this option, the document is split into one-page sections and a locked section with the watermark is added between each two adjacent document sections.

### **Read Only with Editable Content**

In this case, the document is marked as read-only but all the content except the watermark is marked as editable.

### **Completely Read Only**

In this case, the entire document is marked as read-only and nothing can be edited.

## Source Code

The following code sample shows how to impose the above-mentioned restrictions on a Word document when adding the watermark.

{{< gist GroupDocsGists e04a73ccf29f6bab61c59ffa5a8daeca "LockWatermarkInWordDocument.cs" >}}

Have any questions or queries? Do contact us on our [forum](https://forum.groupdocs.com/c/watermark).





