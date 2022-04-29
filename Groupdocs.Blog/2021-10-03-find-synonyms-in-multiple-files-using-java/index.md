---
title: "Search Synonyms in Multiple Files using Java"
seoTitle: "Find any Word and its Synonyms in Multiple Files using Java"
description: "Find specific word and its synonyms within different files using Java. Similary, get all the synonyms, grouped by different meanings using Java Search API."
date: Sun, 03 Oct 2021 07:50:04 +0000
draft: false
url: /2021/10/03/find-synonyms-in-multiple-files-using-java/
author: 'Shoaib Khan'
summary: "We recently have discussed, [how to get all the synonyms of any word][1]. It would be wonderful if we could locate these synonyms within many different documents. In this article, we will see **how to search any word and its synonyms in multiple files using Java**."
tags: ['Find in Files', 'Find in Files using Java', 'Find Synonyms', 'Find Synonyms in Java', 'Search Synonyms', 'Search Synonyms in Java']
categories: ['GroupDocs.Search Product Family']
---

We recently have discussed, [how to get all the synonyms of any word][2]. It would be wonderful if we could locate these synonyms within many different documents. In this article, we will see **how to search any word and its synonyms in multiple files using Java**.

The following are the topics covered below:

*   [Java API – Synonym Search][3]
*   [Find synonyms in documents in Java][4]
*   [Present synonym search results][5]
*   [Complete Java code – Search & print synonyms search results][6]

## Java API - Search Synonyms in Multiple Files {#synonym-search-java-api}

[GroupDocs.Search][7] showcases the Java API ([GroupDocs.Search for Java][8]. It allows searching words and their synonyms in various multiple files of the specified folder. It supports a long list of different file formats and various search techniques. Some of these features are mentioned below and you can use them in combination to achieve your target:

*   Boolean Search
*   Case-Sensitive Search
*   Highlight Search Results
*   Homophone Search
*   Phrase Search
*   Regular Expressions Search
*   Search by Chunks
*   Synonym Search

### Download or Configure

You may download the **JAR** file from the [downloads section][9], or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-search</artifactId>
        <version>21.8</version> 
</dependency>
```

## Find Synonyms in Multiple Files using Java {#synonyms-in-different-files}

Let's quickly move to search synonyms within files. The following steps show how to search synonyms (words with similar meanings) in files within a folder using Java:

*   Define the index folder, document’s folder and query (the word to search).
*   Create an index using defined index folder using [Index][10] class.
*   Add the documents' folder to the index.
*   Enable the Synonym Search using [SearchOptions][11].
*   Call the [search][12] method of Index class and pass the query with search options.
*   Print the summary using the properties of the retrived [SearchResult][13] class.

The following source code shows how to find all the synonyms within files using Java:

{{< gist GroupDocsGists 1cffe6974c43184cb73f49e26af1a7f4 "SearchSynonymsInFilesAndFolders.java" >}}

The following is the output of the above code:

```
Query: **make**
Documents: 3
Word & Synonym Occurrences: 44 
```

## Printing Synonym Search Results using Java {#print-synonym-search}

From the search results obtained in the above step, you can get the information regarding each word and synonym of the search. The following steps present the results in detail after getting all the synonyms and their number of occurrences within each document:

*   Firstly, perform the search to get the [SearchResult][14].
*   Tranverse the search result to work with each [FoundDocument][15].
*   Print the repective properties of each FoundDocument.
*   Now, extract and then traverse the [FoundDocumentField][16] within each FoundDocument.
*   Each FoundDocumentField has its terms, occurrences, and other properties in it. Use respective getter.

The following source code displays the result of the synonym search along with the number of occurrences of each searched term in Java.

{{< gist GroupDocsGists 1cffe6974c43184cb73f49e26af1a7f4 "PrintingSearchResults.java" >}}

The following is the output of the above code:

```
Query: **make**
Documents: 2
Total occurrences: 22

Document: C:/documents/sample.docx
Occurrences: 13
    Field: content
    Occurrences: 13
        **make**  -  2
        **have**  -  1
        **get**  -  2
        **do**  -  8
- - - - - - - - - - - - - - - - 
Document: C:/documents/sample.txt
Occurrences: 11
    Field: content
    Occurrences: 11
        **make**  -  1
        **have**  -  2
        **get**  -  1
        **do**  -  7
- - - - - - - - - - - - - - - - 
Document: C:/documents/sample.pdf
Occurrences: 20
    Field: content
    Occurrences: 20
        **make**  -  2
        **have**  -  2
        **get**  -  2
        **do**  -  14 
```

## Search Synonyms and Printing Results in Java – Complete Code {#search-and-print-synonyms-code}

Let's combine the above two steps, so here is the complete source code. Firstly, it finds all the synonyms according to the provided query. Then, it prints all the occurrences of every synonym in each document in Java.

{{< gist GroupDocsGists 1cffe6974c43184cb73f49e26af1a7f4 "SearchSynonymsAndPrintResults.java" >}}

## Get a Free API License

You can [get a free temporary license][17] in order to use the API without the evaluation limitations.

## Conclusion

To summarize, we discussed how to search any word along with its synonym in multiple documents using Java. Most importantly, now you can try developing your own Java App for searching just like [GroupDocs.Search App][18].

Learn more [about the Java Search Automation API][19] from the documentation. To experience the features, try examples from the [GitHub][20] repository. Feel free to reach us for any query via the [forum][21].

## See Also

*   [Find Synonyms of Words using Java][22]
*   [Build your Full Text Search Solution in Java][23]
*   [Find and Replace Words in Documents using Java][24]
*   [Find and Remove Watermarks from Documents in Java][25]







[1]: https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/
[2]: https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/
[3]: #synonym-search-java-api
[4]: #synonym-search-java-api
[5]: #print-synonym-search
[6]: #search-and-print-synonyms-code
[7]: https://products.groupdocs.com/search/
[8]: https://products.groupdocs.com/search/java/)
[9]: https://downloads.groupdocs.com/search
[10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions
[12]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery,%20com.groupdocs.search.options.SearchOptions)
[13]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult
[14]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult
[15]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument
[16]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocumentField
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://products.groupdocs.app/search/total
[19]: https://docs.groupdocs.com/search/java/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/
[23]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[24]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[25]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/

