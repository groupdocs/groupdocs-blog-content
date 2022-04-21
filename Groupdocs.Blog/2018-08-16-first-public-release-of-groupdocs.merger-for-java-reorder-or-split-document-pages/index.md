---
title: 'First Public Release of GroupDocs.Merger for Java - Reorder or Split Document Pages'
date: Thu, 16 Aug 2018 07:58:23 +0000
draft: false
url: /2018/08/16/first-public-release-of-groupdocs.merger-for-java-reorder-or-split-document-pages/
author: 'Atir Tahir'
summary: ''
tags: ['GrupDocs.Merger for Java']
categories: ['GroupDocs.Merger Product Family']
---

[![GroupDocs Editor for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/08/groupdocs-merger.png)](https://www.groupdocs.com/products/merger/net)

We are pleased to announce [GroupDocs.Merger for Java](https://products.groupdocs.com/merger/java) 18.8. A back-end document manipulation API that allows to split, remove or reorder pages in a document of supported format. Pages could be swapped or trimmed. You can also manage documents protection. GroupDocs.Merger for Java allows to check document protection and then set, remove or update password. Aside this, API permits to join two or more documents of same file format into one.

# Purpose Behind GroupDocs.Merger for Java API

GroupDocs.Merger for Java is an organized API, using that you can manipulate a document programatically in different ways. For instance, see how simply you can trim a document:```
PagesOptions pagesOptions = new PagesOptions(FileFormat.PDF, password, pages);
InputStream documentExample = new FileInputStream(sourceFile);
// Main method.
DocumentResult result = new DocumentHandler().trim(documentExample, pagesOptions);
```API is designed to facilitate users to move, remove and swap pages within a document using simplified calls.

# Supported Features and Formats

GroupDocs.Merger for Java supports a lot of document formats and many document manipulation features.

## Supported Document Formats

*   Word
*   PDF
*   Cell
*   Slide

In order to see file format extensions please visit [this](https://docs.groupdocs.com/display/mergerjava/Supported+Document+Formats) article.

## Features offered by GroupDocs.Merger for Java

*   Combine and merge multiple files into one document
*   Split document to multiple files
*   Arrange documents in any order
*   Check document protection
*   Remove pages from document

See all API features here.

# Available Channels and Resources

Here are a few channels and resources for you to learn, try and get technical support on GroupDocs.Merger:

*   [Download](http://downloads.groupdocs.com/merger/java "GroupDocs.Merger Download") - GroupDocs.Merger for Java Download
*   [Documentation](https://docs.groupdocs.com/display/mergerjava/Home "Merger API documentation") - API Documentation
*   [API Reference](https://apireference.groupdocs.com/java/merger "GroupDocs.Merger API reference") - GroupDocs.Merger for Java API Reference
*   [Examples](https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java "How to use Merger API")\- Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/merger) - Technical Support Forum for GroupDocs.Merger queries

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/merger "Technical Support Forum").




