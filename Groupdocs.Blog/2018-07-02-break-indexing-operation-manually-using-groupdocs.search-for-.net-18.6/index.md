---
title: 'Break Indexing Operation Manually using GroupDocs.Search for .NET 18.6'
date: Mon, 02 Jul 2018 10:00:04 +0000
draft: false
url: /2018/07/02/break-indexing-operation-manually-using-groupdocs.search-for-.net-18.6/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Search', 'GroupDocs.Search for .NET', 'GroupDocs.Search for .NET Releases', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net)GroupDocs team is pleased to announce the monthly release of [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net) **18.6**. Using the latest version, you can now break indexing operation manually. Furthermore, obsolete Relevance property is removed from the DetailResultInfo method and ImportDictionary and ExportDictonary methods are added to index dictionaries. We would recommend you to [install](https://www.nuget.org/packages/GroupDocs.Search/) and use the latest version of API.

## Break Indexing Operation ManuallyUsing GroupDocs.Search API you can break indexing operation manually. The break is not instantaneous and in cases of indexing large documents, the breaking can take about a second. Following is the code snippet to break indexing operation manually:```
string folderForIndex = "c:\\MyIndex\\";
string folderWithDocuments = "c:\\MyDocuments\\";

//Creating index
Index index = new Index(folderForIndex);

//Subscribing on Operation Finished event
index.OperationFinished += index_OperationFinished;

//Indexing selected folder asynchronously
index.AddToIndexAsync(folderWithDocuments);

//Breaking indexing
index.Break(); 
```

## Added ImportDictionary and ExportDictionary methods to index dictionariesIn the latest version of API, Import and Export methods' names are updated to ImportDictonaires and ExportDictionaries.

## Removed obsolete Relevance property from DetailedResultInfoObsolete property GroupDocs.Search.DetailedResultInfo.Relevance is removed from DetailResultInfo in version 18.6 of GroupDocs.Search for .NET API.

## Available Channels and ResourcesHere are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Search:

*   [Installation](https://www.nuget.org/packages/GroupDocs.Search/ "GroupDocs.Search Nuget Package") - Install GroupDocs.Search using NuGet
*   [Documentation](https://docs.groupdocs.com/display/searchnet/Getting+Started "GroupDocs.Search Documentation") - Product docs
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET "How to use Search API") - Examples and Open Source Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMZGPsZX-FCtRM_UBXdLT9h "Search API video Tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/search "GroupDocs.Search Forum") - Technical Support Forum for GroupDocs.Search

## FeedbackIf you have any suggestions, questions, or queries related to the [.NET Search API](https://products.groupdocs.com/search/net), we will be happy to hear from you. Just create a [forum thread](https://forum.groupdocs.com/c/search) to share your thoughts.




