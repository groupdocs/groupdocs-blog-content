---
title: 'Introducing more simplified and improved GroupDocs.Merger for .NET'
date: Thu, 03 Oct 2019 12:45:29 +0000
draft: false
url: /2019/10/03/introducing-more-simplified-and-improved-groupdocs.merger-for-.net/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Merger for .NET', 'GroupDocs.Merger Product Family']
---

GroupDocs.Merger for .NET allows you to merge or manipulate document structure across a wide range of file [formats](https://docs.groupdocs.com/display/mergernet/Supported+Document+Types). Those who are new to this API, you can join several documents into one, split single document to multiple documents, reorder or replace document pages, change page orientation and manage document password.

Version 19.9 is a major release. We totally restructured the API and below are the reasons to migrate:

*   **Merger** class introduced as a single entry point to manage the document processing of any supported file format
*   API is improved to decrease memory usage
*   Easy to instantiate proper options class and control over document structure manipulation processes

Those who are already using the API, let us share the code difference. We will see how to join documents using old and new API.

That's how we were joining documents in older version:

{{< gist GroupDocsGists 0bd8b4db277c1db0f9f3590e819a4c32 "oldcode.cs" >}}

Below is the new way:

{{< gist GroupDocsGists 1072e7c36c402bd339d5cc3528256d85 "newcode.cs" >}}

The legacy API have been moved into Legacy namespace so after update to this version it is required to make project-wide replacement of namespace usages from **GroupDocs.Merger** to **GroupDocs.Merger.Legacy** to resolve build issues.

One new file format **.mht** is also supported in this version.  
Download or clone our updated [GitHub](https://github.com/groupdocs-merger/GroupDocs.Merger-for-.NET) example project. Go through the [developer guide](https://docs.groupdocs.com/display/mergernet/Developer+Guide) and if you face any issue, you can post on [forum](https://forum.groupdocs.com/c/merger).




