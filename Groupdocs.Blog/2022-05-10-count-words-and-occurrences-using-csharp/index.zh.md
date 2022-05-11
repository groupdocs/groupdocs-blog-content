---
title: "使用 C# 计算文档中每个单词的单词和出现次数"
seoTitle: "使用 C# 计算文档中每个单词的单词和出现次数"
description: "使用 .NET 文档解析 API 在 C# 中计算 PDF、Word、Excel、PowerPoint 和电子邮件文档中的单词数及其出现次数。"
date: Tue, 10 May 2022 16:33:57 +0000
draft: false
url: /zh/2022/05/10/count-words-and-occurrences-using-csharp
author: "Shoaib Khan"
summary: "本文演示如何使用 C# 以编程方式计算 PDF、Word、Excel、PowerPoint、电子书、标记和电子邮件文档格式中的单词和每个单词的单词出现次数。"
tags: ['GroupDocs.Parser for .NET']
categories: ['GroupDocs.Parser Product Family']
---

重复数据会降低内容的价值。作为一名作家，你必须遵循[DRY][1]（不要重复自己）的原则。字数或每个单词的出现次数等统计数据可以让您分析内容，但很难手动对多个文档进行分析。因此，本文演示了如何使用 C# **以编程方式计算单词数**以及 PDF、Word、Excel、PowerPoint、电子书、标记和电子邮件文档格式中每个单词的单词出现次数。

## .NET API 来计算单词和出现次数

[GroupDocs.Parser][2] 为开发者提供文档解析解决方案。为了从文档中提取文本并计算出现次数，我们将使用它的 [GroupDocs.Parser for .NET][3]。该 API 还允许从一长串 [支持的文档][4] 格式（如文字处理文档、演示文稿、电子表格、电子邮件、数据库、电子书等）中提取图像和元数据。

您可以从 [下载部分][5] 下载 DLL 或 MSI 安装程序，或者通过 [NuGet][6] 将其包添加到您的 .NET 应用程序来安装 API。

```
PM> Install-Package GroupDocs.Parser
```

## 使用 C# 计算单词 {#count-words}

对于单词的计数，主要是解析和提取文档的全部内容。提取文本后，我们可以将其内容拆分为句子和单词的集合。以下步骤允许使用 C# 计算文档中的单词。

- 使用 [Parser][7] 类加载文档。
- 将加载文档的文本获取到 [TextReader][8]。
- [Get][9] 来自 TextReader 的文档文本作为字符串。
- 将文本拆分为单词并将它们保存到字符串数组中。
- 执行字数统计。

以下 C# 源代码计算文档中的单词数。

```
// 使用 C# 计算 PDF 文档中的字数
using (Parser parser = new Parser("path/document.pdf"))
{                
	// Extract a text into the reader
	using (TextReader reader = parser.GetText())
	{
		string text = reader.ReadToEnd();
		char[] chars = { ' ', '.', ',', ';', ':', '?', '\n', '\r' };
		// split words
		string[] words = text.Split(chars);
		// print total word count
		Console.WriteLine("Total word count: {0}", stats.Count);
	}
}
```

## 在 C# 中计算单词的出现次数 {#count-words-occurrences}

类似地，我们可以计算一个特定单词或短语在文档中使用了多少次。通过使用此功能，您可以避免文章中任何单词的过度重复。以下步骤计算文档中使用的每个单词的出现次数。

- 使用 [Parser][7] 类加载文档。
- 将加载文档的文本检索到 [TextReader][8]。
- 阅读全文并将其拆分为单词集合。
- 遍历单词集合来计算单词。

以下 C# 代码片段计算文档中每个唯一单词的出现次数。

```
// 使用 C# 计算 PDF 文档中唯一单词及其出现次数
using (Parser parser = new Parser("path/document.pdf"))
{                
	// Extract text into TextReader
	using (TextReader reader = parser.GetText())
	{
		Dictionary<string, int> stats = new Dictionary<string, int>();
		string text = reader.ReadToEnd();
		char[] chars = { ' ', '.', ',', ';', ':', '?', '\n', '\r' };
		// split words
		string[] words = text.Split(chars);
		int minWordLength = 2; // Consider a word having more than 2 characters

		// iterate over the words collection to count occurrences
		foreach (string word in words)
		{
			string w = word.Trim().ToLower();
			if (w.Length > minWordLength)
			{
				if (!stats.ContainsKey(w))
				{
					stats.Add(w, 1); // add new word to collection
				}
				else
				{
					stats[w] += 1; // update word occurrence count
				}
			}
		}
		// order the collection by word count
		var orderedStats = stats.OrderByDescending(x => x.Value);
		
    		// Print word count Results
		Console.WriteLine("Total word count: {0}", stats.Count);

    		foreach (var pair in orderedStats)
		{
			Console.WriteLine("Total occurrences of {0}: {1}", pair.Key, pair.Value);
		}
	}
}
```

以下是上述代码的输出：

{{< figure align=center src="images/Word-Count.png" alt="单词出现计数">}}

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][10] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，您学习了如何使用 C# 计算文档中的单词。此外，我们还讨论了如何获取文档中每个单词的单词出现次数。尝试开发您的在线字数计数器 .NET 应用程序。有关 API 的更多详细信息和了解，请访问 [文档][11]。如有疑问，请通过 [论坛][12] 联系我们。

## 也可以看看

- [在 C# 中提取 ZIP 文件数据][13]
- [使用 C# 解析文档以提取图像][14]
- [用 C# 从 EPUB、FB2、CHM 电子书中提取图像][15]
- [使用 C# 读取 PDF 表单域][16]

[1]: [https://en.wikipedia.org/wiki/Don%27t_repeat_yourself]
[2]: https://products.groupdocs.com/parser/
[3]: https://products.groupdocs.com/parser/net/
[4]: https://docs.groupdocs.com/parser/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/parser
[6]: https://www.nuget.org/packages/groupdocs.parser
[7]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[8]: https://docs.microsoft.com/en-us/dotnet/api/system.io.textreader
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/gettext
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/parser/
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/08/25/extract-zip-files-data-in-csharp/
[14]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[15]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[16]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/
