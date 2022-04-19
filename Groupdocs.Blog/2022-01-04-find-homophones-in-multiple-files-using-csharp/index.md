---
title: 'Find Homophones in Multiple Files using C#'
date: Tue, 04 Jan 2022 10:54:00 +0000
draft: false
url: /2022/01/04/find-homophones-in-multiple-files-using-csharp/
author: 'Shoaib Khan'
summary: 'Words that sound the same but are different in meanings or spellings are **Homophones**. Whereas, the words that spell the same, but differ in meaning or pronunciation are **Homographs**. **Homonyms** can either be homophone or homograph; or both. Let us not confuse and automate it. In this article, you will learn **how to search homophones within multiple documents using C#**.'
tags: ['Find Homophones', 'Find Homophones in CSharp', 'Find Homophones in Files', 'Homophones']
categories: ['GroupDocs.Search Product Family']
---

Words that sound the same but are different in meanings or spellings are **Homophones**. Whereas, the words that spell the same, but differ in meaning or pronunciation are **Homographs**. **Homonyms** can either be homophone or homograph; or both. Let's not confuse and automate it. In this article, you'll learn **how to search homophones within multiple documents using C#**.



{{< figure align=center src="images/Search-Homophones-in-Files.jpg" alt="Search Homophones in Files using GroupDocs">}}


The following topics will be covered below:

*   [.NET API - Homophone Search](#homophone-search-dotnet-api)
*   [Find homophones in documents using C#](#homophone-in-different-files)
*   [Play with Homophone Search Result](#print-homophone-search)

## .NET API for Searching Homophones in Multiple Files {#homophone-search-dotnet-api}

[GroupDocs.Search](https://products.groupdocs.com/search/) showcases the .NET API ([GroupDocs.Search for .NET](https://products.groupdocs.com/search/net/)) that allows searching words and their homophones within multiple files of the specified folder. We will use this API in the examples of this article. It can search the content of various different formats. Along with finding the homophones, the API supports many other ways to search as per requirement. Some of the supported search techniques are as follows:

*   Synonym Search
*   Phrase Search
*   Fuzzy Search
*   Case-Sensitive Search
*   Regular Expressions Search
*   Wild Card Search

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/search) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.search).

```
PM> Install-Package GroupDocs.Search
```

## Find Homophones in Multiple Files using C# {#homophone-in-different-files}

The following steps guide how we can search homophones (words with similar sound/pronunciation) in files within a folder using C#.

*   Define the search query, an indexing folder, and the folder that contain your files.
*   Create [Index](https://apireference.groupdocs.com/search/net/groupdocs.search/index) with the defined index folder.
*   Add the document's folder to the created index.
*   Define the [SearchOptions](https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions) and set the [UseHomophoneSearch](https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usehomophonesearch) to true.
*   Search all the homophones by calling [Search](https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index) method with the query and search options.
*   Use the summary using the properties of the retrived [SearchResult](https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult).

The following C# source code finds all the homophones within all the files of a defined folder. Additionally, you can [manage your homophone dictionary](https://docs.groupdocs.com/search/net/homophone-dictionary/).

{{< gist GroupDocsGists 388847f8f9945aa267bfdf8c014b5e28 "SearchHomophoneInFilesAndFolders.cs" >}}

The output of the above code is as follows:

```
Query: **right**
Documents: 2
Occurrences: 17
```

## Printing Homophone Search Results using C# {#print-homophone-search}

Follow the below-mentioned steps after getting all the homophones and their number of occurrences in each document to present the homophone search results.

*   Traverse the homophone search results that are retrieved earlier.
*   Get each document as [FoundDocument](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument) using the [GetFoundDocument()](https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument) method.
*   Use the properties of each FoundDocument as required.
*   Now, traverse the [FoundFields](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/foundfields) of FoundDocument to get [FoundDocumentField](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocumentfield).
*   Lastly, from each FoundDocumentField, get its Terms and their occurrences within each document.

The following C# source code prints the homophone search results along with the number of occurrences of each searched term.

{{< gist GroupDocsGists 388847f8f9945aa267bfdf8c014b5e28 "PrintingHomophoneSearchResults.cs" >}}

The following is the output of the above code example.

```
Query: **right**
Documents: 2
Total occurrences: 17

Document: C:/documents/sample.docx
Occurrences: 11
    Field: content
    Occurrences: 11
        right             3
        rite               4
        wright           1
        write             3
Document: C:/documents/sample.txt
Occurrences: 6
    Field: content
    Occurrences: 6
        right             4
        write             2
```

## Search Homophones and Printing Results using C# - Complete Code {#search-and-print-synonyms-code}

The following C# code sums up the above steps, it first finds all the homophones according to the query, and then prints all the occurrences of all the homophones in each document within the provided folder.

{{< gist GroupDocsGists 388847f8f9945aa267bfdf8c014b5e28 "SearchHomophonesAndPrintResults.cs" >}}

## Conclusion

To sum up, you have learned how to find the words and their homophones from the multiple documents of the specified folder using C#. You can try building your own .NET application for searching homophones within multiple files using **GroupDocs.Search for .NET**.

Learn more [about the .NET Search Automation API](https://docs.groupdocs.com/search/net/) from the documentation. To experience the features, you can have a look at available examples on the [GitHub](https://github.com/groupdocs-search) repository. Reach us for any query via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Find Synonyms of Words using C#](https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp)
*   [Build your Full-Text Search Solution in C#](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)
*   [Text Indexing and Search your Directories using C#](https://blog.groupdocs.com/2020/05/29/search-text-by-indexing-in-csharp-net/)




