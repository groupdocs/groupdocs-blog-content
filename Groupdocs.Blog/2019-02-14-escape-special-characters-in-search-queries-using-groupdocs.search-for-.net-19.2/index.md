---
title: 'Escape Special Characters in Search Queries using GroupDocs.Search for .NET 19.2'
date: Thu, 14 Feb 2019 08:00:09 +0000
draft: false
url: /2019/02/14/escape-special-characters-in-search-queries-using-groupdocs.search-for-.net-19.2/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Search for .NET', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net)We are pleased to announce the monthly release of GroupDocs.Search for .NET 19.2. Improvements such as indexing of a ZIP archive inside other ZIP and escape of special characters in search queries are introduced. Please check GroupDocs.Search for .NET 19.2 [release notes](https://docs.groupdocs.com/display/searchnet/GroupDocs.Search+for+.NET+19.2+Release+Notes) for further reference. We would recommend you to [download](https://www.nuget.org/packages/GroupDocs.Search/) and integrate latest version of the API.

# Breaking Change

*   Removed obsolete methods Import and Export from dictionary classes

# Improvements

Following improvements are introduced in this release:

## Implement escaping special characters in search queries```
string indexFolder = @"c:\MyIndex";
string documentFolder = @"c:\MyDocuments";
// Creating index
Index index = new Index(indexFolder);
// Marking character '&' as a valid letter, not a separator
index.Dictionaries.Alphabet.SetRange(new char[] { '&' }, CharacterType.Letter);
// Adding documents to index
index.AddToIndex(documentFolder);
// Searching for word 'R&B'
SearchResults results0 = index.Search(@"R\&B");
// Searching for word 'R&B'
SearchResults results1 = index.Search(@"R\u0026B");
```

## Indexing ZIP archives inside other ZIP archives```
string indexFolder = @"c:\MyIndex";
string documentFolder = @"c:\MyDocuments";
// Creating index
Index index = new Index(indexFolder);
// Adding documents to index
// ZIP archives and ZIP archives inside those archives will be automatically added to index
index.AddToIndex(documentFolder);
// Searching
SearchResults results = index.Search("zip");
```

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Search:

*   [Installation](https://www.nuget.org/packages/GroupDocs.Search/ "GroupDocs.Search Nuget Package") - Install GroupDocs.Search using NuGet
*   [Documentation](https://docs.groupdocs.com/display/searchnet/Getting+Started "GroupDocs.Search Documentation") - Product docs
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET "How to use Search API") - Examples and Open Source Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMZGPsZX-FCtRM_UBXdLT9h "Search API video Tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/search "GroupDocs.Search Forum") - Technical Support Forum for GroupDocs.Search

# Feedback

If you have any suggestions, questions, or queries related to the [GroupDocs.Search for .NET API](https://products.groupdocs.com/search/net), we will be happy to hear from you. Just create a [forum thread](https://forum.groupdocs.com/c/search) to share your thoughts.




