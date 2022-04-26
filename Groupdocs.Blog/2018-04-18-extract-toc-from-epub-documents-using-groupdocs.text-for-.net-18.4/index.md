---
title: 'Extract TOC from EPUB Documents using GroupDocs.Text for .NET 18.4'
date: Wed, 18 Apr 2018 07:05:55 +0000
draft: false
url: /2018/04/18/extract-toc-from-epub-documents-using-groupdocs.text-for-.net-18.4/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'Extract Text', 'GroupDocs.Text for .NET Releases', 'Text Extraction API for .NET', 'Text Extractor']
categories: ['GroupDocs.Parser Product Family']
---

[![GroupDocs.Text for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs.text-for-dotnet.png)](https://products.groupdocs.com/)It gives us immense pleasure to announce the release of version 18.4 of **[GroupDocs.Text for .NET.](https://products.groupdocs.com/)** The latest version allows extracting the table of contents from the **EPUB** documents. Furthermore, we have added the feature of detecting media type of **.one** file. Following sections provide details about the newly added features.

# Extracting TOC from EPUB Documents

Using version 18.4, you can now extract TOC from the EPUB documents. To access the TOC, **TableOfContents** property of **EpubPackage **class is used. Once you get the TOC from the document, you can access the following properties of TOC items using **TableOfContentsItem** class:

*   **Text** \- the text of the item (usually, it is a chapter’s title)
*   **PageIndex** \- the page index of the text (null if it is just a node without content)
*   **Count** \- the number of sub-items (zero if the item hasn’t sub-items)
*   **this\[int index\]** - gets a sub-item
*   **ExtractPage** \- extracts a text of the item

Following code snippet shows how to extract TOC from EPUB document.```
// Create a text extractor
using (EpubTextExtractor extractor = new EpubTextExtractor(@"document.epub"))
{
    // Print TOC on the screen
    PrintToc(extractor[0].TableOfContents, 0);
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
```

# Media Type Detector for .one Files

This feature allows detecting the media type of OneNote sections using **_NoteMediaTypeDetector_** class. Following code snippet shows how to use this feature.```
// Create a media type detector
var detector = new NoteMediaTypeDetector();
// Detect a media type by the file name
Console.WriteLine(detector.Detect("section.one");
// Detect a media type by the content
Console.WriteLine(detector.Detect(stream));
```

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




