---
title: 'ZIP Archive Indexing is Improved in GroupDocs.Search for Java 19.2'
date: Sat, 16 Feb 2019 07:01:02 +0000
draft: false
url: /2019/02/16/zip-archive-indexing-is-improved-in-groupdocs.search-for-java-19.2/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Search for Java', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for Java](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/10/groupdocs.search-for-java-90x90.png)](https://products.groupdocs.com/search/java)We are pleased to announce the monthly release of GroupDocs.Search for Java 19.2. Improvements such as indexing of a ZIP archive inside other ZIP and escape of special characters in search queries are introduced. Please check GroupDocs.Search for Java 19.2 [release notes](https://docs.groupdocs.com/display/searchjava/GroupDocs.Search+for+java+19.2+Release+Notes) for further reference. We would recommend you to download and integrate latest version of the API.

# Breaking Change

*   Removed obsolete methods Import and Export from dictionary classes

# Improvements

Following improvements are introduced in this release:

## Implement escaping special characters in search queries```
String indexFolder = "c:\\MyIndex";
String documentFolder = "c:\\MyDocuments";
// Creating index
Index index = new Index(indexFolder);
// Marking character '&' as a valid letter, not a separator
index.getDictionaries().getAlphabet().setRange(new char[] { '&' }, CharacterType.Letter);
// Adding documents to index
index.addToIndex(documentFolder);
// Searching for word 'R&B'
SearchResults results0 = index.search("R\\&B");
// Searching for word 'R&B'
SearchResults results1 = index.search("R\\u0026B");
```

## Indexing ZIP archives inside other ZIP archives```
String indexFolder = "c:\\MyIndex";
String documentFolder = "c:\\MyDocuments";
// Creating index
Index index = new Index(indexFolder);
// Adding documents to index
// ZIP archives and ZIP archives inside those archives will be automatically added to index
index.addToIndex(documentFolder);
// Searching
SearchResults results = index.search("zip");
```

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Search:

*   [Installation](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-search "GroupDocs.Search Installation") - Install GroupDocs.Search from Maven
*   [Documentation](https://docs.groupdocs.com/search/java/groupdocs-search-overview/ "Search API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-search/GroupDocs.Search-for-Java "How to use Search API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/search) - Technical Support Forum for GroupDocs.Search

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").




