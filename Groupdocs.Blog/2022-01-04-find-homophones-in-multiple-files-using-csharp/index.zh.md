---
title: "使用 C# 在多个文件中查找同音字"
date: Tue, 04 Jan 2022 10:54:00 +0000
draft: false
url: /zh/2022/01/04/在多个文件中查找同音字-使用-csharp/
author: 'Shoaib Khan'
summary: 'Words that sound the same but are different in meanings or spellings are **Homophones**. Whereas, the words that spell the same, but differ in meaning or pronunciation are **Homographs**. **Homonyms** can either be homophone or homograph; or both. Let us not confuse and automate it. In this article, you will learn **how to search homophones within multiple documents using C#**.

本文将涵盖以下主题：

* .NET API - 同音字搜索
* 使用 C# 在文档中查找同音字
* 管理同音字典'
tags: ['Find Homophones', 'Find Homophones in CSharp', 'Find Homophones in Files', 'Homophones']
categories: ['GroupDocs.Search Product Family']
---

发音相同但含义或拼写不同的单词是**同音字**。然而，拼写相同但含义或发音不同的单词是**同形异义词**。 **同音异义词**可以是同音异义词或同形异义词；或两者。让我们不要混淆和自动化它。在本文中，您将学习**如何使用 C#** 在多个文档中搜索同音字。

{{< figure align=center src="images/Search-Homophones-in-Files.jpg" alt="使用 GroupDocs 在文件中搜索同音字">}}


下面将介绍以下主题：

* [.NET API - 同音字搜索](#homophone-search-dotnet-api)
* [使用 C# 在文档中查找同音字](#homophone-in-different-files)
* [播放同音字搜索结果](#print-homophone-search)

## .NET API 用于在多个文件中搜索同音字 {#homophone-search-dotnet-api}

[GroupDocs.Search](https://products.groupdocs.com/search/) 展示了 .NET API ([GroupDocs.Search for .NET](https://products.groupdocs.com/search/net/))允许在指定文件夹的多个文件中搜索单词及其同音字。我们将在本文的示例中使用此 API。它可以搜索各种不同格式的内容。除了查找同音字外，API 还支持根据需要进行许多其他搜索方式。一些支持的搜索技术如下：

* 同义词搜索
* 短语搜索
* 模糊搜索
* 区分大小写的搜索
* 正则表达式搜索
* 外卡搜索

您可以从 [下载部分](https://downloads.groupdocs.com/search) 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.search) 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Search
```

## 使用 C# 在多个文件中查找同音字 {#homophone-in-different-files}

以下步骤指导我们如何使用 C# 在文件夹中的文件中搜索同音字（具有相似声音/发音的单词) 。

* 定义搜索查询、索引文件夹和包含文件的文件夹。
* 使用定义的索引文件夹创建[索引](https://apireference.groupdocs.com/search/net/groupdocs.search/index)。
* 将文档的文件夹添加到创建的索引中。
* 定义 [SearchOptions](https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions) 并将 [UseHomophoneSearch](https://apireference.groupdocs.com/search/net/groupdocs.search.options/searchoptions/properties/usehomophonesearch) 设置为 true。
* 通过使用查询和搜索选项调用 [Search](https://apireference.groupdocs.com/search/net/groupdocs.search/index/methods/search/index) 方法搜索所有同音字。
* 使用检索到的 [SearchResult](https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult) 的属性使用摘要。

以下 C# 源代码在已定义文件夹的所有文件中查找所有同音字。此外，您还可以[管理您的同音词词典](https://docs.groupdocs.com/search/net/homophone-dictionary/)。

```
// 使用 C# 在多个文件和文件夹中搜索同音字
string query = "right";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
index.Add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions()
{
    UseHomophoneSearch = true // Enabling Homophone Search
}; 

// 搜索单词“正确”
// 除了单词“right”之外，还会搜索单词“rite, wright, write, ...”
SearchResult result = index.Search(query, options);
Console.WriteLine("Query: " + query);
Console.WriteLine("Documents: " + result.DocumentCount);
Console.WriteLine("Occurrences: " + result.OccurrenceCount);
```

上述代码的输出如下：

```
Query: right
Documents: 2
Occurrences: 17
```

## 使用 C# 打印同音字搜索结果 {#print-homophone-search}

在获取所有同音字及其在每个文档中出现的次数后，按照下面提到的步骤呈现同音字搜索结果。

* 遍历之前检索到的同音字搜索结果。
* 使用 [GetFoundDocument()](https://apireference.groupdocs.com/search/net/groupdocs.search.results/searchresult/methods/getfounddocument) 方法将每个文档作为 [FoundDocument](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument) 获取。
* 根据需要使用每个 FoundDocument 的属性。
* 现在，遍历 FoundDocument 的 [FoundFields](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocument/properties/foundfields) 得到 [FoundDocumentField](https://apireference.groupdocs.com/search/net/groupdocs.search.results/founddocumentfield)。
* 最后，从每个 FoundDocumentField 中，获取其术语及其在每个文档中的出现。

以下 C# 源代码打印同音字搜索结果以及每个搜索词的出现次数。

```
// 在 C# 中打印同音字搜索结果
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

## 使用 C# 搜索同音字并打印结果 - 完整代码 {#search-and-print-synonyms-code}

以下 C# 代码总结了上述步骤，它首先根据查询找到所有同音字，然后打印提供的文件夹内每个文档中所有同音字的所有出现。

```
// 在多个文件和文件夹中搜索同音字，然后使用 C# 打印结果
string query = "right";
string indexFolder = @"path\indexFolder";
string documentsFolder = @"path\documentsFolder";

// 在指定文件夹中创建索引
Index index = new Index(indexFolder);
// 索引指定文件夹中的文档
index.Add(documentsFolder);

// 创建搜索选项对象
SearchOptions options = new SearchOptions()
{
    UseHomophoneSearch = true // Enabling Homophone Search
}; 

// 搜索单词“正确”
// 除了单词“right”之外，还会搜索单词“rite, wright, write, ...”
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

综上所述，您已经学会了如何使用 C# 从指定文件夹的多个文档中查找单词及其同音字。您可以尝试使用 **GroupDocs.Search for .NET** 构建自己的 .NET 应用程序，以在多个文件中搜索同音字。

从文档中了解更多 [关于 .NET 搜索自动化 API](https://docs.groupdocs.com/search/net/)。要体验这些功能，您可以查看 [GitHub](https://github.com/groupdocs-search) 存储库中的可用示例。通过 [论坛](https://forum.groupdocs.com/) 联系我们进行任何查询。

## 也可以看看

* [使用 C# 查找单词的同义词](https://blog.groupdocs.com/2021/09/14/find-synonyms-of-words-using-csharp)
* [用 C# 构建您的全文搜索解决方案](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)
* [使用 C# 进行文本索引和搜索您的目录](https://blog.groupdocs.com/2020/05/29/search-text-by-indexing-in-csharp-net/)