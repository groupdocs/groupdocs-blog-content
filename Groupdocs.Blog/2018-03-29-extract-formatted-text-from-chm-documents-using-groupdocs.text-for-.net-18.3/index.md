---
title: 'Extract Formatted Text from CHM Documents using GroupDocs.Text for .NET 18.3'
date: Thu, 29 Mar 2018 16:53:14 +0000
draft: false
url: /2018/03/29/extract-formatted-text-from-chm-documents-using-groupdocs.text-for-.net-18.3/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'Extract Text', 'GroupDocs.Text for .NET Releases', 'Text Extraction API for .NET', 'Text Extractor']
categories: ['GroupDocs.Parser Product Family']
---

[![GroupDocs.Text for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs.text-for-dotnet.png)](https://products.groupdocs.com/)We keep looking forward to bringing you more features and therefore, we have released version 18.3 of **[GroupDocs.Text for .NET](https://products.groupdocs.com/)** providing the support of extracting formatted text from **CHM** documents. The latest version also allows you to extract text by pages and extract table of content from CHM documents. The following sections will provide you the details about the new features of the API.

# Extracting Formatted Text from CHM Documents

GroupDocs.Text provides a couple of ways to extract formatted text from CHM documents. You can extract the text line by line or as a whole as described below.

## Extracting Line of CharactersFollowing code sample shows how to extract a line of characters from a CHM document.```
// Create a text extractor for chm documents
using (var extractor = new ChmFormattedTextExtractor(stream)) {
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

## Extracting all CharactersFollowing code sample shows how to extract all characters at once from a CHM document.```
// Create a text extractor for chm documents
using (var extractor = new ChmFormattedTextExtractor(stream)) {
  // Extract a text
  Console.WriteLine(extractor.ExtractAll());
}
```You can also use a document formatter to extract text in a particular format. For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

# Extracting Text by Pages from CHM Documents

Using version 18.3, you can also extract text by pages from the CHM documents. For page by page text extraction, we have added the implementation of **IPageTextExtractor** interface to **ChmTextExtractor** class. For more details on this feature, please visit [this](https://docs.groupdocs.com/) documentation article.

# Extracting TOC from CHM Documents

We have also added a useful feature of extracting the table of content from CHM documents. To access the TOC, **TableOfContents** property of **ChmTextExtractor** class is used. Following code sample shows how to extract the table of content from a CHM document.```
// Create a text extractor
using (ChmTextExtractor extractor = new ChmTextExtractor(@"C:\Sources\GroupDocs.Text\TestData\unit\chm\VBOB6.CHM"))
{
    // Print TOC on the screen
    PrintToc(extractor.TableOfContents, 0);
}
 
private static void PrintToc(IEnumerable tableOfContents, int depth)
{
    // Use spaces to indicate the depth of the TOC item
    string spaces = new string(' ', depth);
 
    // Iterate over items
    foreach (TableOfContentsItem item in tableOfContents)
    {
        System.Console.Write(spaces);
        // Print the item's text
        System.Console.Write(item.Text);
 
        // If item has a text (it's not just a node)
        if (item.PageIndex.HasValue)
        {
            // Print the text length
            System.Console.Write(string.Format(" ({0})", item.ExtractPage().Length));
        }
 
        System.Console.WriteLine();
 
        // If the item has children
        if (item.Count > 0)
        {
            // Print them
            PrintToc(item, depth + 1);
        }
    }
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/) documentation article.

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




