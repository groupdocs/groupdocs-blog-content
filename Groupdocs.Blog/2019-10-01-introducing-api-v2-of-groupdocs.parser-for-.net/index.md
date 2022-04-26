---
title: 'Introducing API v2 of GroupDocs.Parser for .NET'
date: Tue, 01 Oct 2019 06:07:23 +0000
draft: false
url: /2019/10/01/introducing-api-v2-of-groupdocs.parser-for-.net/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Parser for .NET Releases', 'GroupDocs.Parser Product Family']
---

The all-new API v2 of [**GroupDocs.Parser for .NET**](https://products.groupdocs.com/parser/net) has been released! It would be a piece of breaking news for those who are already using our **document parsing API** as well as who are looking for an easy to use solution for **extracting text**, **images**, and **metadata** from **PDF**, **word processing** **documents**, **spreadsheets**, **presentations**, **emails**, **EPUB** & **ZIP** file formats.

## What's new in the API v2?

We have done some major updates at the architecture level of the API to perform product optimization. This also includes the renaming of classes and methods as well as simplifying the whole process of document parsing. The following are some key updates we have done in the latest release:

*   The [_Parser_](https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser)class is introduced as a **single entry point** to extract data from the documents.  
    
*   The data extraction process has been unified for all the data types i.e. text, metadata, etc.
*   The product architecture has been redesigned from scratch in order to simplify passing options and classes to manipulate the data.
*   Document information and preview generation procedures have been simplified.
*   The overall document related classes have been unified into common classes.

## What is the difference in coding style?

Because of the changes in the architecture of the API, the coding style has also been modified and simplified. Have a look at the difference in terms of coding style between the old and the new version of the API.

**Old coding style**

{{< gist GroupDocsGists 1abb5d9bf8336ff30a9791636e9eda3c "DocumentParsingCSharpOld.cs" >}}

**New coding style**

{{< gist GroupDocsGists 1abb5d9bf8336ff30a9791636e9eda3c "DocumentParsingCSharpNew.cs" >}}

In case you are already using GroupDocs.Parser for .NET in your application and want to migrate to the latest release, have a look at the [migration notes](https://docs.groupdocs.com/display/parsernet/Migration+Notes). Consult the [release notes](https://docs.groupdocs.com/display/parsernet/GroupDocs.Parser+for+.NET+19.9+Release+Notes) for a complete list of public API changes.

Get started with the API v2 by cloning or downloading the source code examples from [GitHub](https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET). Visit the [documentation](https://docs.groupdocs.com/display/parsernet/Home) of the API for more details about every feature of the API. In case you would find something difficult for you, do let us know on our [forum](https://forum.groupdocs.com/c/parser).




