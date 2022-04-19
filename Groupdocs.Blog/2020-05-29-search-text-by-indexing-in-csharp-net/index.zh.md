---
title: "使用 C# 文本索引和搜索您的目录"
date: Fri, 29 May 2020 07:30:00 +0000
draft: false
url: /zh/2020/05/29/search-text-by-indexing-in-csharp-net/
author: 'Shoaib Khan'
summary: "使用 .NET API，您可以按部分执行搜索并指定 C# 中的搜索线程数。当您在包含数千个文档的大型索引中搜索文本时，此功能将更加有用。此外，您现在可以获取开始和结束时间，以及获取搜索结果的总搜索时间。"
tags: ['search in chunk', 'search text in csharp', 'search text in folders in csharp', 'search text in parts', 'text searching using csharp']
categories: ['GroupDocs.Search Product Family']
---

使用 .NET API，您可以按部分执行搜索并指定 C# 中的搜索线程数。当您在包含数千个文档的大型索引中搜索文本时，此功能将更加有用。此外，您现在可以获取开始和结束时间，以及获取搜索结果的总搜索时间。

以下 codf 片段显示了如何创建索引，然后使用 [GroupDocs.Search for .NET][1] 从 C# 中提到的文件夹中搜索块中的文本。为了利用最佳性能和更新的功能，我建议您[安装][2] 并使用最新版本的 API。

## 在 C# 中通过索引搜索文本

以下示例显示如何按部分/块执行搜索。

* 使用您的索引文件夹创建 [索引][3]。
* [添加][4] 您在创建的索引中的文档文件夹。
* 设置 [Search Option][5] 并将 [IsChunkSearch][6] 设置为 true 以按块/部分搜索
* 通过提供搜索查询和搜索选项来调用索引的 [Search][7] 方法。
* 现在在结果中，您可以使用 [Search Next][8] 遍历每个段，并将 [Chunk Search Token][9] 作为参数传递给它。

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
string query = "Einstein";
// Creating an index in the specified folder
Index index = new Index(indexFolder);
// Indexing documents from the specified folder
index.Add(documentsFolder);
// Creating a search options instance
SearchOptions options = new SearchOptions();
options.IsChunkSearch = true; // Enabling the search by chunks
// Starting the search by chunks
SearchResult result = index.Search(query, options);
Console.WriteLine("Document count: " + result.DocumentCount);
Console.WriteLine("Occurrence count: " + result.OccurrenceCount);
// Continuing the search by chunks
while (result.NextChunkSearchToken != null)
{
    result = index.SearchNext(result.NextChunkSearchToken);
    Console.WriteLine("Document count: " + result.DocumentCount);
    Console.WriteLine("Occurrence count: " + result.OccurrenceCount);
}
```

对于与 [.NET Search API][10] 相关的任何建议、困惑或查询，您可以使用 [论坛][11] 进行快速回复。您可以快速创建一个线程来分享您的想法。

## 也可以看看

* [使用 C# 查找和替换 PDF 中的文本][12]
* [使用C#查找和替换Word文档中的单词][13]







[1]: https://products.groupdocs.com/search/net
[2]: https://www.nuget.org/packages/GroupDocs.Search/
[3]: https://apireference.groupdocs.com/net/search/groupdocs.search/index
[4]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/add
[5]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions
[6]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/ischunksearch
[7]: https://apireference.groupdocs.com/net/search/groupdocs.search/index/methods/search/index
[8]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/searchnext
[9]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/properties/nextchunksearchtoken
[10]: https://products.groupdocs.com/search/net
[11]: https://forum.groupdocs.com/c/search
[12]: https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/
[13]: https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/


