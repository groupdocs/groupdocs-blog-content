---
title: 'Improved Text Area Extraction for PDF Documents in GroupDocs.Parser for Java 18.11'
date: Mon, 19 Nov 2018 05:49:37 +0000
draft: false
url: /2018/11/19/improved-text-area-extraction-for-pdf-documents-in-groupdocs.parser-for-java-18.11/
author: 'Usman Aziz'
summary: ''
tags: ['Document Parser', 'document text extraction', 'document text parser', 'Java API', 'Java Text Extractor', 'text extraction API', 'text extractor API for Java', 'GroupDocs.Parser for Java Releases']
categories: ['GroupDocs.Parser Product Family']
---

![GroupDocs.Parser for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/06/groupdocs-parser-java.png "GroupDocs-Parser-theme-100x100")

We are delighted to announce the release of [GroupDocs.Parser for Java](https://products.groupdocs.com/parser/java "GroupDocs.Parser product page") 18.11. The latest version came up with one new feature and three enhancements. It allows you to get information about the supported extractors for a document. Furthermore, we have improved the text area extraction for the PDF documents. For more details, please have a look at the [release notes](https://docs.groupdocs.com/display/parserjava/GroupDocs.Parser+for+java+18.11+Release+Notes) of version 18.11.

# Features Introduced

## Getting Information of Supported Extractors for a DocumentThis feature helps to get the information about the supported extractors for a document. For example, you can check if you can extract the plain text, formatted text, and metadata from a particular document. Furthermore, you can also check if the document is a container that contains other documents in it. For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/java/) documentation article.

# Enhancements

## IFastTextExtractor InterfaceGroupDocs.Parser allows changing the default behavior of text extraction. By default, the text is extracted using the **_Standard Extract_** mode. In _**Standard Extract**_ mode, the text is extracted with better quality but it takes more time. This enhancements allows setting the fast text extraction via _**IFastTextExtractor**_ interface. The support for _**IFastTextExtractor**_ interface is added to the following classes:

*   _**PdfTextExtractor**_
*   _**CellsTextExtractor**_
*   _**SlidesTextExtractor**_

For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/java/) documentation article.

## IDocumentContentExtractor InterfaceThis enhancement allows getting the access to _**Text Analysis API**_ via _**IDocumentContentExtractor**_ interface. The support for **IDocumentContentExtractor** interface is added to the following classes:

*   _**PdfTextExtractor**_
*   _**CellsTextExtractor**_
*   _**SlidesTextExtractor**_
*   _**WordsTextExtractor**_

For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/java/) documentation article.

## Improved Text Area Extraction for PDF DocumentsThis enhancement improves the text area extraction for PDF documents. In the latest version, the Y-coordinates of text areas start from the top of the page.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Parser:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-parser "GroupDocs.Parser Installation") - Install GroupDocs.Parser from Maven
*   [Documentation](https://docs.groupdocs.com/display/parserjava/Introducing+GroupDocs.Parser+for+Java "Parser API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java "How to use Parser API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/parser) - Technical Support Forum for GroupDocs.Parser

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").





