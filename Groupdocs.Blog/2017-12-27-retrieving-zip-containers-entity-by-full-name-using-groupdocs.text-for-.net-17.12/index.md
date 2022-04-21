---
title: 'Retrieving ZIP Container''s Entity by Full Name using GroupDocs.Text for .NET 17.12'
date: Wed, 27 Dec 2017 14:20:54 +0000
draft: false
url: /2017/12/27/retrieving-zip-containers-entity-by-full-name-using-groupdocs.text-for-.net-17.12/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Text Extractor', 'GroupDocs.Text for .NET Releases', 'Text Extraction API for .NET']
categories: ['GroupDocs.Parser Product Family']
---

[![GroupDocs.Text for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs.text-for-dotnet.png)](https://products.groupdocs.com/)We are excited to announce that we have released version 17.12 of **GroupDocs.Text for .NET** API. In this version, we have introduced a simplified way of extracting text as well as formatted text using a simple interface. We have also extended the support of IPageTextExtractor interface for **OneNote** documents. Furthermore, the latest version also allows you to retrieve an entity by its name from **ZIP** container. Please continue to read for more details.

# GroupDocs.Text for .NET API - New Features

## Extracting Text via Extractor ClassThis feature allows you to extract text from a file or stream via a simple interface. We have added **ExtractText** method to **Extractor** class for this purpose. Following code snippet demonstrates the usage of this feature.```
// Extract text from the stream
Console.WriteLine(Extractor.Default.ExtractText(stream));

// Extract text from the file
Console.WriteLine(Extractor.Default.ExtractText(fileName)); 
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

## Extracting Formatted Text via Extractor ClassThis feature allows extracting formatted text from a file or stream via Extractor class. We have added **ExtractFormattedText** method to Extractor class for this feature. Following code snippet shows the usage of this feature.```
// Extract formatted text from the stream
Console.WriteLine(Extractor.Default.ExtractFormattedText(stream));
 
// Extract formatted text from the file
Console.WriteLine(Extractor.Default.ExtractFormattedText(fileName)); 
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

## Retrieving Entity by Full Name from ZIP ContainerThis feature allows you to get an entity by its full name from ZIP container. We have added **GetEntity** method to **ZipContainer** class for the implementation of this feature. Following is the sample code that could be used to get entity by its name.```
// Create a factory
ExtractorFactory factory = new ExtractorFactory();
// Create Zip container
ZipContainer zip = new ZipContainer(stream);
// Try to get "container.xml" entity from "META-INF" folder
Container.Entity containerEntry = zip.GetEntity("META-INF\\container.xml");
// If the entity isn't found
if (containerEntry == null)
{
    throw new GroupDocsTextException("File not found");
}
 
// Try to create a text extractor
TextExtractor extractor = factory.CreateTextExtractor(containerEntry.OpenStream());
try
{
    // Extract text (if the document type is supported)
    Console.WriteLine(extractor == null ? "Document type isn't supported" : extractor.ExtractAll());
}
finally
{
    // Cleanup
    if (extractor != null)
    {
        extractor.Dispose();
    }
}
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

# .NET Text Extraction API - Enhancements

## IPageTextExtractor Support for NoteTextExtractorIn GroupDocs.Text for .NET 17.12, we have extended the support of **IPageTextExtractor** for OneNote documents. **IPageTextExtractor** interface allows you to work with the document's pages in the same way for all supported documents. Following code snippets shows how to extract the text of OneNote document pages using IPageTextExtractor.```
// Create a text extractor
NoteTextExtractor textExtractor = new NoteTextExtractor(stream);

// Check if IPageTextExtractor is supported
    IPageTextExtractor pageTextExtractor = textExtractor as IPageTextExtractor;
    if (pageTextExtractor != null)
    {
        // Iterate over all pages
        for (int i = 0; i < pageTextExtractor.PageCount; i++)
        {
            // Print a page number
            Console.WriteLine(string.Format("{0}/{1}", i, pageTextExtractor.PageCount));
            // Extract text from the page
            Console.WriteLine(pageTextExtractor.ExtractPage(i));
        }
    } 
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

## ITextExtractorWithFormatter InterfaceSince version 17.12, we have added a feature that allows you to get or set document formatter via **ITextExtractorWithFormatter** interface. ITextExtractorWithFormatter interface has only one property.```
DocumentFormatter DocumentFormatter { get; set; }
```This property allows you to get or set document formatter of all types of formatted text extractors. Following code sample demonstrates its usage.```
// If the extractor supports ITextExtractorWithFormatter interface
if (extractor is ITextExtractorWithFormatter) {
  // Set MarkdownDocumentFormatter formatter
  (extractor as ITextExtractorWithFormatter).DocumentFormatter = new MarkdownDocumentFormatter;
}
```For more details, please visit [this](https://docs.groupdocs.com/) documentation article.

# GroupDocs.Text for .NET - Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Text:

*   Download - MSI Package or Zipped DLLs Only
*   [NuGet](https://www.nuget.org/packages/groupdocs.text "GroupDocs.Text Nuget Package") - NuGet Package
*   [Documentation](https://docs.groupdocs.com/"GroupDocs.Text Documentation") - Product Docs
*   [Examples](https://github.com/groupdocs-text/GroupDocs.Text-for-.NET "GroupDocs.Text Github repository") - Github Source Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPQyfL8Tkz8XH7yOPhrglb7 "GroupDocs.Text for .NET tutorials") – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/text "GroupDocs.Text for .NET Support forum") – Technical Support Forum for GroupDocs.Text

# Feedback

As always, you are welcome to share your feedback or suggestions to improve this product. Just create a new topic at our [forum](https://forum.groupdocs.com/c/text) and our dedicated support team will be there to respond.




