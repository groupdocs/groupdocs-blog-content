---
title: 'Build your Full Text Search Solution in C#'
date: Thu, 03 Jun 2021 00:20:00 +0000
draft: false
url: /2021/06/03/build-your-full-text-search-solution-in-csharp/
aliases:
    - /2019/11/22/build-your-full-text-search-solution-in-csharp/
author: 'Shoaib Khan'
summary: 'Full-text search is basically a more advanced way to search a text/query over a collection of documents. This approach quickly finds all instances of a term and it works by using text indexes. In this article, we will learn, how to programmatically search full-text in documents using C#.

The following topics are discussed in this article:

*   .NET API for Full-Text Search
*   Full-Text Search
*   Perform Search in C#
*   Highlight Search Results

[Continue Reading ...][1]'
tags: ['full text search', 'Full Text Search Csharp']
categories: ['GroupDocs.Search Product Family']
---

Before we leap into the details, let's get an overview of the full-text search technique. Full-text search is basically a more advanced way to search a text/query over a collection of documents. This approach quickly finds all instances of a term and it works by using text indexes. In this article, we will learn, how to programmatically search full-text in documents using C#.

After this, you can implement various search techniques to search text in word-processing documents, spreadsheets, presentations, HTML files, PDF eBooks, email messages, ZIP archives, and many other files.

One of the examples of full-text search implementation is in Word processors and text editors. It helps you to find a phrase or word anywhere in the document.



{{< figure align=center src="images/TextSearch-1.png" alt="Full Text Search">}}


The following topics are covered below:

*   [.NET API for Full-Text Search][2]
*   [Full Text Search][3]
*   [Perform Search in C#][4]
*   [Highlight Search Results][5]

## .NET API for Text Searching {#full-text-search-dotnet-api}

[GroupDocs.Search for .NET][6] is a back-end searching API that allows full-text search and can be integrated into any .NET application without any third-party tool or software dependency. It allows you to [search over a multitude of document formats][7] in your applications.

You can download the **DLLs** or **MSI** installer from the [downloads section][8] or install the API in your .NET application via [NuGet][9].

```
PM> Install-Package GroupDocs.Search
```

## Full Text Search using C# {#full-text-search-in-csharp}

There are two main steps to perform or implement a full-text search.

*   Indexing
*   Perform Search

## Indexing

To make it possible to search instantly across thousands of documents with the same or different file formats, you need to create an index and add these documents to it.

### **What is an index?**

An index possesses scanned text of all the documents. Therefore, when you are going to perform a search operation (search a specific query), only the index is referenced, rather than the text of the original documents.

### **Index creation**

An index can be created in memory or on a disk. The index created in memory cannot be saved after exiting your program. In contrast, an index created on the disk may be loaded in the future to continue working. The following example shows how to create an index on a disk.

```
Index index = new Index("indexPath/FolderName/");
```

When documents are indexed, the index is ready to handle the search queries. The following are some of the search techniques that can be performed using GroupDocs.Search for .NET:

*   Case Sensitive Search
*   Regular Expression Search
*   Phrase Search
*   Faceted Search
*   Synonym Search
*   Wildcard Search

## Perform Search in C# {#perform-search-in-csharp}

Starting with a use case. If we have multiple documents (Word, PDF, Excel, and HTML) and we want to perform a specific search query (search term "video") over them.

The following are the steps for how to perform text search on multiple documents within a folder:

*   Decide source documents folder and index folder.
*   Prepare the query string.
*   Create [Index][10] using the index folder.
*   Add the source documents folder to the index.
*   Perform a search using the [Search][11] method [Index][12] class.
*   Traverse and search results for each document's properties.

The following source code performs a text search using C# on all the documents of the provided folder.

{{< gist GroupDocsGists 9600c1fffefa5e1d0edea71fb209d7a1 "SearchTextInDocs.cs" >}}

We will get the document path and the number of search term occurrences in all the documents available in the document folder. Here is the screenshot to visualize.



{{< figure align=center src="images/SearchTextOutput.jpg" alt="Full Search Text Output">}}


## Highlight Text Search Results in C# {#highlight-search-results-in-csharp}

Let's now perform the same text search, but this time we will highlight all the occurrences that match the query.

The following steps show how to highlight the text search results:

*   Prepare the query string.
*   Create [Index][13] using index folder path.
*   Add the source documents folder to the index.
*   Search the document folder using the [Search][14] method.
*   While traversing the search results, create the [Highlighter][15].
*   Use the [Highlight][16] method of the [Index][17] class to highlight the search results.

The following code generates the HTML output with highlighted search results using C#.

{{< gist GroupDocsGists 9600c1fffefa5e1d0edea71fb209d7a1 "HighlightSearchResults.cs" >}}

As an output, we will get multiple HTML files. Each file will show the content of a different document (e.g. excel.xlsx, source.docx, target.docx) with highlighted search term/word. Given below is the highlighted HTML output of a DOCX file.



{{< figure align=center src="images/highlight-text-search-result.jpg" alt="Highlight full text search results in content">}}


## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][18] in order to use the API without the evaluation limitations.

## Conclusion

In this article, we have learned to search text within multiple documents of a folder using C#. Further, we discussed how to programmatically highlight the text of search results in HTML format.

You may learn more about the API using [documentation][19]. Many more examples are available at [GitHub][20]. For queries, contact us via the [forum][21].

## See Also

*   [Build full-text search solution in Java][22]
*   [Find Synonyms of Words using C#][23]
*   [Search Synonyms in Multiple Files using C#][24]
*   [Find and Replace Text in PDF using C#][25]
*   [Find and Replace Words in Word Documents using C#][26]







[1]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[2]: #full-text-search-dotnet-api
[3]: #full-text-search-in-csharp
[4]: #perform-search-in-csharp
[5]: #highlight-search-results-in-csharp
[6]: https://products.groupdocs.com/search/net
[7]: https://docs.groupdocs.com/search/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/search
[9]: https://www.nuget.org/packages/groupdocs.search
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[12]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[13]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[14]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[15]: https://apireference.groupdocs.com/search/net/groupdocs.search.highlighters/highlighter
[16]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/highlight/index
[17]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[18]: https://purchase.groupdocs.com/temporary-license
[19]: https://docs.groupdocs.com/search/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[23]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[24]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp/
[25]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[26]: https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/

