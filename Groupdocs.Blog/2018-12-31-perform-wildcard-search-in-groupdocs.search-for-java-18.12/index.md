---
title: 'Perform Wildcard Search in GroupDocs.Search for Java 18.12'
date: Mon, 31 Dec 2018 07:31:24 +0000
draft: false
url: /2018/12/31/perform-wildcard-search-in-groupdocs.search-for-java-18.12/
author: 'Ali Ahmed'
summary: ''
tags: ['GroupDocs.Search', 'GroupDocs.Search for Java', 'GroupDocs.Search for Java Releases']
categories: ['GroupDocs.Search Product Family']
---

[![GroupDocs.Search for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/10/groupdocs.search-for-java-90x90.png)](https://products.groupdocs.com/search/java)We are pleased to announce the monthly release of [GroupDocs.Search for Java](https://products.groupdocs.com/search/java "GroupDocs.Search product page") **18.12**. Using the latest version, you can now index and search blended characters and perform a wildcard search. We would recommend you to [install](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-search) and use the latest version of the API.

# Features

Following are the new features introduced in the latest version:

## Blended Characters SearchGroupDocs.Search for Java API 18.12 introduces a new class of characters - **blended**. When indexing, blended characters are interpreted simultaneously as valid letters and as separators. For example, if the hyphen is marked as a blended character then indexing of term 'silver-gray' will result in saving of 3 terms in the index: 'silver', 'gray', and 'silver-gray'. The following code snippet shows how to work with blended characters:```
 String indexFolder = "c:\\MyIndex";
String documentFolder = "c:\\MyDocuments";
  
// Creating index
Index index = new Index(indexFolder);
  
// Marking hyphen as blended character
index.getDictionaries().getAlphabet().setRange(new char[] { '-' }, CharacterType.Blended);
  
// Adding documents to index
index.addToIndex(documentFolder);
  
// Searching for word 'silver-gray'
SearchResults results = index.search("silver-gray");
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/java/) documentation article.

## Wildcard SearchThe latest version allows performing search of words containing wildcards. There are two possible forms of wildcards to use in wildcard search:

*   ? - question mark representing one arbitrary character
*   ?(N~M) - the range of arbitrary characters in an amount from N to M, where N and M must be in the range from 0 to 255

The following code snippet shows how to perform wildcard search:```
 String indexFolder = "c:\\MyIndex";
String documentFolder = "c:\\MyDocuments";
  
// Creating index
Index index = new Index(indexFolder);
  
// Adding documents to index
index.addToIndex(documentFolder);
  
// Searching for words 'affect' or 'effect' in a one document with 
// 'principal', 'principle', 'principles', or 'principally'
SearchResults results1 = index.search("?ffect & princip?(2~4)");
  
// Searching with a single query for phrases 'assure equal opportunities', 
// 'ensure equal opportunities', and 'sure equal opportunities'
SearchResults results2 = index.search("\"?(0~2)sure equal opportunities\"");
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/java/) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Search:

*   [Installation](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-search "GroupDocs.Search Installation") - Install GroupDocs.Search from Maven
*   [Documentation](https://docs.groupdocs.com/search/java/groupdocs-search-overview/ "Search API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-search/GroupDocs.Search-for-Java "How to use Search API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/search) - Technical Support Forum for GroupDocs.Search

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").





