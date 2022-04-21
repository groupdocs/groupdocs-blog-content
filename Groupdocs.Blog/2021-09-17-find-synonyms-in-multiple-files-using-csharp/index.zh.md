---
title: "使用 C# 在多个文件中搜索同义词"
date: Fri, 17 Sep 2021 10:57:00 +0000
draft: false
url: /zh/2021/09/17/在多个文件中查找同义词-使用-csharp/
author: 'Shoaib Khan'
summary: "在另一篇文章中，我们看到了什么是同义词，以及如何获取任何单词的所有同义词。如何在不同的文档中找到这些同义词。本文将指导您如何使用 C# 在多个文件中搜索任何特定查询（单词）的同义词。"
tags: ['Find Synonyms', 'Find Synonyms in CSharp', 'Search Synonyms', 'Search Synonyms in CSharp', 'Search Synonyms in Files']
categories: ['GroupDocs.Search Product Family']
---

在另一篇文章中，我们已经看到什么是同义词，以及[如何获取任何单词的所有同义词][1]。如何在不同的文档中找到这些同义词？本文将指导您如何使用 C# 在多个文件中搜索任何特定查询（单词）的同义词。

下面将介绍以下主题：

* [.NET API - 同义词搜索][2]
* [使用 C# 在文档中查找同义词][3]
* [使用 C# 显示同义词搜索结果][4]
* [完整代码 - 搜索和打印同义词搜索结果][5]

## .NET API 用于在多个文件中搜索同义词 {#synonym-search-dotnet-api}

[GroupDocs.Search][6] 提供.NET API，允许在指定文件夹的多个文件中搜索任何单词及其同义词。我将在本文所示示例中使用此 API。它允许您[搜索大量文档格式][7]。除了查找同义词外，GroupDocs.Search for .NET 还支持更多的搜索技术，包括：

* 模糊搜索
*区分大小写的搜索
* 同音字搜索
* 正则表达式搜索
* 外卡搜索

您可以从 [下载部分][8] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][9] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Search
```

## 使用 C# 在多个文件中查找同义词 {#synonyms-in-different-files}

这些步骤显示了如何使用 C# 在文件夹内的文件中搜索同义词（具有相似含义的单词）。

* 定义搜索查询、索引文件夹和文档的文件夹。
* 使用 [Index][10] 类创建具有已定义索引文件夹的索引。
* 将文档的文件夹添加到索引中。
* 创建 [SearchOptions][11] 并将 [UseSynonymSearch][12] 设置为 true。
* 调用Index类的[Search][13]方法，传递查询和搜索选项。
* 要打印摘要，请使用检索到的 [SearchResult][14] 的属性。

源代码显示了如何使用 C# 在文件夹的所有文件中查找所有同义词

```
// 使用 C# 在多个文件和文件夹中搜索同义词
string query = "make";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
index.Add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions();
options.UseSynonymSearch = true; // Enabling Synonym Search

// 搜索单词“make”
// 除了单词“make”，还将搜索同义词“do, cause, get, ...”
SearchResult result = index.Search(query, options);
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Occurrences: " + result.OccurrenceCount);
```

```
Query: **make**
Documents: 2
Occurrences: 22
```

## 使用 C# 打印同义词搜索结果 {#print-synonym-search}

在获取所有同义词及其在每个文档中出现的次数后，以下步骤将详细打印结果。

* 遍历使用上述代码检索到的搜索结果。
* 使用 [GetFoundDocument][16] 方法获取每个 [FoundDocument][15]。
* 打印每个 FoundDocument 的相应属性。
* 遍历每个FoundDocument中的[FoundFields][17]，得到[Found Document Field][18]。
* 从每个 FoundDocumentField 中，您可以获取其术语及其在每个文档中的出现次数。

以下源代码使用 C# 打印同义词搜索结果以及每个搜索词的出现次数。

```
// 在 C# 中打印同义词搜索结果
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Total occurrences: " + result.OccurrenceCount + "\n");
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("Document: " + document.DocumentInfo.FilePath);
    Console.WriteLine("Occurrences: " + document.OccurrenceCount);
    for (int j = 0; j < document.FoundFields.Length; j++)
    {
        FoundDocumentField field = document.FoundFields[j];
        Console.WriteLine("\tField: " + field.FieldName);
        Console.WriteLine("\tOccurrences: " + document.OccurrenceCount);
        // Printing found terms
        if (field.Terms != null)
        {
            for (int k = 0; k < field.Terms.Length; k++)
            {
                Console.WriteLine("\t\t" + field.Terms[k].PadRight(20) + field.TermsOccurrences[k]);
            }
        }
    }
}
```

```
Query: **make**
Documents: 2
Total occurrences: 22

Document: C:/documents/sample.docx
Occurrences: 6
    Field: content
    Occurrences: 6
        make             1
        get                 2
        cause            1
        do                  2
Document: C:/documents/sample.txt
Occurrences: 16
    Field: content
    Occurrences: 16
        get                  4
        cause             1
        do                  11
```

## 使用 C# 搜索同义词和打印结果 - 完整代码 {#search-and-print-synonyms-code}

这是完整的源代码，它首先根据提供的查询找到所有同义词，然后使用 C# 打印该文件夹内每个文档中所有同义词的所有出现。

```
// 在多个文件和文件夹中搜索同义词并使用 C# 打印结果
string query = "make";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
// 索引指定文件夹中的文档
index.Add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions();
options.UseSynonymSearch = true; // Enabling synonym search

// 搜索单词“make”
// 除了单词“make”之外，还将搜索单词“do, cause, get, ...”
SearchResult result = index.Search(query, options);

// 打印结果
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Total occurrences: " + result.OccurrenceCount + "\n");
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("Document: " + document.DocumentInfo.FilePath);
    Console.WriteLine("Occurrences: " + document.OccurrenceCount);
    for (int j = 0; j < document.FoundFields.Length; j++)
    {
        FoundDocumentField field = document.FoundFields[j];
        Console.WriteLine("\tField: " + field.FieldName);
        Console.WriteLine("\tOccurrences: " + document.OccurrenceCount);
        // Printing found terms
        if (field.Terms != null)
        {
            for (int k = 0; k < field.Terms.Length; k++)
            {
                Console.WriteLine("\t\t" + field.Terms[k].PadRight(20) + field.TermsOccurrences[k]);
            }
        }
    }
}
```

## 结论

最后，您已经学习了如何使用 C# 在指定文件夹内的多个文档中查找特定单词及其同义词。您可以尝试开发自己的 .NET 应用程序来搜索多个文件中的任何单词及其同义词。

从文档中了解 [关于 .NET 搜索自动化 API][19] 的更多信息。要体验这些功能，您可以查看 [GitHub][20] 存储库中的示例。通过 [论坛][21] 联系我们进行任何查询。

## 也可以看看

* [使用 C# 查找单词的同义词][22]
* [用 C# 构建您的全文搜索解决方案][23]
* [使用 C# 文本索引和搜索您的目录][24]







[1]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp
[2]: #synonym-search-dotnet-api
[3]: #synonyms-in-different-files
[4]: #print-synonym-search
[5]: #search-and-print-synonyms-code
[6]: https://products.groupdocs.com/search/
[7]: https://docs.groupdocs.com/search/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/search
[9]: https://www.nuget.org/packages/groupdocs.search
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions
[12]: https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usesynonymsearch
[13]: https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index
[14]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult
[15]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument
[16]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument
[17]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/foundfields
[18]: https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocumentfield
[19]: https://docs.groupdocs.com/search/net/
[20]: https://github.com/groupdocs-search
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp
[23]: https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/
[24]: https://blog.groupdocs.com/2020/05/29/search-text-by-indexing-in-csharp-net/


