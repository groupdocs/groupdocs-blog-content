---
title: "Find Synonyms of Words using Java"
seoTitle: "Find Synonyms of any Word in Java | Synonym Groups by Meanings"
description: "Find all the possible synonyms of any word in Java. Get different collections of synonyms arranged by different meanings of the same word using Search API."
date: Thu, 30 Sep 2021 14:17:00 +0000
draft: false
url: /2021/09/30/find-synonyms-of-words-using-java/
author: 'Shoaib Khan'
summary: "Avoid the repetition of the same word; use **Synonyms** (two different words that mean the same). What if you need to find all such synonyms of any word programmatically? This article guides you on how to find out all the synonyms of any word using Java. Similarly, a single word could have multiple meanings. We will see how the synonyms can be grouped according to different meanings of that same word."
tags: ['Find Synonyms', 'Find Synonyms in Java', 'Search Synonyms', 'Search Synonyms in Java', 'Synonyms in Java']
categories: ['GroupDocs.Search Product Family']
---

Avoid the repetition of the same word; use **Synonyms** (two different words that mean the same). What if you need to find synonyms of any word programmatically? This article guides you on **how to find out all the synonyms of any word using Java**. Similarly, a single word could have multiple meanings. We will see how the synonyms can be grouped according to different meanings of that same word.

The following topics will be covered below:

*   [Java API – Find Synonyms][1]
*   [Get synonyms of any word in Java][2]
*   [Get synonyms – Grouped by different meanings][3]

## Java API for Finding Synonyms {#find-synonyms-java-api}

[GroupDocs.Search][4] allows finding synonyms of words through its APIs. I will be using its [Java API][5] in the examples. It further lets searching the word and all its synonyms in multiple documents within a folder. Many different search techniques are available that can be used to [search over a large list of document formats][6].

### Download or Configure

You may download the **JAR** file from the [downloads section][7], or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

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

## Find Synonyms of any Word in Java {#get-synonyms}

Suppose, you have the word "SHOW" in your mind. Let's see, what possibly could be the synonyms of 'SHOW'. The following are the steps to get synonyms using Java.

*   First, set the query/word to find its synonyms.
*   Create index using the [Index][8] class.
*   From the various dictionaries, get the synonyms dictionary and then the collection of synonyms by passing the query to [getSynonyms][9] method.
*   Tranverse the synonyms to work with each synonym.

The following source code shows how to get all the synonyms of any provided word in Java.

{{< gist GroupDocsGists 1cffe6974c43184cb73f49e26af1a7f4 "SynonymsOfAnyWord.java" >}}

Here is the output of the above Java code that displays all the synonyms of the word “show”.

```
Synonyms for '**show**':

 - prove
 - testify
 - present
 - demo
 - exhibit
 - demonstrate
 - evidence  
```

## Find Synonyms Grouped by Different Meanings in Java {#get-synonyms-as-group}

There could be different meanings of a single word according to the situation and its usage. You can group different sets of synonyms w.r.t its meaning. The following steps allow you to get different groups of synonyms using Java.

*   First, set the word whose synonyms are required.
*   Create the index using [Index][10] class.
*   From the different dictionaries, get the synonyms dictionary and then the collection of synonym groups by passing the query to the [getSynonymGroups][11] method.
*   Tranverse synonym groups collection to work with each group or synonym word.

The following source code shows how to get all the synonym groups of any provided word in Java.

{{< gist GroupDocsGists 1cffe6974c43184cb73f49e26af1a7f4 "SynonymsGroups.java" >}}

The following is the output of the above Java code that displays all the synonyms of the provided word “show” grouped according to its different meaning.

```
Synonym groups for **show**:

 - evidence prove **show** testify 
 - demo demonstrate exhibit present **show** 
```

Next, we will discuss in a separate article, [how to find any word and its synonyms within multiple files of a folder using Java][12].

## Conclusion

To sum up, we discussed how to find the possible synonyms of any word in Java using simple methods. Further, we discussed that how to get all the groups of synonyms that are created according to the different meanings of that same word. Now, you can try to build your own Java application synonyms.

Learn more [about the Java Search Automation API][13] from the documentation. To experience the features, you can have a look at examples on the [GitHub][14] repository. Reach us for any query via the [forum][15].

## See Also

*   [Find Synonyms of Words using C#][16]
*   [Search Synonyms in Multiple Files using Java][17]
*   [Build your Full Text Search Solution in Java][18]
*   [Find and Replace Words in Documents using Java][19]
*   [Find and Remove Watermarks from Documents in Java][20]







[1]: #find-synonyms-java-api
[2]: #get-synonyms
[3]: #get-synonyms-as-group
[4]: https://products.groupdocs.com/search/
[5]: https://products.groupdocs.com/search/java/
[6]: https://docs.groupdocs.com/search/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/search
[8]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[9]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.dictionaries/SynonymDictionary#getSynonyms(java.lang.String)
[10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.dictionaries/SynonymDictionary#getSynonymGroups(java.lang.String)
[12]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[13]: https://docs.groupdocs.com/search/java/
[14]: https://github.com/groupdocs-search
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[17]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[18]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[19]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[20]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/

