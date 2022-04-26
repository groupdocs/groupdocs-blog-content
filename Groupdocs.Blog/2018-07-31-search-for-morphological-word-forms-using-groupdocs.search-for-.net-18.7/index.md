---
title: 'Search for Morphological Word Forms using GroupDocs.Search for .NET 18.7'
date: Tue, 31 Jul 2018 07:48:09 +0000
draft: false
url: /2018/07/31/search-for-morphological-word-forms-using-groupdocs.search-for-.net-18.7/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Search', 'GroupDocs.Search for .NET', 'GroupDocs.Search for .NET Releases', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net)We are proudly announcing the monthly release of [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net) **18.7**. Using the latest version, you can search for morphological word forms. Furthermore, you can now break updating, merging and indexing operations manually. We would recommend you to [install](https://www.nuget.org/packages/GroupDocs.Search/) and use the latest version of API.

# Enhancements

Following are the enhancements introduced in the latest version:

## Search for Morphological Word FormsThe latest version of API allows you to search for singular and plural forms of a noun at the same time. You can also search for all existing forms of a verb at the same time: root, third-person singular, present participle, simple past, and past participle. Following code snippet shows how to search for morphological word forms:```
string folderForIndex = "c:\\MyIndex\\";
string folderWithDocuments = "c:\\MyDocuments\\";
Index index = new Index(folderForIndex); 
index.AddToIndex(folderWithDocuments);
SearchParameters parameters = new SearchParameters();
parameters.UseWordFormsSearch = true;
//Searching for words "simplest", "simple", and "simpler"
SearchResults results1 = index.Search("simplest", parameters);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

## Break Updating Operation ManuallyUsing v18.7, you can cancel the updating operation by request and for time limitation of indexing. Following code snippets show how to break updating operation:

### Break Updating Operation```
string indexFolder = @"c:\MyIndex";
Index index = new Index(indexFolder);
index.UpdateAsync();
index.Break();
```

### Break Updating Operation using Cancellation Object```
string indexFolder = @"c:\MyIndex";
Cancellation cancellation = new Cancellation();
Index index = new Index(indexFolder);
index.UpdateAsync(cancellation);
cancellation.Cancel();
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

## Break Merging Operation ManuallyUsing the latest version, you can cancel the merging operation by request. Following code snippet shows how to break merging operation:```
string indexFolder = @"c:\MyIndex";
string documentsFolder = @"c:\MyDocuments";
Cancellation cancellation = new Cancellation();
cancellation.CancelAfter(5000);
Index index = new Index(indexFolder);
index.Merge(cancellation);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

## Break Indexing Operation using Cancellation ObjectThe latest version also allows you to cancel the indexing operation by request and for time limitation of indexing. Following code snippet shows how to break indexing operation:```
string indexFolder = @"c:\MyIndex";
string documentsFolder = @"c:\MyDocuments";
Cancellation cancellation = new Cancellation();
Index index = new Index(indexFolder);
index.AddToIndexAsync(documentsFolder, cancellation);
Thread.Sleep(1000);
cancellation.Cancel();
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Search:

*   [Installation](https://www.nuget.org/packages/GroupDocs.Search/ "GroupDocs.Search Nuget Package") - Install GroupDocs.Search using NuGet
*   [Documentation](https://docs.groupdocs.com/display/searchnet/Getting+Started "GroupDocs.Search Documentation") - Product docs
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET "How to use Search API") - Examples and Open Source Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMZGPsZX-FCtRM_UBXdLT9h "Search API video Tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/search "GroupDocs.Search Forum") - Technical Support Forum for GroupDocs.Search

# Feedback

If you have any suggestions, questions, or queries related to the [GroupDocs.Search for .NET API](https://products.groupdocs.com/search/net), we will be happy to hear from you. Just create a [forum thread](https://forum.groupdocs.com/c/search) to share your thoughts.




