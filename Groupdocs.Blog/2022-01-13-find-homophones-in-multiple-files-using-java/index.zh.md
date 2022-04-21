---
title: "'在 Java 中的多个文件中查找同音字'"
date: Thu, 13 Jan 2022 06:28:19 +0000
draft: false
url: /zh/2022/01/13/find-homophones-in-multiple-files-using-java/
author: 'Shoaib Khan'
summary: '**Synonyms** are words with similar meaning, and **Homophones** sounds the same but are different in meanings or spellings. We learned to [find synonyms in multiple documents using Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/). Today, in this article, we will see **how to search homophones within multiple documents using Java**.

本文涵盖以下主题：

* Java API - 同音字搜索
* 使用 Java 在文档中查找同音字
* 玩同音搜索结果'
tags: ['Find Homophone in Java', 'Find Homophones', 'Find Homophones in Files', 'Homophones']
categories: ['GroupDocs.Search Product Family']
---

{{< figure align=center src="images/Search-Homophones-in-Files.jpg" alt="使用 GroupDocs 在文件中搜索同音字">}}

**同义词**是具有相似含义的词，**同音词**听起来相同，但含义或拼写不同。我们学会了[使用 Java 在多个文档中查找同义词](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/)。今天，在本文中，我们将了解**如何使用 Java 在多个文档中搜索同音字**。

下面将介绍以下主题：

* [Java API - 同音字搜索](#homophone-search-java-api)
* [使用 Java 在文档中查找同音字](#homophone-in-different-files)
* [播放同音字搜索结果](#print-homophone-search)

## 用于搜索同音字的 Java API {#homophone-search-java-api}

[GroupDocs.Search](https://products.groupdocs.com/search/) 展示了 Java API ([GroupDocs.Search for Java](https://products.groupdocs.com/search/net/))，它允许在任何特定文件夹的多个文件中查找任何单词及其同音字。 它可以搜索[各种不同格式](https://docs.groupdocs.com/search/net/supported-document-formats/) 的内容。 除了查找同音字之外，API 还支持许多其他搜索技术，包括：

*区分大小写的搜索
* 模糊搜索
* 短语搜索
* 正则表达式搜索
* 同义词搜索
* 外卡搜索

您可以从[下载部分](https://downloads.groupdocs.com/search)下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) 配置。

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

## Trouver des homophones dans plusieurs fichiers en Java {#homophone-in-different-files}

以下步骤指导如何在 Java 中搜索文件夹的多个文件中的同音字。

* 定义搜索词查询、索引文件夹和文件的容器文件夹。
* 使用定义的索引文件夹创建[Index](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index)。
* 将文档的文件夹添加到索引中。
* 定义 [SearchOptions](https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions) 并使用 [setUseHomophoneSearch()](https://apireference.groupdocs.com/search/java/com.groupdocs.search.options/SearchOptions#setUseHomophoneSearch(boolean))。
* 使用 [search()](https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery,%20com.groupdocs.search.options.SearchOptions)) 方法执行同音字搜索。
* 根据需要使用检索到的 [SearchResult](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult) 的属性。

以下 Java 源代码在已定义文件夹的文件中查找所有同音字。 此外，您还可以[管理您的同音词词典](https://docs.groupdocs.com/search/java/homophone-dictionary/)。

```
// 使用 Java 在多个文件和文件夹中搜索同音字
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "right";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
index.add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions();
options.setUseHomophoneSearch(true); // Enable Homophone Search

// 搜索单词“正确”
// 除了单词“right”之外，还将搜索同音词“rite, write, wright, ...”
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Homophone Occurrences: " + result.getOccurrenceCount());
```

上述代码的输出如下：

```
Query: right
Documents: 2
Occurrences: 17
```

## 用 Java 打印同音字搜索结果 {#print-homophone-search}

从每个文档中获取同音字及其出现后，您可以按照以下步骤使用同音字搜索结果。

*   遍历搜索结果。
*   使用 [getFoundDocument()](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/SearchResult#getFoundDocument(int)) 方法获取每个 [FoundDocument](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocument)。
*   根据需要使用每个 FoundDocument 的属性。
*   现在，通过获取 [FoundDocumentField](https://apireference.groupdocs.com/search/java/com.groupdocs.search.results/FoundDocumentField) 来遍历 FoundDocument 的字段。
*   稍后，从每个 FoundDocumentField 中，获取每个文档中的所有术语及其出现。

以下 Java 代码示例打印同音字搜索结果以及每个搜索词的出现次数。

```
// 用 Java 打印同音字搜索结果
System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Homophone Occurrences: " + result.getOccurrenceCount());

// 遍历文档
for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrences: " + document.getOccurrenceCount());
  
  // 遍历找到的字段
  for (FoundDocumentField field : document.getFoundFields()) {
        System.out.println("\tField: " + field.getFieldName());
        System.out.println("\tOccurrences: " + document.getOccurrenceCount());
  
        // 打印找到的术语
        if (field.getTerms() != null) {
            for (int k = 0; k < field.getTerms().length; k++) {
                System.out.println("\t\t" + field.getTerms()[k] + "\t - \t" + field.getTermsOccurrences()[k]);
            }
        }
    }
}
```

以下是上述代码示例的输出。

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

## 使用 Java 搜索同音字并打印结果 - 完整代码 {#search-and-print-synonyms-code}

以下 Java 代码结合了上述步骤。 最初，它根据查询找到同音字，然后从提供的文件夹中的每个文档中打印所有出现的同音字。

```
// 使用 Java 在多个文件和文件夹中搜索同音字
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "right";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
index.add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions();
options.setUseHomophoneSearch(true); // Enable Homophone Search

// 搜索单词“正确”
// 除了单词“right”之外，还将搜索同音词“rite, write, wright, ...”
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Homophone Occurrences: " + result.getOccurrenceCount());

for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrences: " + document.getOccurrenceCount());

  for (FoundDocumentField field : document.getFoundFields()) {
        System.out.println("\tField: " + field.getFieldName());
        System.out.println("\tOccurrences: " + document.getOccurrenceCount());
  
        // Printing found terms
        if (field.getTerms() != null) {
            for (int k = 0; k < field.getTerms().length; k++) {
                System.out.println("\t\t" + field.getTerms()[k] + "\t - \t" + field.getTermsOccurrences()[k]);
            }
        }
    }
}
```

## Conclusion

最后，您学习了如何使用 Java 从指定文件夹内的多个文档中查找单词及其同音字。 您可以尝试使用 **GroupDocs.Search for Java** 开发自己的 Java 应用程序来搜索同音字。

从文档中了解 [关于 Java 搜索自动化 API](https://docs.groupdocs.com/search/java/) 的更多信息。 要体验其功能，您可以查看 [GitHub](https://github.com/groupdocs-search) 存储库中的可用示例。 通过 [论坛](https://forum.groupdocs.com/) 联系我们进行任何查询。

## See Also

*   [在 C# 中搜索多个文件中的同音字](https://blog.groupdocs.com/2022/01/04/find-homophones-in-multiple-files-using-csharp/)
*   [使用 Java 查找单词的同义词](https://blog.groupdocs.com/2021/09/30/find-synonyms-of-words-using-java/)
*   [用 Java 构建您的全文搜索解决方案](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)
*   [使用 Java 查找和替换文档中的单词](https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/)
*   [在 Java 中查找和删除文档中的水印](https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/)





