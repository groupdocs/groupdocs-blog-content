---
title: 'Get List of Indexed Documents using GroupDocs.Search for .NET 18.9'
date: Mon, 24 Sep 2018 10:36:39 +0000
draft: false
url: /2018/09/24/get-list-of-indexed-documents-using-groupdocs.search-for-.net-18.9/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Search', 'GroupDocs.Search for .NET', 'GroupDocs.Search for .NET Releases', 'GroupDocs.Search Product Family']
---

[![GroupDocs.Search for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-search-net.png)](https://www.groupdocs.com/products/search/net)We are pleased to announce the monthly release of [GroupDocs.Search for .NET](https://products.groupdocs.com/search/net) **18.9**.  Using the latest version, you can now get the list of indexed documents and document's text from the index archive. Moreover, you can now save encodings automatically which were used to extract text from TXT files.  We would recommend you to [install](https://www.nuget.org/packages/GroupDocs.Search/) and use the latest version of the API.

# Enhancements

Following are the enhancements introduced in the latest version:

## Get List of Indexed DocumentsUsing GroupDocs.Search API you can get a list of indexed documents and items from container documents like ZIP archives, OST and PST files. This example shows how to get a list of indexed documents from an index:```
 string indexFolder = @"c:\MyIndex";
  
// Creating index from existing folder
Index index = new Index(indexFolder);
  
// Getting list of indexed documents
DocumentInfo[] documents = index.GetIndexedDocuments();
  
// Getting items of container document
DocumentInfo[] items = index.GetIndexedDocumentItems(documents[0]);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

## Extract Document TextUsing the latest version, you can now extract document text from the index archive or from a document directly if archiving is not used. An extracted text can be used to check an encoding that is used for indexing text documents. Also, it can be used for quick manual checking of the presence or absence of any words in documents. This example shows how to extract document text from the index:```
 string indexFolder = @"c:\MyIndex";
   
// Creating index from existing folder
Index index = new Index(indexFolder);
   
// Getting list of indexed documents
DocumentInfo[] documents = index.GetIndexedDocuments();
  
// Extracting HTML formatted document text
string htmlText = index.ExtractDocumentText(documents[0], null);
```This example shows how to extract document text to a file:```
 string indexFolder = @"c:\MyIndex";
   
// Creating index from existing folder
Index index = new Index(indexFolder);
   
// Getting list of indexed documents
DocumentInfo[] documents = index.GetIndexedDocuments();
  
// Extracting HTML formatted document text to a file
index.ExtractDocumentText(@"c:\DocumentText.html", documents[0], null);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/search/net) documentation article.

## Save Encodings AutomaticallyGroupDocs.Search for .NET 18.9 implements automatic saving of encodings which were used to extract text from TXT files. In practice, this means that there is no longer any need to provide an encoding when generating document text with highlighted found words. This example shows how to generate HTML formatted text with highlighted found words:```
 string indexFolder = @"c:\MyIndex";
string documentFolder = @"c:\MyDocuments";
  
// Creating index
Index index = new Index(indexFolder);
  
// Subscribing to file indexing event
index.FileIndexing += (sender, args) =>
{
    // Setting encoding for each text file during indexing
    args.Encoding = Encodings.windows_1251;
};
  
// Adding text documents encoded in windows-1251 to index
index.AddToIndex(documentFolder);
  
// Searching for word 'человеческий'
SearchResults results = index.Search("человеческий");
  
// Generating HTML formatted text with highlighted found words
// There is no need to provide the encoding again - it is saved in the index
string htmlText = index.HighlightInText(results[0]);
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




