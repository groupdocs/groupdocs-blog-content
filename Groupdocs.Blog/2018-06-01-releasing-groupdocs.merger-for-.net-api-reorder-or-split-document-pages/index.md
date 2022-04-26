---
title: 'Releasing GroupDocs.Merger for .NET API - Reorder or Split Document Pages'
date: Fri, 01 Jun 2018 16:01:37 +0000
draft: false
url: /2018/06/01/releasing-groupdocs.merger-for-.net-api-reorder-or-split-document-pages/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Merger for .NET', 'GroupDocs.Merger Product Family']
---

[![GroupDocs Editor for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/05/groupdocs-merger.png)](https://www.groupdocs.com/products/merger/net)

We are pleased to announce GroupDocs.Merger for .NET 18.5. A back-end document manipulation API that allows to split, remove or reorder pages in a document of supported format. Pages could be swapped or trimmed. You can also manage documents protection. GroupDocs.Merger for .NET allows to check document protection and then set, remove or update password. Aside this, API permits to join two or more documents of same file format into one.

# Purpose Behind GroupDocs.Merger for .NET API

GroupDocs.Merger for .NET is an organized API, using that you can manipulate a document programatically in different ways. For instance, see how simply you can trim a document:```
PagesOptions pagesOptions = new PagesOptions(FileFormat.Pdf, password, pages);
Stream openFile = new FileStream(sourceFile, FileMode.Open);
// Main method.
DocumentResult result = new DocumentHandler().Trim(openFile, pagesOptions);
```API is designed to facilitate users to move, remove and swap pages within a document using simplified calls.

# Supported Features and Formats

GroupDocs.Merger for .NET supports a lot of document formats and many document manipulation features.

## Supported Document Formats

*   Word
*   PDF
*   Cell
*   Slide

In order to see file format extensions please visit [this](https://docs.groupdocs.com/merger/net/) article.

## Features offered by GroupDocs.Merger for .NET

*   Combine and merge multiple files into one document
*   Split document to multiple files
*   Arrange documents in any order
*   Check document protection
*   Remove pages from document

See all API features [here](https://docs.groupdocs.com/display/mergernet/Features+Overview).

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on GroupDocs.Merger:

*   [NuGet](https://www.nuget.org/packages/GroupDocs.Merger/ "GroupDocs.Merger Nuget Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/display/mergernet/Getting+Started "Merger API documentation") - API Documentation
*   [API Reference](https://apireference.groupdocs.com/net/merger "GroupDocs.Merger API reference") - GroupDocs.Merger for .NET API Reference
*   [Examples](https://github.com/groupdocs-merger/GroupDocs.Merger-for-.NET "How to use Merger API")\- Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/merger) - Technical Support Forum for GroupDocs.Merger queries

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/merger "Technical Support Forum").




