---
title: 'Find Homophones in Multiple Files in Java'
date: Thu, 13 Jan 2022 06:28:19 +0000
draft: false
url: /2022/01/13/find-homophones-in-multiple-files-using-java/
author: 'Shoaib Khan'
summary: '**Synonyms** are words with similar meaning, and **Homophones** sounds the same but are different in meanings or spellings. We learned to [find synonyms in multiple documents using Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/). Today, in this article, we will see **how to search homophones within multiple documents using Java**.'
tags: ['Find Homophone in Java', 'Find Homophones', 'Find Homophones in Files', 'Homophones']
categories: ['GroupDocs.Search Product Family']
---

{{< figure align=center src="images/Search-Homophones-in-Files.jpg" alt="Search Homophones in Files using GroupDocs">}}

**Synonyms** are words with similar meaning, and **Homophones** sounds the same but are different in meanings or spellings. We learned to [find synonyms in multiple documents using Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/). Today, in this article, we'll see **how to search homophones within multiple documents using Java**.

The following topics will be covered below:

*   [Java API - Homophone Search](#homophone-search-java-api)
*   [Find homophones in documents using Java](#homophone-in-different-files)
*   [Play with Homophone Search Result](#print-homophone-search)

## Java API for Searching Homophones {#homophone-search-java-api}

[GroupDocs.Search](https://products.groupdocs.com/search/) showcases the Java API ([GroupDocs.Search for Java](https://products.groupdocs.com/search/net/)) that allows finding any word and its homophones within multiple files of any specific folder. It can search the content of [various different formats](https://docs.groupdocs.com/search/net/supported-document-formats/). In addition to finding the homophones, the API supports many other searching techniques which include:

*   Case-Sensitive Search
*   Fuzzy Search
*   Phrase Search
*   Regular Expressions Search
*   Synonym Search
*   Wild Card Search

You can download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/search) or use the latest repository and dependency [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) configurations within your Java applications.

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

```
PM> Install-Package GroupDocs.Search
```

## Find Homophones in Multiple Files in Java {#homophone-in-different-files}

The following steps guide how to search homophones in multiple files of a folder in Java.

*   Define the search word query, indexing folder, and the container folder of your files.
*   Create [Index](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index) with the defined index folder.
*   Add the document's folder to the index.
*   Define the [SearchOptions](https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions) and enable the homophoneSearch using [setUseHomophoneSearch()](https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions#setUseHomophoneSearch(boolean)).
*   Perform the homophones search using [search()](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery,%20com.groupdocs.search.options.SearchOptions)) method.
*   Use the properties of the retrived [SearchResult](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult) as needed.

The following Java source code finds all the homophones within files of the defined folder. Further, you can also [manage your homophone dictionary](https://docs.groupdocs.com/search/java/homophone-dictionary/).

{{< gist GroupDocsGists e150579822915caefa017952b0f19b3d "SearchHomophonesInFilesAndFolders.java" >}}

The output of the above code is as follows:

```
Query: right
Documents: 2
Occurrences: 17
```

## Printing Homophone Search Results in Java {#print-homophone-search}

You can use the homophones search results by following the steps after getting the homophones and their occurrences from each document.

*   Traverse the search results.
*   Get each [FoundDocument](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument) using the [getFoundDocument()](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult#getFoundDocument(int)) method.
*   Use the properties of each FoundDocument as required.
*   Now, traverse the fields of FoundDocument by getting [FoundDocumentField](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocumentField).
*   Later, from each FoundDocumentField, get all the terms and their occurrences within each document.

The following Java code example prints the homophone search results along with the number of occurrences of each searched term.

{{< gist GroupDocsGists e150579822915caefa017952b0f19b3d "PrintingHomophoneSearchResults.java" >}}

The following is the output of the above code example.

```
Query: right
Documents: 2
Total occurrences: 17

Document: C:/documents/sample.docx
Occurrences: 11
    Field: content
    Occurrences: 11
        right             3
        rite               4
        wright           1
        write             3
Document: C:/documents/sample.txt
Occurrences: 6
    Field: content
    Occurrences: 6
        right             4
        write             2
```

## Search Homophones and Printing Results using Java - Complete Code {#search-and-print-synonyms-code}

The following Java code combines the above steps. Initially, it finds the homophones as per query, and then prints all the occurrences of homophones from each document within the provided folder.

{{< gist GroupDocsGists e150579822915caefa017952b0f19b3d "SearchHomophonesAndPrintResults.java" >}}

## Conclusion

To conclude, you learned how to find the words and their homophones from multiple documents within a specified folder using Java. You can try developing your own Java application for searching homophones using **GroupDocs.Search for Java**.

Learn more [about the Java Search Automation API](https://docs.groupdocs.com/search/java/) from the documentation. To experience its features, you can have a look at the available examples on the [GitHub](https://github.com/groupdocs-search) repository. Reach us for any query via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Search Homophones in Multiple Files in C#](https://blog.groupdocs.com/2022/01/04/find-homophones-in-multiple-files-using-csharp/)
*   [Find Synonyms of Words using Java](https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/)
*   [Build your Full Text Search Solution in Java](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)
*   [Find and Replace Words in Documents using Java](https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/)
*   [Find and Remove Watermarks from Documents in Java](https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/)




