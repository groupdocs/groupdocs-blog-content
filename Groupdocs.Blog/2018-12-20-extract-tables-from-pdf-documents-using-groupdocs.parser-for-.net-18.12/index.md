---
title: 'Extract Tables from PDF Documents using GroupDocs.Parser for .NET 18.12'
date: Thu, 20 Dec 2018 10:08:36 +0000
draft: false
url: /2018/12/20/extract-tables-from-pdf-documents-using-groupdocs.parser-for-.net-18.12/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'Document Parser', 'metadata extractor', 'text analysis API']
categories: ['GroupDocs.Parser for .NET', 'GroupDocs.Parser for .NET Releases', 'GroupDocs.Parser Product Family']
---

![GroupDocs.Parser for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/05/groupdocs-parser.png "GroupDocs-Parser-theme-100x100")

It is our pleasure to announce the release of version 18.12 of [GroupDocs.Parser for .NET](https://products.groupdocs.com/parser/net). The latest version allows you to extract the tables from PDF documents. Furthermore, we have added the support of extracting text and metadata from text and presentation templates. For more details, please have a look at the [release notes](https://docs.groupdocs.com/display/parsernet/GroupDocs.Parser+for+.NET+18.12+Release+Notes) of version 18.12.

# Features Introduced

## Extracting Tables from PDF DocumentsThis feature is very useful when you want to extract only the tables form a PDF document. For extracting tables, **TableAreaParser** class is used. The instance of **TableAreaParser** class is available via property with the same name in **PdfTextExtractor** class. You can create the table bounds manually or let the API detect the layout in automatic mode using **TableAreaDetector** class. For working example of this feature, please refer to [this](https://docs.groupdocs.com/parser/net) documentation article.

## Extracting Text and Metadata from Text and Presentation TemplatesGroupDocs.Parser now supports extracting text and metadata from the following text and presentation template formats:

*       dotx (Template)
*       dotm (Macro-enabled template)
*       ott (OpenDocument Text Template)
*       potx (Template)
*       potm (Macro-enabled template)
*       ppsm (Macro-enabled slideshow)
*       pptm (Macro-enabled presentation)

The following code samples show how to extract text and metadata from templates.```
// Extracting Text
void ExtractText(string fileName)
{
    // Extract a text from the file
    var text = Extractor.Default.ExtractText(fileName);
    // Print an extracted text
    Console.WriteLine(text);
}
// Extracting Metadata 
void ExtractMetadata(string fileName)
{
    // Extract metadata from the file
    var metadata = Extractor.Default.ExtractMetadata(fileName);
    // Print extracted metadata
    foreach (var m in metadata)
    {
        // Print a metadata key
        Console.Write(m.Key);
        Console.Write(": ");
        // Print a metadata value
        Console.WriteLine(m.Value);
    }
}
```

# Enhancements

## Detecting Type of Password-protected Office Open XML DocumentsThis feature allows detecting media type of the password-protected Office Open XML documents. To detect media type of encrypted Office Open XML document, **Detect(Stream, LoadOptions)** method is used. You can also use **IPasswordProvider** interface for batch document processing. For working examples of this feature, please refer to [this](https://docs.groupdocs.com/parser/net) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Parser:

*   [Installation](https://www.nuget.org/packages/groupdocs.parser "GroupDocs.Text Nuget Package") - Install GroupDocs.Parser using NuGet
*   [Documentation](https://docs.groupdocs.com/display/parsernet/Home "GroupDocs.Text Documentation") - Product Docs
*   [Examples](https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET "GroupDocs.Text Github repository") - GitHub Source Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPQyfL8Tkz8XH7yOPhrglb7 "GroupDocs.Text for .NET tutorials") – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/parser "GroupDocs.Text for .NET Support forum") – Technical Support Forum for GroupDocs.Parser

# Have Queries?

If you have got any queries or concerns about the API, please feel free to get in touch with us over the [forum](https://forum.groupdocs.com/). We’ll be glad to address your concerns.




