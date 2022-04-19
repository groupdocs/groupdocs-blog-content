---
title: "使用 Java 在多个文件中搜索同义词"
date: Sun, 03 Oct 2021 07:50:04 +0000
draft: false
url: /zh/2021/10/03/find-synonyms-in-multiple-files-using-java/
author: 'Shoaib Khan'
summary: "我们最近讨论过，[如何获取任何单词的所有同义词][1]。如果我们能在许多不同的文档中找到这些同义词，那就太好了。在本文中，我们将看到**如何使用 Java 搜索多个文件中的任何单词及其同义词**。"
tags: ['Find in Files', 'Find in Files using Java', 'Find Synonyms', 'Find Synonyms in Java', 'Search Synonyms', 'Search Synonyms in Java']
categories: ['GroupDocs.Search Product Family']
---

我们最近讨论过，[如何获取任何单词的所有同义词][2]。如果我们能在许多不同的文档中找到这些同义词，那就太好了。在本文中，我们将看到**如何使用 Java 搜索多个文件中的任何单词及其同义词**。

以下是以下涵盖的主题：

* [Java API – 同义词搜索][3]
* [在 Java 文档中查找同义词][4]
* [当前同义词搜索结果][5]
* [完整的Java代码-搜索和打印同义词搜索结果][6]

## Java API - 在多个文件中搜索同义词 {#synonym-search-java-api}

[GroupDocs.Search][7] 展示了 Java API ([GroupDocs.Search for Java][8]。它允许在指定文件夹的多个文件中搜索单词及其同义词。它支持一长串不同的文件格式和各种搜索技术。下面提到了其中一些功能，您可以结合使用它们来实现您的目标：

* 布尔搜索
*区分大小写的搜索
* 突出显示搜索结果
* 同音字搜索
* 短语搜索
* 正则表达式搜索
* 按块搜索
* 同义词搜索

### 下载或配置

您可以从 [下载部分][9] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

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

## 使用 Java 在多个文件中查找同义词 {#synonyms-in-different-files}

让我们快速开始搜索文件中的同义词。以下步骤显示了如何使用 Java 在文件夹中的文件中搜索同义词（具有相似含义的单词）：

* 定义索引文件夹、文档文件夹和查询（要搜索的词）。
* 使用 [Index][10] 类使用定义的索引文件夹创建索引。
* 将文档的文件夹添加到索引中。
* 使用 [SearchOptions][11] 启用同义词搜索。
* 调用 Index 类的 [search][12] 方法并传递带有搜索选项的查询。
* 使用检索到的 [SearchResult][13] 类的属性打印摘要。

以下源代码显示了如何使用 Java 查找文件中的所有同义词：

```
// 使用 Java 在多个文件和文件夹中搜索同义词
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "make";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
index.add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions();
options.setUseSynonymSearch(true); // Enable Synonym Search

// 搜索单词“make”
// 除了单词“make”，还将搜索同义词“do, get, have, ...”
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Synonym Occurrences: " + result.getOccurrenceCount());
```

以下是上述代码的输出：

```
Query: **make**
Documents: 3
Word & Synonym Occurrences: 44 
```

## 使用 Java 打印同义词搜索结果 {#print-synonym-search}

从上述步骤中得到的搜索结果中，您可以得到搜索的每个单词和同义词的信息。在获得所有同义词及其在每个文档中出现的次数后，以下步骤详细展示了结果：

* 首先进行搜索，得到[SearchResult][14]。
* 遍历搜索结果以使用每个 [FoundDocument][15]。
* 打印每个 FoundDocument 的相应属性。
* 现在，提取并遍历每个 FoundDocument 中的 [FoundDocumentField][16]。
* 每个 FoundDocumentField 都有它的术语、出现次数和其他属性。使用各自的吸气剂。

以下源代码显示同义词搜索的结果以及 Java 中每个搜索词的出现次数。

```
// 用 Java 打印同义词搜索结果
System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Synonym Occurrences: " + result.getOccurrenceCount());

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

以下是上述代码的输出：

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

## 用 Java 搜索同义词和打印结果 - 完整代码 {#search-and-print-synonyms-code}

让我们结合上面的两个步骤，所以这里是完整的源代码。首先，它根据提供的查询找到所有同义词。然后，它打印 Java 中每个文档中每个同义词的所有出现。

```
// 使用 Java 在多个文件和文件夹中搜索同义词
String indexFolder = "path/indexFolder";
String documentsFolder = "path/documentsFolder";
String query = "make";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
index.add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions();
options.setUseSynonymSearch(true); // Enable Synonym Search

// 搜索单词“make”
// 除了单词“make”，还将搜索同义词“do, get, have, ...”
SearchResult result = index.search(query, options);

System.out.println("Query: " + query);
System.out.println("Documents: " + result.getDocumentCount());
System.out.println("Word & Synonym Occurrences: " + result.getOccurrenceCount());

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

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][17] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们讨论了如何使用 Java 在多个文档中搜索任何单词及其同义词。最重要的是，现在您可以尝试开发自己的 Java 应用程序进行搜索，就像 [GroupDocs.Search App][18] 一样。

从文档中了解更多 [关于 Java 搜索自动化 API][19]。要体验这些功能，请尝试 [GitHub][20] 存储库中的示例。如有任何疑问，请随时通过 [论坛][21] 联系我们。

## 也可以看看

* [使用 Java 查找单词的同义词][22]
* [用 Java 构建您的全文搜索解决方案][23]
* [使用Java查找和替换文档中的单词][24]
* [在Java文档中查找和删除水印][25]







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


