---
title: 'Search Text in Word, Excel, PDF, ZIP and other Document Formats using C# .NET'
date: Fri, 29 May 2020 09:25:45 +0000
draft: false
url: /2020/05/29/search-text-in-word-excel-pdf-zip-document-formats-using-csharp-net/
author: 'Muhammad Sohail'
summary: 'We often need a full-text search API that enables our applications to search through documents for particular information specified as a textual search query. The documents can be of any format such as Word (Doc, Docx), PDF, HTML, EPUB, Spreadsheet (XLS, XLSX), Presentation (PPT, PPTX), images, and videos.'
tags: ['Full Text Search Csharp', 'Search text in multiple Documents', 'Search text in PDF Document', 'Search text in Word Document']
categories: ['GroupDocs.Search Product Family']
---



{{< figure align=center src="images/Search-Documents.png" alt="Full text search of documents">}}


We often need a full-text search API that enables our applications to search through documents for particular information specified as a textual search query. The documents can be of any format such as Word (Doc, Docx), PDF, HTML, EPUB, Spreadsheet (XLS, XLSX), Presentation (PPT, PPTX), images, and videos.

[GroupDocs.Search][1] is a powerful full-text search API that allows you to search through [over 70 document formats][2] in your applications. To make it possible to search instantly across thousands of documents, they must be added to the index.

## Why Use GroupDocs.Search as a Developer?

*   No additional software is required to search through documents of supported formats.
*   Great variety of indexing and search options are provided to meet any requirements.
*   A wide selection of search types is available in text or object form queries.
*   High indexing and search performance is achieved by unique algorithms and data structures, optimizations and multi-threaded execution.
*   Various ways of visualizing search results in the text of documents are supported.

Please check [About Search Engines][3] article to know what place GroupDocs.Search API occupies in the classification of search engines.

## Installation

GroupDocs.Search for .NET is hosted on [NuGet][4] and can easily be installed using the NuGet Package Manager. Alternatively, you can download the API’s DLL from the [Downloads][5] section.

## Search Through Office Documents using C#

The following steps explain how to search words or phrases in multiple documents (Word, Excel, PDF and other document formats).

*   **Create a new index**: First of all, you need to create an index. An index can be created in memory or on disk. An index created in memory cannot be saved after exiting your program. In contrast, an index created on disk may be loaded in the future to continue working. Details on creating an index are described in the section [Creating an index][6].
*   **Subscribe to index events:** After creating an index, you need to add documents to the index for indexing. Indexing documents can be successful or unsuccessful for various reasons, for example, due to read errors from the disk or the presence of a password to access a document. To receive information about indexing errors, you can subscribe to the ErrorOccurred event. To work with events, see the section [Search index events][7].
*   **Index Documents**: Document indexing can be performed synchronously or asynchronously. Synchronous indexing means that a thread that started the indexing process will be busy until the operation is completed. However, more often, it is necessary to perform indexing asynchronously, with the ability to execute other tasks in the thread that launched the operation. A detailed description of all aspects of the indexing process is provided in section [Indexing][8].
*   **Perform search:** When documents are indexed, the index is ready to handle search queries. The following types of search queries are supported: simple, fuzzy, case sensitive, boolean, phrasal, faceted, with wildcards, and others. Description of search queries of various types is presented in the section [Searching][9].
*   **Use search results:** When a search is completed, you need to somehow interpret a result. The result can be represented by a simple list of documents found, or the words and phrases found can be highlighted in the text of the document. For more information on processing search results, see [Search results][10].

```
string indexFolder = @"/Users/muhammadsohailismail/MyIndex/"; // Specify the path to the index folder
string documentsFolder = @"/Users/muhammadsohailismail/MyDocuments/"; // Specify the path to a folder containing documents to search

// a) Create new index or
// b) Open existing index
Index index = new Index(indexFolder);

// c) Subscribe to index events
index.Events.ErrorOccurred += (sender, args) =>
{
    Console.WriteLine(args.Message); // Writing error messages to the console
};

// d) Add files synchronously
index.Add(documentsFolder); // Synchronous indexing documents from the specified folder

// f) Perform search
string query = "Worthy"; // Specify a search query
SearchResult result = index.Search(query); // Searching in the index

// g) Use search results
// Printing the result
Console.WriteLine("Documents found: " + result.DocumentCount);
Console.WriteLine("Total occurrences found: " + result.OccurrenceCount);
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("\\tDocument: " + document.DocumentInfo.FilePath);
    Console.WriteLine("\\tOccurrences: " + document.OccurrenceCount);
}

// Highlight occurrences in text
if (result.DocumentCount > 0)
{
    FoundDocument document = result.GetFoundDocument(0); // Getting the first found document
    string path = @"/Users/muhammadsohailismail/Output/Highlighted.html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); // Creating the output adapter to a file
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter); // Creating the highlighter object
    index.Highlight(document, highlighter); // Generating output HTML formatted document with highlighted search results

    Console.WriteLine();
    Console.WriteLine("Generated HTML file can be opened with Internet browser.");
    Console.WriteLine("The file can be found by the following path:");
    Console.WriteLine(Path.GetFullPath(path));
}
```

The above code generates the following output and [HTML file][11].



{{< figure align=center src="images/Output.jpg" alt="">}}


## Search in Fields of Documents using C#

Faceted search is filtering of search results by setting valid document field names to search. Faceted search allows you to search only in certain fields of documents, for example, only in the content field or in the file name field. A simple faceted search example is presented below with queries in text and object form.

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.Add(documentsFolder);
 
// Search in the content field with text query
SearchResult result1 = index.Search("content: Einstein");
 
// Search in the content field with object query
SearchQuery wordQuery = SearchQuery.CreateWordQuery("Einstein");
SearchQuery fieldQuery = SearchQuery.CreateFieldQuery(CommonFieldNames.Content, wordQuery);
SearchResult result2 = index.Search(fieldQuery);
```

### Using format specific fields

For each document format, there are standard fields that may be present in documents of this type. The library provides the following classes containing constants with the names of standard document fields: [EpubFieldNames][12], [FictionBookFieldNames][13], [MailFieldNames][14], [PresentationFieldNames][15], [SpreadsheetFieldNames][16], [WordsFieldNames][17].

There are also fields that may be present in documents of any type. The names of such fields are represented in the [CommonFieldNames][18] class.

An example of using standard field names of documents is presented in the following example.

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.Add(documentsFolder);
 
// Search in the content field with text query
string query1 = WordsFieldNames.Company + ": Dycum";
SearchResult result1 = index.Search(query1);
 
// Search in the content field with object query
SearchQuery wordQuery = SearchQuery.CreateWordQuery("Dycum");
SearchQuery fieldQuery = SearchQuery.CreateFieldQuery(WordsFieldNames.Company, wordQuery);
SearchResult result2 = index.Search(fieldQuery);
```

Detailed information about faceted search is presented on the page [Faceted search][19].

## Conclusion

This article has explained how to search through documents (DOCX, PDF, Excel, Text files) for particular information in C#. It also explained how to search in the fields of documents. GroupDocs.Search contains several other features, please check the [documentation][20] to learn more about it.







[1]: https://products.groupdocs.com/search
[2]: https://docs.groupdocs.com/display/searchnet/Supported+Document+Formats
[3]: https://docs.groupdocs.com/display/searchnet/About+Search+Engines
[4]: https://www.nuget.org/packages/GroupDocs.Search/
[5]: https://downloads.groupdocs.com/search/net
[6]: https://docs.groupdocs.com/display/searchnet/Creating+an+index
[7]: https://docs.groupdocs.com/display/searchnet/Search+index+events
[8]: https://docs.groupdocs.com/display/searchnet/Indexing
[9]: https://docs.groupdocs.com/display/searchnet/Searching
[10]: https://docs.groupdocs.com/display/searchnet/Search+results
[11]: https://www.dropbox.com/s/ioztnalgq2fjqcs/Highlighted.html?dl=0
[12]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/epubfieldnames
[13]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/fictionbookfieldnames
[14]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/mailfieldnames
[15]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/presentationfieldnames
[16]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/spreadsheetfieldnames
[17]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/wordsfieldnames
[18]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/commonfieldnames
[19]: https://docs.groupdocs.com/display/searchnet/Faceted+search
[20]: https://docs.groupdocs.com/display/searchnet/Developer+Guide

