---
title: "使用 C# 查找单词的同义词"
date: Tue, 14 Sep 2021 13:40:00 +0000
draft: false
url: /zh/2021/09/14/使用 csharp 查找单词的同义词/
author: 'Shoaib Khan'
summary: "同义词是与另一个词具有完全相同或几乎相同含义的词。我们通常使用同义词来避免重复使用同一个词。作为开发人员，您可能需要找出所有具有相同含义的单词，以便进行搜索或文档分析。本文将指导您**如何使用 .NET API 找出 C# 中任何特定单词的所有同义词**。此外，您还可以获得根据同一个词的不同含义排列的这些同义词的不同组。"
tags: ['Find Synonyms', 'Find Synonyms in CSharp', 'Search Synonyms', 'Search Synonyms in CSharp']
categories: ['GroupDocs.Search Product Family']
---

同义词是与另一个词具有完全相同或几乎相同含义的词。我们通常使用同义词来避免重复使用同一个词。作为开发人员，您可能需要找出所有具有相同含义的单词，以便进行搜索或文档分析。本文将指导您**如何使用 .NET API 找出 C# 中任何特定单词的所有同义词**。此外，您还可以获得根据同一个词的不同含义排列的这些同义词的不同组。

下面将介绍以下主题：

* [.NET API - 查找同义词][1]
* [获取C#中任意单词的同义词][2]
* [获取同义词 - 按不同含义分组][3]

## 用于查找同义词的 .NET API {#find-synonyms-dotnet-api}

[GroupDocs.Search][4] 提供了允许查找任何单词的同义词的 .NET API。它还允许在文件夹内的多个文档中搜索该单词及其所有同义词。它支持不同的搜索技术来[搜索大量文档格式][5]。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Search
```

## 在 C# 中查找任何单词的同义词 {#get-synonyms}

在这里，您可以找到您脑海中可能出现的单词的同义词。要获取 .NET 应用程序中任何单词的同义词列表，您只需使用以下步骤和下面的 C# 代码：

* 定义查询/单词以查找其同义词。
* 使用 [Index][8] 类创建索引。
* 使用 [GetSynonyms][9] 方法从同义词词典中获取同义词集合。
* 遍历同义词集合以处理每个同义词。

```
// 获取 C# 中任何单词的所有同义词
string query = "make";
string[] synonyms = new Index().Dictionaries.SynonymDictionary.GetSynonyms(query);
Console.WriteLine("Synonyms for '" + query + "':");

for (int i = 0; i < synonyms.Length; i++)
{
    Console.WriteLine("- " + synonyms[i]);
}
```

以下是上述 C# 代码的输出，其中显示了提供的单词“make”的所有同义词。

```
Synonyms for '**make**':
 - brand
 - construct
 - build
 - cook
 - fix
 - ready
 - prepare
 - induce
 - stimulate
 - cause
 - have
 - get
 - create
 - do
 - produce
 - reach
 - attain
 - hit
 - gain 
```

## 使用 C# 查找按单词的不同含义分组的同义词 {#get-synonyms-as-group}

根据情况，一个词可能有许多不同的含义。所以它的同义词也可以根据用途的不同进行分组。以下步骤和源代码根据 C# 中该词的不同含义为您提供不同的同义词组。

*定义单词（查询）以查找其同义词。
* 使用 [Index][10] 类创建索引。
* 使用 [GetSynonymGroups][11] 方法从同义词词典中获取同义词组的集合。
* 遍历同义词组集合以使用每个组或同义词。

```
// 在 C# 中获取同义词组
string query = "make";
string[][] groups = new Index().Dictionaries.SynonymDictionary.GetSynonymGroups(query);

Console.WriteLine("Synonyms for " + query + ":");
for (int i = 0; i < groups.Length; i++)
{
    Console.Write("- ");
    string[] group = groups[i];
    for (int j = 0; j < group.Length; j++)
    {
        Console.Write(group[j] + " ");
    }
    Console.WriteLine();
}
```

以下是上述 C# 代码的输出，显示了提供的单词“make”的所有同义词，根据其不同的含义进行分组。

```
Synonyms for **make**:

 - attain gain hit **make** reach 
 - create **make** produce 
 - do **make** 
 - cause get have induce **make** stimulate 
 - cook fix **make** prepare ready 
 - build construct **make** 
 - brand **make** 
```

接下来，我们将在另一篇文章中看到，[如何在 C# 中的文件夹的多个文件中查找任何单词及其同义词][12]。

## 结论

最后，您已经学会了如何在 C# 中查找任何特定单词的可能同义词。此外，我们讨论了如何获取按同一单词的不同含义分组的所有同义词。您可以尝试开发自己的 .NET 应用程序来搜索任何单词的同义词。

从文档中了解 [关于 .NET 搜索自动化 API][13] 的更多信息。要体验这些功能，您可以查看 [GitHub][14] 存储库中的示例。通过 [论坛][15] 联系我们进行任何查询。

## 也可以看看

* [使用 C# 在多个文件中搜索同义词][16]
* [使用 C# 中的情感分析对客户反馈进行分类][17]







[1]: #find-synonyms-dotnet-api
[2]: #get-synonyms
[3]: #get-synonyms-as-group
[4]: https://products.groupdocs.com/search/
[5]: https://docs.groupdocs.com/search/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/search
[7]: https://www.nuget.org/packages/groupdocs.search
[8]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[9]: https://apireference.groupdocs.com/search/net/groupdocs.search.dictionaries/synonymdictionary/methods/getsynonyms
[10]: https://apireference.groupdocs.com/search/net/groupdocs.search/index
[11]: https://apireference.groupdocs.com/search/net/groupdocs.search.dictionaries/synonymdictionary/methods/getsynonymgroups
[12]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp
[13]: https://docs.groupdocs.com/search/net/
[14]: https://github.com/groupdocs-search
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp
[17]: https://blog.groupdocs.com/2020/06/17/classify-customers-feedback-using-sentiment-analysis-in-csharp/


