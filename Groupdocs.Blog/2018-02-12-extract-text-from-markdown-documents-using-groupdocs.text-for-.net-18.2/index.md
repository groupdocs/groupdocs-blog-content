---
title: 'Extract Text from Markdown Documents using GroupDocs.Text for .NET 18.2'
date: Mon, 12 Feb 2018 10:36:19 +0000
draft: false
url: /2018/02/12/extract-text-from-markdown-documents-using-groupdocs.text-for-.net-18.2/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'GroupDocs.Text for .NET Releases', 'Text Extraction API for .NET']
categories: ['GroupDocs.Parser Product Family']
---

[![GroupDocs.Text for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs.text-for-dotnet.png)](https://products.groupdocs.com/)We are pleased to announce that we have released another version of **[GroupDocs.Text for .NET](https://products.groupdocs.com/)** API providing the support of text extraction from **Markdown** documents. Using GroupDocs.Text for .NET 18.2, you can extract raw text, formatted text and the structured text from a Markdown document. Following sections will provide you the details about the new features of the API.

# Extracting Raw Text from Markdown Documents

Since version 18.2, GroupDocs.Text allows you to extract a line of characters as well as all the characters at once from a Markdown document. Following code samples show you how to extract text in either way.

## Extracting Line of CharactersFollowing code sample shows how to extract a line of characters from a Markdown document.```
// Create a text extractor for Markdown documents
using (var extractor = new MarkdownTextExtractor(stream)) {
  // Extract a line of the text
  string line = extractor.ExtractLine();
  // If the line is null, then the end of the file is reached
  while (line != null) {
    // Print a line to the console
    Console.WriteLine(line);
    // Extract another line
    line = extractor.ExtractLine();
  }
}
```

## Extracting all CharactersFollowing code sample shows how to extract all characters at once from a Markdown document.```
// Create a text extractor for Markdown documents
using (var extractor = new MarkdownTextExtractor(stream)) {
  // Extract a text
  Console.WriteLine(extractor.ExtractAll());
}
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

# Extracting Formatted Text from Markdown Documents

GroupDocs.Text also allows you to extract formatted text from the Markdown documents. Same as raw text extraction, you can extract the characters line by line as well as extract all the characters from the document.

## Extracting Line of CharactersFollowing code sample shows how extract line of characters as formatted text from a Markdown document.```
// Create a text extractor for Markdown documents
using (var extractor = new MarkdownFormattedTextExtractor(stream)) {
  // Extract a line of the text
  string line = extractor.ExtractLine();
  // If the line is null, then the end of the file is reached
  while (line != null) {
    // Print a line to the console
    Console.WriteLine(line);
    // Extract another line
    line = extractor.ExtractLine();
  }
}
```

## Extracting all CharactersFollowing is the sample code to extract all the characters as formatted text from Markdown documents.```
// Create a text extractor for Markdown documents
using (var extractor = new MarkdownFormattedTextExtractor(stream)) {
  // Extract a text
  Console.WriteLine(extractor.ExtractAll());
}
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

# Extracting Structured Text from Markdown Documents

Since version 18.2, GroupDocs.Text enables you to extract text with its structure from Markdown documents. Following code sample shows how to extract headers from Markdown document.```
StringBuilder sb = new StringBuilder();
IStructuredExtractor extractor = new MarkdownTextExtractor(stream);
StructuredHandler handler = new StructuredHandler();
 
// Handle List event to prevent processing of lists
handler.List += (sender, e) => e.Properties.SkipElement = true; // ignore lists
 
// Handle Table event to prevent processing of tables
handler.Table += (sender, e) => e.Properties.SkipElement = true; // ignore tables
 
// Handle Paragraph event to process a paragraph
handler.Paragraph += (sender, e) =>
{
    int h1 = (int)ParagraphStyle.Heading1;
    int h6 = (int)ParagraphStyle.Heading6;
 
    int style = (int)e.Properties.Style;
    if (h1 <= style && style <= h6) { if (sb.Length > 0)
        {
            sb.AppendLine();
        }
 
        sb.Append(' ', style - h1); // make an indention for the header (h1 - no indention)
    }
    else
    {
        e.Properties.SkipElement = e.Properties.Style != ParagraphStyle.Title; // skip paragraph if it's not a header or a title
    }
};
 
// Handle ElementText event to process a text
handler.ElementText += (sender, e) => sb.Append(e.Text);
 
// Extract a text with its structure
extractor.ExtractStructured(handler);
 
Console.WriteLine(sb.ToString());
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Text:

*   [Download](http://downloads.groupdocs.com/text/net "GroupDocs.Text dll and msi") - MSI Package or Zipped DLLs Only
*   [NuGet](https://www.nuget.org/packages/groupdocs.text "GroupDocs.Text Nuget Package") - NuGet Package
*   [Documentation](https://docs.groupdocs.com/"GroupDocs.Text Documentation") - Product Docs
*   [Examples](https://github.com/groupdocs-text/GroupDocs.Text-for-.NET "GroupDocs.Text Github repository") - Github Source Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPQyfL8Tkz8XH7yOPhrglb7 "GroupDocs.Text for .NET tutorials") – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/text "GroupDocs.Text for .NET Support forum") – Technical Support Forum for GroupDocs.Text

# Feedback

As always, you are welcome to share your feedback or suggestions to improve this product. Just create a new topic at our [forum](https://forum.groupdocs.com/c/text) and our dedicated support team will be there to respond.




