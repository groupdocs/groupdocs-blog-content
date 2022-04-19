---
title: "用 Java 构建全文搜索解决方案"
date: Sat, 07 Aug 2021 08:09:00 +0000
draft: false
url: /zh/2021/08/07/build-full-text-search-solution-in-java/
author: 'Shoaib Khan'
summary: "全文搜索是一种在文档集合中搜索文本/查询的方法。这种方法可以快速找到一个术语/短语的所有实例，并且它通过使用文本索引来工作。在本文中，我们将学习如何使用 Java 以编程方式搜索文档中的全文。"
tags: ['find in files and folder using Java', 'full text search', 'Full Text Search in Java', 'search via indexing']
categories: ['GroupDocs.Search Product Family']
---

全文搜索是一种在文档集合中搜索文本/查询的方法。这种方法可以快速找到一个术语/短语的所有实例，并且它通过使用文本索引来工作。在本文中，我们将学习如何使用 Java 以编程方式搜索文档中的全文。



{{< figure align=center src="images/TextSearch-1.png" alt="全文搜索">}}


在此之后，您可以实施各种搜索技术并为文字处理文档、电子表格、演示文稿、HTML 文件、PDF 文件、电子书、电子邮件、ZIP 存档和许多其他 [文档格式][1] 构建搜索解决方案。

以下主题涵盖以下内容：

* [用于全文搜索的 Java API][2]
* [全文检索][3]
* [在 Java 中执行搜索][4]
* [突出显示搜索结果][5]

## 用于全文搜索的 Java API {#full-text-search-java-api}

[GroupDocs.Search][6]提供了[全文搜索Java API][7]，可以集成到任何应用程序中，无需任何第三方工具和软件依赖。它允许您[搜索大量文档格式][8]。可以使用 API 执行的一些搜索技术如下：

* 区分大小写搜索
* 正则表达式搜索
* 分面搜索
* 模糊搜索
* 同音字搜索
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
        <version>21.3</version> 
</dependency>
```

## 使用 Java 进行全文搜索 {#full-text-search}

在文件夹中存储的文件中执行搜索有两个步骤。

* 索引
* 执行搜索

## 使用 Java 索引文件

索引拥有所有文档的扫描文本。因此，当您要执行搜索操作时，只引用索引，而不是原始文档的文本。为了能够立即搜索具有相同或不同文件格式的数千个文档，您需要创建一个索引并将这些文档添加到其中。当文档被索引时，索引已准备好处理搜索查询。

以下简单的两行代码创建一个索引，并将文档文件夹添加到索引中。

```
Index index = new Index("indexingFolderPath");
index.add("documentsFolderPath");
```

## 在 Java 中执行搜索 {#perform-search}

在索引多个相同或不同格式（如 Word、PDF、Excel 和 HTML）的文档后，我们可以继续处理对它们的特定搜索查询（搜索词“Draw”）。以下是如何使用 Java 对文件夹内的多个文档执行文本搜索的步骤：

* 指定文档的源文件夹和索引文件夹。
* 使用索引文件夹创建[索引][10]。
* 将源文件夹添加到索引中。
* 准备查询字符串。
* 使用 Index 类的 [search][11] 方法执行搜索。
* 遍历每个搜索结果的每个文档的属性。

以下源代码在 Java 中对提供的文件夹的所有文档执行文本搜索。

```
// 使用 Java 在文件夹中搜索多个 PDF、Word、Excel、HTML 文档中的指定文本
Index index = new Index("path/indexingFolder");
index.add("path/documentsFolderPath");

// 在索引中搜索指定文本
SearchResult result = index.search("Draw");

for (int i = 0; i < result.getDocumentCount(); i++) {
    FoundDocument document = result.getFoundDocument(i);
    System.out.println("Document Path: " + document.getDocumentInfo().getFilePath());
    System.out.println("Occurrence : " + document.getOccurrenceCount());
}
```

我们将获取文档路径和搜索词在该指定文件夹的所有文档中出现的次数。这是可视化的屏幕截图。



{{< figure align=center src="images/SearchTextOutput.jpg" alt="完整搜索文本输出">}}


## 在 Java 中突出显示文本搜索结果 {#highlight-search-results}

现在让我们执行相同的全文搜索并突出显示与您的查询匹配的所有匹配项。

以下步骤显示如何突出显示文本搜索结果：

* 创建[索引][12]并将文档文件夹添加到索引中。
* 准备查询字符串。
* 使用 [search][13] 方法搜索文件夹。
* 在遍历结果时，使用 [HtmlHighlighter][14] 创建荧光笔。
* 使用高亮方法突出显示搜索结果。

以下代码使用 Java 生成带有突出显示的搜索结果的 HTML 输出。

```
// 在Java中突出显示文件夹中多个文档的全文搜索结果
Index index = new Index("path/indexingFolder");
index.add("path/documentsFolderPath"); // Synchronous indexing documents from the specified folder

String query = "draw"; // Specify a search query
SearchResult result = index.search(query); // Searching in the index

for (int i = 0; i < result.getDocumentCount(); i++) 
{
    FoundDocument document = result.getFoundDocument(i);

    String path = "path/Highlighted-"+ i +".html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); 
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter); // Creating the highlighter
    index.highlight(document, highlighter); // Generates HTML formatted output document with highlighted search results
}
```

作为输出，我们将获得多个 HTML 文件。每个文件将显示单独文档的内容（例如 excel.xlsx、source.docx、target.docx），并带有突出显示的搜索词/词。下面给出的是使用上述代码获得的 DOCX 文件、TXT 文件和 PDF 文件的突出显示的 HTML 输出。



{{< figure align=center src="images/full-text-search-with-groupdocs.jpg" alt="使用 Java 突出显示内容中的全文搜索结果">}}


## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][15] 以便在没有评估限制的情况下使用 API。

## 结论

在本文中，我们学习了在 Java 中搜索文件夹的多个文档中的文本。此外，我们讨论了如何使用 [GroupDocs.Search for Java][16] 以编程方式突出显示 MS Word 文件、TXT 文件和 PDF 文件的 HTML 格式的搜索结果文本。

您可以使用 [documentation][17] 了解有关 API 的更多信息。 [GitHub][18] 上提供了更多示例。如有疑问，请通过 [论坛][19] 联系我们。

## 也可以看看

* [用 C# 构建您的全文搜索解决方案][20]
* [Java 中的 PDF 中的单词搜索和替换文本][21]







[1]: https://docs.groupdocs.com/search/java/supported-document-formats/
[2]: #full-text-search-java-api
[3]: #full-text-search
[4]: #perform-search
[5]: #highlight-search-results
[6]: https://products.groupdocs.com/search/
[7]: https://products.groupdocs.com/search/java/
[8]: https://docs.groupdocs.com/search/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/search
[10]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[11]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery)
[12]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index
[13]: https://apireference.groupdocs.com/search/java/com.groupdocs.search/Index#search(com.groupdocs.search.SearchQuery)
[14]: https://apireference.groupdocs.com/search/java/com.groupdocs.search.highlighters/HtmlHighlighter
[15]: https://purchase.groupdocs.com/temporary-license
[16]: https://products.groupdocs.com/search/java/
[17]: https://docs.groupdocs.com/search/
[18]: https://github.com/groupdocs-search
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[21]: https://blog.groupdocs.com/2022/03/08/find-and-replace-text-in-pdf-in-java/


