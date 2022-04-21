---
title: "用 C# 构建您的全文搜索解决方案"
date: Thu, 03 Jun 2021 00:20:00 +0000
draft: false
url: /zh/2021/06/03/build-your-full-text-search-solution-in-csharp/
aliases:
- /2019/11/22/build-your-full-text-search-solution-in-csharp/
author: 'Shoaib Khan'
summary: "Full-text search is basically a more advanced way to search a text/query over a collection of documents. This approach quickly finds all instances of a term and it works by using text indexes. In this article, we will learn, how to programmatically search full-text in documents using C#."
tags: ['full text search', 'Full Text Search Csharp']
categories: ['GroupDocs.Search Product Family']
---

在我们深入细节之前，让我们先了解一下全文搜索技术。全文搜索基本上是在文档集合中搜索文本/查询的更高级方法。这种方法可以快速找到一个术语的所有实例，并且它通过使用文本索引来工作。在本文中，我们将学习如何使用 C# 以编程方式在文档中搜索全文。

在此之后，您可以实施各种搜索技术来搜索文字处理文档、电子表格、演示文稿、HTML 文件、PDF 电子书、电子邮件、ZIP 档案和许多其他文件中的文本。

全文搜索实现的示例之一是在文字处理器和文本编辑器中。它可以帮助您在文档中的任何位置查找短语或单词。



{{< figure align=center src="images/TextSearch-1.png" alt="全文搜索">}}


以下主题涵盖以下内容：

* [用于全文搜索的.NET API][2]
* [全文检索][3]
* [在 C# 中执行搜索][4]
* [突出显示搜索结果][5]

## 用于文本搜索的 .NET API {#full-text-search-dotnet-api}

[GroupDocs.Search for .NET][6] 是一个后端搜索 API，它允许全文搜索，并且可以集成到任何 .NET 应用程序中，而无需任何第三方工具或软件依赖。它允许您在您的应用程序中[搜索多种文档格式][7]。

您可以从 [下载部分][8] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][9] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Search
```

## 使用 C# 进行全文搜索 {#full-text-search-in-csharp}

执行或实施全文搜索有两个主要步骤。

* 索引
* 执行搜索

## 索引

为了能够立即搜索具有相同或不同文件格式的数千个文档，您需要创建一个索引并将这些文档添加到其中。

### **什么是索引？**

索引拥有所有文档的扫描文本。因此，当您要执行搜索操作（搜索特定查询）时，只引用索引，而不是原始文档的文本。

### **索引创建**

可以在内存中或磁盘上创建索引。退出程序后无法保存在内存中创建的索引。相反，在磁盘上创建的索引可能会在将来加载以继续工作。以下示例显示如何在磁盘上创建索引。

```
Index index = new Index("indexPath/FolderName/");
```

当文档被索引时，索引已准备好处理搜索查询。以下是可以使用 GroupDocs.Search for .NET 执行的一些搜索技术：

* 区分大小写搜索
* 正则表达式搜索
* 短语搜索
* 分面搜索
* 同义词搜索
* 通配符搜索

## 在 C# 中执行搜索 {#perform-search-in-csharp}

从一个用例开始。如果我们有多个文档（Word、PDF、Excel 和 HTML）并且我们想要对它们执行特定的搜索查询（搜索词“视频”）。

以下是如何对文件夹中的多个文档执行文本搜索的步骤：

* 决定源文件文件夹和索引文件夹。
* 准备查询字符串。
* 使用索引文件夹创建[索引][10]。
* 将源文档文件夹添加到索引中。
* 使用 [Search][11] 方法 [Index][12] 类执行搜索。
* 遍历和搜索每个文档属性的结果。

以下源代码使用 C# 对所提供文件夹的所有文档执行文本搜索。

```
// 在 C# 中提供的文件夹的所有文档中搜索查询文本
string indexFolder =  @"indexPath/GroupDocs/index/";
string documentsFolder = @"documentPath/GroupDocs/source/";
string query = "video";

// 在指定文件夹中创建索引并将文档文件夹添加到索引
Index index = new Index(indexFolder);
index.Add(documentsFolder);

// 在索引中搜索
SearchResult result = index.Search(query);
Console.WriteLine("Documents found: " + result.DocumentCount);

// 遍历Search Result的每个文档
foreach (FoundDocument document in result)
{
    Console.WriteLine("Document Path : " + document.DocumentInfo.FilePath);
    Console.WriteLine("Occurance : " + document.OccurrenceCount);
}
```

我们将获取文档文件夹中所有可用文档中的文档路径和搜索词出现的次数。这是可视化的屏幕截图。



{{< figure align=center src="images/SearchTextOutput.jpg" alt="完整搜索文本输出">}}


## 在 C# 中突出显示文本搜索结果 {#highlight-search-results-in-csharp}

现在让我们执行相同的文本搜索，但这次我们将突出显示与查询匹配的所有匹配项。

以下步骤显示如何突出显示文本搜索结果：

* 准备查询字符串。
* 使用索引文件夹路径创建 [Index][13]。
* 将源文档文件夹添加到索引中。
* 使用[搜索][14]方法搜索文件夹。
* 在遍历搜索结果时，创建[Highlighter][15]。
* 使用 [Index][17] 类的 [Highlight][16] 方法突出显示搜索结果。

以下代码使用 C# 生成带有突出显示的搜索结果的 HTML 输出。

```
string indexFolder =    @"indexPath/GroupDocs/index/";
string documentFolder = @"documentPath/GroupDocs/source/";
string query = "draw";

// 在指定文件夹中创建索引并将文档文件夹添加到索引
Index index = new Index(indexFolder);
index.Add(documentFolder);

// 搜索查询词
SearchResult result = index.Search(query);

// 突出显示文本中的所有出现
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
                    
    string path = indexFolder + "Highlighted-"+ i +".html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); 
    Highlighter highlighter = new HtmlHighlighter(outputAdapter); 
    index.Highlight(document, highlighter);
}
```

作为输出，我们将获得多个 HTML 文件。每个文件将显示不同文档的内容（例如 excel.xlsx、source.docx、target.docx），并带有突出显示的搜索词/词。下面给出的是 DOCX 文件的突出显示的 HTML 输出。



{{< figure align=center src="images/highlight-text-search-result.jpg" alt="在内容中突出显示全文搜索结果">}}


## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][18] 以便在没有评估限制的情况下使用 API。

## 结论

在本文中，我们学习了使用 C# 在文件夹的多个文档中搜索文本。此外，我们还讨论了如何以编程方式突出显示 HTML 格式的搜索结果文本。

您可以使用 [documentation][19] 了解有关 API 的更多信息。 [GitHub][20] 上提供了更多示例。如有疑问，请通过 [论坛][21] 联系我们。

## 也可以看看

* [用Java构建全文搜索解决方案][22]
* [使用 C# 查找单词的同义词][23]
* [使用 C# 在多个文件中搜索同义词][24]
* [使用 C# 查找和替换 PDF 中的文本][25]
* [使用C#查找和替换Word文档中的单词][26]







[1]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[2]: #full-text-search-dotnet-api
[3]: #full-text-search-in-csharp
[4]: #perform-search-in-csharp
[5]: #highlight-search-results-in-csharp
[6]: https://products.groupdocs.com/search/net
[7]: https://docs.groupdocs.com/search/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/search
[9]: https://www.nuget.org/packages/groupdocs.search
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[12]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[13]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[14]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[15]: https://apireference.groupdocs.com/search/net/groupdocs.search.highlighters/highlighter
[16]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/highlight/index
[17]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[18]: https://purchase.groupdocs.com/temporary-license
[19]: https://docs.groupdocs.com/search/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/
[23]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp/
[24]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp/
[25]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[26]: https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/


