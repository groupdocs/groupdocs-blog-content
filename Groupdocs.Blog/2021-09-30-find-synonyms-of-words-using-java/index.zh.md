---
title: "使用 Java 查找单词的同义词"
date: Thu, 30 Sep 2021 14:17:00 +0000
draft: false
url: /zh/2021/09/30/find-synonyms-of-words-using-java/
author: 'Shoaib Khan'
summary: "避免重复同一个词；使用**同义词**（两个不同的词，意思相同）。如果您需要以编程方式查找任何单词的所有此类同义词怎么办？本文将指导您如何使用 Java 找出任何单词的所有同义词。同样，一个词可能有多种含义。我们将看到如何根据同一个词的不同含义对同义词进行分组。"
tags: ['Find Synonyms', 'Find Synonyms in Java', 'Search Synonyms', 'Search Synonyms in Java', 'Synonyms in Java']
categories: ['GroupDocs.Search Product Family']
---

避免重复同一个词；使用**同义词**（两个不同的词，意思相同）。如果您需要以编程方式查找任何单词的同义词怎么办？本文将指导您**如何使用 Java 找出任何单词的所有同义词**。同样，一个词可能有多种含义。我们将看到如何根据同一个词的不同含义对同义词进行分组。

下面将介绍以下主题：

* [Java API – 查找同义词][1]
* [获取Java中任何单词的同义词][2]
* [获取同义词 - 按不同含义分组][3]

## 用于查找同义词的 Java API {#find-synonyms-java-api}

[GroupDocs.Search][4] 允许通过其 API 查找单词的同义词。我将在示例中使用它的 [Java API][5]。它还允许在文件夹内的多个文档中搜索单词及其所有同义词。许多不同的搜索技术可用于[搜索大量文档格式][6]。

### 下载或配置

您可以从 [下载部分][7] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-search</artifactId>
        <version>21.8</version> 
</dependency>
```

## 在 Java 中查找任何单词的同义词 {#get-synonyms}

假设，你的脑海里有“SHOW”这个词。让我们看看，“SHOW”的同义词可能是什么。以下是使用 Java 获取同义词的步骤。

* 首先，设置查询/单词以查找其同义词。
* 使用 [Index][8] 类创建索引。
* 通过将查询传递给 [getSynonyms][9] 方法，从各种词典中获取同义词词典，然后获取同义词集合。
* 遍历同义词以使用每个同义词。

以下源代码显示了如何在 Java 中获取任何提供的单词的所有同义词。

```
// 获取Java中任何单词的所有同义词
String query = "show";
String[] synonyms = new Index().getDictionaries().getSynonymDictionary().getSynonyms(query);

System.out.println("Synonyms for " + query +":");

for (String synonym : synonyms) {
    System.out.println(synonym);
}
```

这是上述 Java 代码的输出，显示了单词“show”的所有同义词。

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

## 在 Java 中查找按不同含义分组的同义词 {#get-synonyms-as-group}

根据情况和用法，单个词可能有不同的含义。您可以根据其含义对不同的同义词集进行分组。以下步骤允许您使用 Java 获取不同的同义词组。

* 首先，设置需要同义词的单词。
* 使用 [Index][10] 类创建索引。
* 通过将查询传递给 [getSynonymGroups][11] 方法，从不同的字典中获取同义词字典，然后是同义词组的集合。
*横向同义词组集合与每个组或同义词一起工作。

以下源代码显示了如何获取 Java 中任何提供的单词的所有同义词组。

```
// 使用Java根据同一个词的不同含义获取同义词组
String query = "show";
String[][] groups = new Index().getDictionaries().getSynonymDictionary().getSynonymGroups(query);

System.out.println("Synonym groups for " + query +":");

for (String[] group : groups) {
    for (String group1 : group) {
        System.out.print(group1 + " ");
    }
    System.out.println();
}
```

以下是上述 Java 代码的输出，显示了提供的单词“show”的所有同义词，根据其不同的含义进行分组。

```
Synonym groups for **show**:

 - evidence prove **show** testify 
 - demo demonstrate exhibit present **show** 
```

接下来，我们将在另一篇文章中讨论，[如何使用 Java 在文件夹的多个文件中查找任何单词及其同义词][12]。

## 结论

总而言之，我们讨论了如何使用简单的方法在 Java 中找到任何单词的可能同义词。此外，我们讨论了如何获取根据同一个词的不同含义创建的所有同义词组。现在，您可以尝试构建自己的 Java 应用程序同义词。

从文档中了解 [关于 Java 搜索自动化 API][13] 的更多信息。要体验这些功能，您可以查看 [GitHub][14] 存储库中的示例。通过 [论坛][15] 联系我们进行任何查询。

## 也可以看看

* [使用 C# 查找单词的同义词][16]
* [使用 Java 在多个文件中搜索同义词][17]
* [用 Java 构建您的全文搜索解决方案][18]
* [使用Java查找和替换文档中的单词][19]
* [在Java文档中查找和删除水印][20]







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


