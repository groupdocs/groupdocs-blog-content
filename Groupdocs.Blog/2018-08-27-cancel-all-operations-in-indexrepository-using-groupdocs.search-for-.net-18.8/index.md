---
title: 'Cancel All Operations in IndexRepository using GroupDocs.Search for .NET 18.8'
date: Mon, 27 Aug 2018 11:50:29 +0000
draft: false
url: /2018/08/27/cancel-all-operations-in-indexrepository-using-groupdocs.search-for-.net-18.8/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Search', 'GroupDocs.Search for .NET', 'GroupDocs.Search for .NET Releases', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net)We are proudly announcing the monthly release of [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net) **18.8**.  Using the latest version, you can now cancel all operations in IndexRepository. We would recommend you to [install](https://www.nuget.org/packages/GroupDocs.Search/) and use the latest version of the API.

# Enhancements

Following are the enhancements introduced in the latest version:

## Breaking functionality for IndexRepository ClassUsing the latest version you can now cancel the operations in all indexes in the index repository. The cancelling is not instantaneous and in cases of operations with large documents, the breaking can take about a second. The following code snippet shows how to break the updating operation:```
 string indexFolder = "c:\\MyIndex\\";
string documentsFolder = "c:\\MyDocuments\\";
  
IndexRepository repository = new IndexRepository();
Index index = repository.Create(indexFolder );
index.AddToIndexAsync(indexFolder);
  
// Breaking all processes in all indexes in repository
repository.Break();
```You can also cancel the operation using Cancellation object. The following code snippet breaks the updating operation with Cancellation object:```
 string documentsFolder = "c:\\MyDocuments\\";
IndexRepository repository = new IndexRepository();
Index index = repository.Create();
index.AddToIndex(documentsFolder);
   
Cancellation cnc = new Cancellation();
   
// Updating all indexes in repository
repository.UpdateAsync(cnc);
   
// Canceling all operations in index repository
cnc.Cancel();
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




