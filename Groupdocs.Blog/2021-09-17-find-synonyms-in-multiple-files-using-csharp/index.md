---
title: "Search Synonyms in Multiple Files using C#"
seoTitle: "Find any Word and its Synonyms in Multiple Files using C#"
description: "Find specific words and their synonyms within different files of a folder using C#. Get all the synonyms, grouped by different meanings using .NET API."
date: Fri, 17 Sep 2021 10:57:00 +0000
draft: false
url: /2021/09/17/find-synonyms-in-multiple-files-using-csharp/
author: 'Shoaib Khan'
summary: "In an other article we have seen that what are synonyms, and how to get all the synonyms of any word. What about find these synonyms with in different documents. This article will guide you about how to search the synonyms of any specific query (word) in multiple files using C#."
tags: ['Find Synonyms', 'Find Synonyms in CSharp', 'Search Synonyms', 'Search Synonyms in CSharp', 'Search Synonyms in Files']
categories: ['GroupDocs.Search Product Family']
---

In another article, we have seen that what are synonyms, and [how to get all the synonyms of any word][1]. What about finding these synonyms within different documents? This article will guide you about how to search the synonyms of any specific query (word) in multiple files using C#.

The following topics will be covered below:

*   [.NET API - Synonym Search][2]
*   [Find synonyms in documents using C#][3]
*   [Present synonym search results using C#][4]
*   [Complete code - Search & print synonyms search results][5]

## .NET API for Searching Synonyms in Multiple Files {#synonym-search-dotnet-api}

[GroupDocs.Search][6] provides the .NET API that allows searching any word and its synonyms in multiple files of the specified folder. I will be using this API in the shown examples of this article. It allows you to [search over a large list of document formats][7]. Along with finding the synonyms, GroupDocs.Search for .NET also supports some more search techniques that include:

*   Fuzzy Search
*   Case-Sensitive Search
*   Homophone Search
*   Regular Expressions Search
*   Wild Card Search

You can download the **DLLs** or **MSI** installer from the [downloads section][8] or install the API in your .NET application via [NuGet][9].

```
PM> Install-Package GroupDocs.Search
```

## Find Synonyms in Multiple Files using C# {#synonyms-in-different-files}

The steps show how to search synonyms (words with similar meanings) in files within a folder using C#.

*   Define the search query, index folder, and the document's folder.
*   Create index with defined index Folder using [Index][10] class.
*   Add the document's folder to the index.
*   Create the [SearchOptions][11] and set the [UseSynonymSearch][12] to true.
*   Call the [Search][13] method of Index class and pass the query and search options.
*   To print the summary, use the properties of the retrived [SearchResult][14].

The source code shows how to find all the synonyms within all the files of a folder using C#

{{< gist GroupDocsGists a58dbce63ea1a37b97dbdb5b3a8a0a88 "SearchSynonymsInFilesAndFolders.cs" >}}

```
Query: **make**
Documents: 2
Occurrences: 22
```

## Printing Synonym Search Results using C# {#print-synonym-search}

The following steps print the results in detail after getting all the synonyms and their number of occurrences in each document.

*   Traverse the search results that are retrieved using the above code.
*   Get each [FoundDocument][15] using the [GetFoundDocument][16] method.
*   Print the repective properties of each FoundDocument.
*   Traverse the [FoundFields][17] within each FoundDocument to get [Found Document Field][18].
*   From each FoundDocumentField, you can get its terms and its occurrences count within each document.

The following source code prints the synonym search results along with the number of occurrences of each searched term using C#.

{{< gist GroupDocsGists a58dbce63ea1a37b97dbdb5b3a8a0a88 "PrintingSearchResults.cs" >}}

```
Query: **make**
Documents: 2
Total occurrences: 22

Document: C:/documents/sample.docx
Occurrences: 6
    Field: content
    Occurrences: 6
        make             1
        get                 2
        cause            1
        do                  2
Document: C:/documents/sample.txt
Occurrences: 16
    Field: content
    Occurrences: 16
        get                  4
        cause             1
        do                  11
```

## Search Synonyms and Printing Results using C# - Complete Code {#search-and-print-synonyms-code}

Here is the complete source code that first finds all the synonyms according to the provided query, and then prints all the occurrences of all the synonyms in each document within that folder using C#.

{{< gist GroupDocsGists a58dbce63ea1a37b97dbdb5b3a8a0a88 "SearchSynonymsAndPrintResults.cs" >}}

## Conclusion

To conclude, you have learned how to find the specific words and also their synonyms in multiple documents within the specified folder using C#. You can try to develop your own .NET application for searching any word and its synonyms within multiple files.

Learn more [about the .NET Search Automation API][19] from the documentation. To experience the features, you can have a look at examples on the [GitHub][20] repository. Reach us for any query via the [forum][21].

## See Also

*   [Find Synonyms of Words using C#][22]
*   [Build your Full-Text Search Solution in C#][23]
*   [Text Indexing and Search your Directories using C#][24]







[1]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp
[2]: #synonym-search-dotnet-api
[3]: #synonyms-in-different-files
[4]: #print-synonym-search
[5]: #search-and-print-synonyms-code
[6]: https://products.groupdocs.com/search/
[7]: https://docs.groupdocs.com/search/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/search
[9]: https://www.nuget.org/packages/groupdocs.search
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions
[12]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usesynonymsearch
[13]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[14]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult
[15]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument
[16]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument
[17]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/foundfields
[18]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocumentfield
[19]: https://docs.groupdocs.com/search/net/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp
[23]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[24]: https://blog.groupdocs.com/2020/05/29/search-text-by-indexing-in-csharp-net/

