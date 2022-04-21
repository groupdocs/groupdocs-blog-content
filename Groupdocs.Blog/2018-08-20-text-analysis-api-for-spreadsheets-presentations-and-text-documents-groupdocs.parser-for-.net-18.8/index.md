---
title: 'Text Analysis API for Spreadsheets, Presentations and Text Documents - GroupDocs.Parser for .NET 18.8'
date: Mon, 20 Aug 2018 06:22:23 +0000
draft: false
url: /2018/08/20/text-analysis-api-for-spreadsheets-presentations-and-text-documents-groupdocs.parser-for-.net-18.8/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'Dcoument Parsing API', 'Document Parser', 'Text Extraction API for .NET']
categories: ['GroupDocs.Parser for .NET Releases', 'GroupDocs.Parser Product Family']
---

![GroupDocs.Parser for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/05/groupdocs-parser.png "GroupDocs-Parser-theme-100x100")

We are pleased to announce the release of version 18.8 of [GroupDocs.Parser for .NET](https://products.groupdocs.com/parser/net). In this version, we have extended the support of text analysis API for spreadsheets, presentations and text documents. Furthermore, the latest version allows providing a password for protected documents on-demand. We’d recommend you to use the latest version of the API and share your feedback.

# Features Introduced

## Text Analysis APIGroupDocs.Parser allows extracting text areas from the pages of a document. This feature may help you getting data for text analysis. _DocumentContent_ abstract class provides API to extract text areas from document pages. This feature has been extended for spreadsheets, presentations and text documents in the current version of the API. The following code sample shows how to get text areas from a text document.```
// Create a text extractor
WordsTextExtractor extractor = new WordsTextExtractor("invoice.docx");
  
// Create search options
TextAreaSearchOptions searchOptions = new TextAreaSearchOptions();
// Set a regular expression to search 'Invoice # XXX' text
searchOptions.Expression = "\\s?INVOICE\\s?#\\s?[0-9]+";
// Limit the search with a rectangle
searchOptions.Rectangle = new GroupDocs.Parser.Rectangle(10, 10, 300, 150);
 
// Get text areas
IList< textarea > texts = extractor.DocumentContent.GetTextAreas(0, searchOptions);
             
// Iterate over a list
foreach(TextArea area in texts)
{
    // Print a text
    Console.WriteLine(area.Text);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/parser/net) documentation article.

## Requesting the Password for Protected DocumentsWe have two ways to provide a password for the protected documents. When the password is known, Password property of LoadOptions class is used. If it is not known whether it is protected or not before opening the document, PasswordProvider property of LoadOptions class is used. This feature allows providing a password for protected documents on-demand. _IPasswordProvider _interface is used for this purpose. For more details on this feature, please visit [this](https://docs.groupdocs.com/parser/net) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Parser:

*   [Installation](https://www.nuget.org/packages/groupdocs.parser "GroupDocs.Text Nuget Package") - Install GroupDocs.Parser using NuGet
*   [Documentation](https://docs.groupdocs.com/display/parsernet/Home "GroupDocs.Text Documentation") - Product Docs
*   [Examples](https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET "GroupDocs.Text Github repository") - GitHub Source Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPQyfL8Tkz8XH7yOPhrglb7 "GroupDocs.Text for .NET tutorials") – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/parser "GroupDocs.Text for .NET Support forum") – Technical Support Forum for GroupDocs.Parser

# Have Queries?

If you have got any queries or concerns about the API, please feel free to get in touch with us over the [forum](https://forum.groupdocs.com/). We’ll be glad to address your concerns.




