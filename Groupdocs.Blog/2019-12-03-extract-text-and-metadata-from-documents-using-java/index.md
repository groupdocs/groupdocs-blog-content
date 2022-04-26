---
title: 'Parse Documents to Extract Text and Metadata using Java'
date: Tue, 03 Dec 2019 15:00:01 +0000
draft: false
url: /2019/12/03/extract-text-and-metadata-from-documents-using-java/
aliases:
    - /2019/12/03/java-api-to-read-and-extract-text-images-metadata-in-documents/
author: 'Usman Aziz'
summary: ''
tags: ['document parsing API', 'extract metadata in java', 'extract text in java', 'parser in java', 'read text']
categories: ['GroupDocs.Parser Product Family']
---

[GroupDocs.Parser for Java](https://products.groupdocs.com/parser/java) API is in the market since last year and it is proved to be one of the powerful document parser APIs. It allows parsing and reading popular formats of word processing documents, spreadsheets, presentations, ebooks, emails, markup documents, notes, archives, and databases. Not only the text but you can also extract the images and metadata properties from various document formats including PDF, XLS, XLSX, CSV, DOC, DOCX, PPT, PPTX, MPP, EML, MSG, OST, PST, ONE, and [many more](https://docs.groupdocs.com/display/parserjava/Supported+Document+Formats).

In order to improve the working of the API and simplify its usage for the developers, we have revamped its architecture from scratch. Now, the improved and simplified API is onboard as [GroupDocs.Parser for Java 19.11](https://downloads.groupdocs.com/parser/java).

## What is new in Parser API for Java?

In case you are using an older version. The following are the key reasons why you should upgrade to the latest release.

*   The _[Parser](https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser)_  class is introduced to read and extract data from the document of any supported format.  
    
*   The process of data extraction has been unified for all data types.  
    
*   Product architecture has been revamped from scratch in order to simplify the usage of different options and classes to manipulate data.
*   The process of getting document information and preview generation has been simplified.

## How to migrate?

Since the product has gone through the major updates, the classes, methods, and the way they are used have also been changed. However, we haven't yet removed the legacy API from the package, instead, we have moved it to the _[com.groupdocs.parser.legacy](https://apireference.groupdocs.com/parser/java)_ package. Once you upgrade to the v19.11, you just need to perform project-wide replacements of packages from _com.groupdocs.parser_ to _com.groupdocs.parser.legacy_. This way you will get rid of immediate build issues. You can then gradually proceed to update the source code and use the new public API's classes and methods.

## Code Comparison - Extract Text and Metadata from Documents using Java

Let's now have a look at how the code has been changed for extracting text and metadata using the latest release.

### **Extract Text from PDF** in Java

#### **v19.11 or Later**

{{< gist GroupDocsGists edf8d6b50694f877f39586059d8562e3 "ExtractTextFromPDFInJavaNew.java" >}}

#### **Legacy API**

{{< gist GroupDocsGists edf8d6b50694f877f39586059d8562e3 "ExtractTextFromPDFInJavaOld.java" >}}

### **Extract Metadata** from Documents in Java

#### **v19.11 or Later**

{{< gist GroupDocsGists edf8d6b50694f877f39586059d8562e3 "ExtractMetadataFromDocumentNew.Java" >}}

#### **Legacy API**

{{< gist GroupDocsGists edf8d6b50694f877f39586059d8562e3 "ExtractMetadataFromDocumentOld.Java" >}}

For more details on code comparison, please have a look at the [migration notes](https://docs.groupdocs.com/display/parserjava/Migration+Notes).

Well, this was a brief overview of the latest release. Now, you can evaluate the recent changes yourself by downloading or cloning the updated source code examples from the [GitHub repository](https://github.com/groupdocs-parser/GroupDocs.Parser-for-java). We have also updated the [documentation](https://docs.groupdocs.com/display/parserjava/Introducing+GroupDocs.Parser+for+Java) as per the latest release.

In case you would face any issue while migrating to the latest release or using any particular feature, feel free to let us know via our [forum](https://forum.groupdocs.com/c/parser).




