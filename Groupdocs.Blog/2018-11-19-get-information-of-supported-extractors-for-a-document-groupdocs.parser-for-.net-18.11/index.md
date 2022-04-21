---
title: 'Get Information of Supported Extractors for a Document using GroupDocs.Parser for .NET 18.11'
date: Mon, 19 Nov 2018 05:48:28 +0000
draft: false
url: /2018/11/19/get-information-of-supported-extractors-for-a-document-groupdocs.parser-for-.net-18.11/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'Document Parser', 'document parsing API', 'document text extraction', 'text parser']
categories: ['GroupDocs.Parser for .NET', 'GroupDocs.Parser for .NET Releases', 'GroupDocs.Parser Product Family']
---

![GroupDocs.Parser for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/05/groupdocs-parser.png "GroupDocs-Parser-theme-100x100")

We are pleased to announce the release of version 18.11 of [GroupDocs.Parser for .NET](https://products.groupdocs.com/parser/net). The latest version came up with one new feature and three enhancements. It allows you to get information about the supported extractors for a document. Furthermore, we have improved the text area extraction for the PDF documents. For more details, please have a look at the release notes of version 18.11.

# Features Introduced

## Getting Information of Supported Extractors for a DocumentThis feature helps to get the information about the supported extractors for a document. For example, you can check if you can extract the plain text, formatted text, and metadata from a particular document. Furthermore, you can also check if the document is a container that contains other documents in it. For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/net) documentation article.

# Enhancements

## IFastTextExtractor InterfaceGroupDocs.Parser allows changing the default behavior of text extraction. By default, the text is extracted using the **_Standard Extract_** mode. In _**Standard Extract**_ mode, the text is extracted with better quality but it takes more time. This enhancements allows setting the fast text extraction via _**IFastTextExtractor**_ interface. The support for _**IFastTextExtractor**_ interface is added to the following classes:

*   _**PdfTextExtractor** _
*   _**CellsTextExtractor** _
*   _**SlidesTextExtractor** _

For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/net) documentation article.

## IDocumentContentExtractor InterfaceThis enhancement allows getting the access to _**Text Analysis API**_ via _**IDocumentContentExtractor**_ interface. The support for **IDocumentContentExtractor** interface is added to the following classes:

*   _**PdfTextExtractor** _
*   _**CellsTextExtractor** _
*   _**SlidesTextExtractor**_
*   _**WordsTextExtractor**_

For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/net) documentation article.

## Improved Text Area Extraction for PDF DocumentsThis enhancement improves the text area extraction for PDF documents. In the latest version, the Y-coordinates of text areas start from the top of the page.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Parser:

*   [Installation](https://www.nuget.org/packages/groupdocs.parser "GroupDocs.Text Nuget Package") - Install GroupDocs.Parser using NuGet
*   [Documentation](https://docs.groupdocs.com/display/parsernet/Home "GroupDocs.Text Documentation") - Product Docs
*   [Examples](https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET "GroupDocs.Text Github repository") - GitHub Source Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPQyfL8Tkz8XH7yOPhrglb7 "GroupDocs.Text for .NET tutorials") – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/parser "GroupDocs.Text for .NET Support forum") – Technical Support Forum for GroupDocs.Parser

# Have Queries?

If you have got any queries or concerns about the API, please feel free to get in touch with us over the [forum](https://forum.groupdocs.com/). We’ll be glad to address your concerns.




