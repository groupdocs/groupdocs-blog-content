---
title: 'Extract Text Areas from Document Pages using GroupDocs.Parser for .NET 18.7'
date: Tue, 10 Jul 2018 06:22:08 +0000
draft: false
url: /2018/07/10/extract-text-areas-from-document-pages-using-groupdocs.parser-for-.net-18.7/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'Document Parser', 'Extract Text', 'Text Extraction API for .NET', 'Text extractor API', 'text parser']
categories: ['GroupDocs.Parser for .NET', 'GroupDocs.Parser for .NET Releases', 'GroupDocs.Parser Product Family']
---

![GroupDocs.Parser for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/05/groupdocs-parser.png "GroupDocs-Parser-theme-100x100")

Today, we are excited to announce the release of version 18.7 of [GroupDocs.Parser for .NET](https://products.groupdocs.com/parser/net). The latest release supports extracting text areas from document pages. This feature may help you getting data for text analysis. We recommend you to upgrade the API to the latest version and share your valuable feedback.

## Extracting Text AreasExtracting text areas is useful when you need to get the data for text analysis. To extract text areas, text extractors implement their own internal private class and provide DocumentContent property (see [PdfTextExtractor](https://apireference.groupdocs.com/parser/net) as the sample). The DocumentContent class has the following members:

Member

Description

PageCount

Returns a total number of document pages

Dispose

Releases resources used by the class

GetPage

Returns a document page (see below)

GetTextAreas

Returns a collection of TextArea objects (see below)

The following code sample shows how to get text areas from a PDF document.```
// Create a text extractor
PdfTextExtractor extractor = new PdfTextExtractor("invoice.pdf");
 
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
```

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Parser:

*   [Installation](https://www.nuget.org/packages/groupdocs.parser "GroupDocs.Text Nuget Package") - Install GroupDocs.Parser using NuGet
*   [Documentation](https://docs.groupdocs.com/display/parsernet/Home "GroupDocs.Text Documentation") - Product Docs
*   [Examples](https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET "GroupDocs.Text Github repository") - GitHub Source Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPQyfL8Tkz8XH7yOPhrglb7 "GroupDocs.Text for .NET tutorials") – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/parser "GroupDocs.Text for .NET Support forum") – Technical Support Forum for GroupDocs.Parser

## Have Queries?If you have got any queries or concerns about the API, please feel free to get in touch with us over the [forum](https://forum.groupdocs.com/). We’ll be glad to address your concerns.




