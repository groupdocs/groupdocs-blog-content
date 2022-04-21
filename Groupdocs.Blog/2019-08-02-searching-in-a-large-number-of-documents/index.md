---
title: 'Searching in a Large Number of Documents'
date: Fri, 02 Aug 2019 13:16:23 +0000
draft: false
url: /2019/08/02/searching-in-a-large-number-of-documents/
author: 'Muhammad Umar'
summary: ''
tags: ['Facet Search', 'Fuzzy', 'GroupDocs', 'Indexing', 'lucene', 'search api', 'Searching', 'Stop Words']
categories: ['GroupDocs.Search', 'GroupDocs.Search Product Family']
---

Usually, a searching software is able to achieve fast search responses because, instead of search the text directly, it searches an index. This would be the equivalent of retrieving pages in a book related to a keyword by searching the index at the back of a book, as opposed to searching the words in each page of the book.

## Using GroupDocs.Search for Indexing and Searching

**Problem:** Suppose you have 10 million documents of different file formats, e.g. MS Word, Spreadsheets, Presentations, etc. Due to limited memory size, you cannot store more than 5% of the entire data. Now the main issue is how to apply indexing and searching in this case.

**Solution:** The GroupDocs.Search for .NET provides many ways to perform search operations on any size of document collections. It is capable in indexing various types of documents and perform searches on it. The API supports searching for:

*   Text occurrences
*   Basic metadata fields
*   File names
*   Document types

Moreover, it allows searching on the basis of different search query types. The advanced search (e.g fuzzy search, synonyms search, boolean search) is also supported.

### Creating Index

Let's try the GroupDocs.Search API for indexing the bulk of documents of different file formats(see the [supported formats](https://docs.groupdocs.com/display/searchnet/Supported+Document+Formats) list). Although, the Index can be created in memory, but here, let's create it on disk. You just need to follow these simple steps:

*   Create a directory for Indexing
*   Create another directory and copy all the required documents into it.
*   Come to the code and firstly initialize _Index_ object by passing the path of the index directory
*   Add documents using _AddToIndex("Documents\_Folder\_Path")_ method of Index object.

The C# code will look like this:

{{< gist GroupDocsGists 2365b860d1cddfdc424ab2ca744f8519 "Examples-CSharp-GroupDocs.Search.Examples.CSharp-Indexing-AddDocumentToIndex.cs" >}}

Java guys can write the code like this:

{{< gist GroupDocsGists 0b3dd7b17f9896c5a7d4edf63c6f3bc2 "addDocumentToIndex.java" >}}

After creating Index you will see the files in the Index folder like following screenshot:



{{< figure align=center src="images/6nPzno7.png" alt="">}}


### Searching The Terms

The GroupDocs.Search allows various kinds of queries for search operations with more advance features. Please see [this article](https://docs.groupdocs.com/search/net) for the detail.

Lets come to the code.

Suppose, the index has been already created as described in the above section. Let's simply search a term. Follow the steps as written below:

*   Instantiate _Index _by passing index folder path
*   Search the term using _Index.Search()_ method which will return _SearchResults_ object.
*   Show list of searched files

The C# code will look like:

{{< gist GroupDocsGists a378fe664de1d55d7fed530fa6c1ce15 "SearchBooksInExistingIndex.cs" >}}

Java developers can write the code like this:

{{< gist GroupDocsGists 464009c05863cf8c7cadea997cd8735c "searchBooksInExistingIndex.java" >}}

The output will be appeared like the following screenshot:



{{< figure align=center src="images/i9lD6YE.png" alt="">}}


The complete ready to run code sample is available on [GitHub](https://github.com/groupdocs-search).




