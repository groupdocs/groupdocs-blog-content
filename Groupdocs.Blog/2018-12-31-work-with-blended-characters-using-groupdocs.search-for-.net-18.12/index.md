---
title: 'Work with Blended Characters using GroupDocs.Search for .NET 18.12'
date: Mon, 31 Dec 2018 07:29:23 +0000
draft: false
url: /2018/12/31/work-with-blended-characters-using-groupdocs.search-for-.net-18.12/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Search', 'GroupDocs.Search for .NET', 'GroupDocs.Search for .NET Releases', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net)We are delighted to announce the monthly release of [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net) **18.12**. Using the latest version, you can now index and search blended characters and perform a wildcard search. We would recommend you to [install](https://www.nuget.org/packages/GroupDocs.Search/) and use the latest version of the API.

# Features

Following are the new features introduced in the latest version:

## Blended Characters SearchGroupDocs.Search for .NET API 18.12 introduces a new class of characters - **blended**. When indexing, blended characters are interpreted simultaneously as valid letters and as separators. For example, if the hyphen is marked as a blended character then indexing of term 'silver-gray' will result in saving of 3 terms in the index: 'silver', 'gray', and 'silver-gray'. The following code snippet shows how to work with blended characters:```
 string indexFolder = @"c:\MyIndex";
string documentFolder = @"c:\MyDocuments";
   
// Creating index
Index index = new Index(indexFolder);
   
// Marking hyphen as blended character
index.Dictionaries.Alphabet.SetRange(new char[] { '-' }, CharacterType.Blended);
   
// Adding documents to index
index.AddToIndex(documentFolder);
   
// Searching for word 'silver-gray'
SearchResults results = index.Search("silver-gray");
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

## Wildcard SearchThe latest version allows performing search of words containing wildcards. There are two possible forms of wildcards to use in wildcard search:

*   ? - question mark representing one arbitrary character
*   ?(N~M) - the range of arbitrary characters in an amount from N to M, where N and M must be in the range from 0 to 255

This following code snippet shows how to perform wildcard search:```
 string indexFolder = @"c:\MyIndex";
string documentFolder = @"c:\MyDocuments";
   
// Creating index
Index index = new Index(indexFolder);
   
// Adding documents to index
index.AddToIndex(documentFolder);
   
// Searching for words 'affect' or 'effect' in a one document with 
// 'principal', 'principle', 'principles', or 'principally'
SearchResults results1 = index.Search("?ffect & princip?(2~4)");
   
// Searching with a single query for phrases 'assure equal opportunities', 
// 'ensure equal opportunities', and 'sure equal opportunities'
SearchResults results2 = index.Search("\"?(0~2)sure equal opportunities\"");
```For more details on this feature, please visit [this](https://docs.groupdocs.com/display/searchnet/Wildcard+Search) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Search:

*   [Installation](https://www.nuget.org/packages/GroupDocs.Search/ "GroupDocs.Search Nuget Package") - Install GroupDocs.Search using NuGet
*   [Documentation](https://docs.groupdocs.com/display/searchnet/Getting+Started "GroupDocs.Search Documentation") - Product docs
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-search/GroupDocs.Search-for-.NET "How to use Search API") - Examples and Open Source Application
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMZGPsZX-FCtRM_UBXdLT9h "Search API video Tutorials") - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/search "GroupDocs.Search Forum") - Technical Support Forum for GroupDocs.Search

# Feedback

If you have any suggestions, questions, or queries related to the [GroupDocs.Search for .NET API](https://products.groupdocs.com/search/net), we will be happy to hear from you. Just create a [forum thread](https://forum.groupdocs.com/c/search) to share your thoughts.




