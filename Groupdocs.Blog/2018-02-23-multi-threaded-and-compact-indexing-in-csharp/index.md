---
title: 'Multi-Threaded &amp; Compact Indexing with Less Storage'
date: Fri, 23 Feb 2018 02:32:24 +0000
draft: false
url: /2018/02/23/multi-threaded-and-compact-indexing-in-csharp/
aliases:
    - /2018/02/23/multi-threaded-indexing-in-groupdocs.search-for-.net-18.2/
author: 'Ali Ahmed'
summary: ''
tags: ['.NET Text Searching API', 'compact indexing', 'compact indexing in csharp', 'indexing in csharp', 'multi-threaded indexing', 'multi-threaded indexing in csharp']
categories: ['GroupDocs.Search Product Family']
---



{{< figure align=center src="images/groupdocs-annotation-net.png" alt="GroupDocs.Search for .NET">}}


GroupDocs team is pleased to announce three enhancements in [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net) **18.2**. Using the latest version, you can now perform indexing in multiple threads using multi-threaded indexing. Furthermore, you can now implement compact indexing that consumes up to 5 times less disk space. We would recommend you to [download](https://downloads.groupdocs.com/search/net/new-releases/groupdocs.search-for-.net-18.2/) the latest version for better user experience.

## Multi-Threaded Indexing in C#

In this enhancement, you can perform indexing in multiple threads. Multi-threaded indexing is faster but uses more memory and may cause memory overflow error. If you have only 8 GB of RAM installed, it is recommended to use not more than 2 threads for indexing. If you have 16 GB of RAM installed, you can use 4 threads for indexing. Following code sample shows how to use multi-threaded indexing.

```
string indexFolder = @"c:\\MyIndex";
string documentsFolder = @"c:\\MyDocuments";
 
// Creating index
Index index = new Index(indexFolder);
 
// Indexing in 2 threads
index.AddToIndex(documentsFolder, 2);
 
// Searching
SearchResults result = index.Search("Einstein");
```

You can also run multi-threaded indexing using the asynchronous method as shown in the following code sample.

```
string indexFolder = @"c:\\MyIndex";
string documentsFolder = @"c:\\MyDocuments";
 
// Creating index
Index index = new Index(indexFolder);
 
// Indexing in 2 threads
index.AddToIndexAsync(documentsFolder, 2);
 
// User can perform a search after the completion of the indexing operation
```

## Compact Indexing

This enhancement allows you to create an index that consumes up to 5 times less disk space. This is possible for the reason of containing only number of word occurrences without positions. For the same reason, index of this type does not support phrase search and date range search.

```
string indexFolder = @"c:\\MyIndex";
string documentsFolder = @"c:\\MyDocuments";
 
// Creating indexing settings object
IndexingSettings indexingSettings = new IndexingSettings();
// Setting compact index type
indexingSettings.IndexType = IndexType.CompactIndex;
 
// Creating index
Index index = new Index(indexFolder, indexingSettings);
 
// Indexing
index.AddToIndex(documentsFolder);
 
// Searching
SearchResults result = index.Search("Einstein");
```

## Improved Index Structure to Increase Indexing Speed

This enhancement is implemented to increase indexing performance. As a result, the performance of single-threaded indexing has been improved by around 8%.

## Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Search:

*   [Download](https://downloads.groupdocs.com/search/net "GroupDocs.Search MSI") - MSI Package
*   [NuGet](https://www.nuget.org/packages/GroupDocs.Search "GroupDocs.Search Nuget Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/display/searchnet/Getting+Started) - API docs
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET "How to use Search API") - Examples and Open Source Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMZGPsZX-FCtRM_UBXdLT9h "Search API video Tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/search) - Technical Support Forum for GroupDocs.Search

## Feedback

If you have any suggestions, questions, or queries related to the [.NET Search API](https://products.groupdocs.com/search/net), we will be happy to hear from you. Just create a [forum thread](https://forum.groupdocs.com/c/search) to share your thoughts.




