---
title: "使用 C# .NET 在 Word、Excel、PDF、ZIP 和其他文档格式中搜索文本"
date: Fri, 29 May 2020 09:25:45 +0000
draft: false
url: /zh/2020/05/29/search-text-in-word-excel-pdf-zip-document-formats-using-csharp-net/
author: 'Muhammad Sohail'
summary: "我们经常需要一个全文搜索 API，它使我们的应用程序能够在文档中搜索指定为文本搜索查询的特定信息。文档可以是任何格式，例如 Word（Doc、Docx）、PDF、HTML、EPUB、电子表格（XLS、XLSX）、演示文稿（PPT、PPTX）、图像和视频。"
tags: ['Full Text Search Csharp', 'Search text in multiple Documents', 'Search text in PDF Document', 'Search text in Word Document']
categories: ['GroupDocs.Search Product Family']
---



{{< figure align=center src="images/Search-Documents.png" alt="文件全文检索">}}


我们经常需要一个全文搜索 API，它使我们的应用程序能够在文档中搜索指定为文本搜索查询的特定信息。文档可以是任何格式，例如 Word（Doc、Docx）、PDF、HTML、EPUB、电子表格（XLS、XLSX）、演示文稿（PPT、PPTX）、图像和视频。

[GroupDocs.Search][1] 是一个功能强大的全文搜索 API，允许您在应用程序中搜索 [超过 70 种文档格式][2]。为了能够立即搜索数千个文档，必须将它们添加到索引中。

## 为什么使用 GroupDocs.Search 作为开发人员？

* 搜索支持格式的文档不需要额外的软件。
* 提供多种索引和搜索选项以满足任何要求。
* 在文本或对象形式的查询中提供多种搜索类型。
* 高索引和搜索性能是通过独特的算法和数据结构、优化和多线程执行来实现的。
* 支持在文档文本中可视化搜索结果的各种方式。

请查看[关于搜索引擎][3] 文章了解 GroupDocs.Search API 在搜索引擎分类中的位置。

## 安装

GroupDocs.Search for .NET 托管在 [NuGet][4] 上，可以使用 NuGet 包管理器轻松安装。或者，您可以从 [下载][5] 部分下载 API 的 DLL。

## 使用 C# 搜索 Office 文档

以下步骤说明如何在多个文档（Word、Excel、PDF 和其他文档格式）中搜索单词或短语。

* **创建新索引**：首先，您需要创建一个索引。可以在内存或磁盘上创建索引。退出程序后无法保存在内存中创建的索引。相反，将来可能会加载在磁盘上创建的索引以继续工作。 [创建索引][6] 部分描述了有关创建索引的详细信息。
* **订阅索引事件：**创建索引后，需要将文档添加到索引中进行索引。索引文档可能因各种原因成功或不成功，例如，由于磁盘读取错误或存在访问文档的密码。要接收有关索引错误的信息，您可以订阅 ErrorOccurred 事件。要使用事件，请参阅 [搜索索引事件][7] 部分。
* **索引文档**：文档索引可以同步或异步执行。同步索引意味着启动索引过程的线程将一直忙到操作完成。然而，更多时候，需要异步执行索引，并能够在启动操作的线程中执行其他任务。 [索引][8] 部分提供了索引过程所有方面的详细描述。
* **执行搜索：** 当文档被索引时，索引已准备好处理搜索查询。支持以下类型的搜索查询：简单、模糊、区分大小写、布尔、短语、分面、带通配符等。 [搜索][9] 部分介绍了各种类型的搜索查询。
* **使用搜索结果：** 搜索完成后，您需要以某种方式解释结果。结果可以通过找到的文档的简单列表来表示，或者可以在文档的文本中突出显示找到的单词和短语。有关处理搜索结果的更多信息，请参阅 [搜索结果][10]。

```
string indexFolder = @"/Users/muhammadsohailismail/MyIndex/"; // Specify the path to the index folder
string documentsFolder = @"/Users/muhammadsohailismail/MyDocuments/"; // Specify the path to a folder containing documents to search

// a) Create new index or
// b) Open existing index
Index index = new Index(indexFolder);

// c) Subscribe to index events
index.Events.ErrorOccurred += (sender, args) =>
{
    Console.WriteLine(args.Message); // Writing error messages to the console
};

// d) Add files synchronously
index.Add(documentsFolder); // Synchronous indexing documents from the specified folder

// f) Perform search
string query = "Worthy"; // Specify a search query
SearchResult result = index.Search(query); // Searching in the index

// g) Use search results
// Printing the result
Console.WriteLine("Documents found: " + result.DocumentCount);
Console.WriteLine("Total occurrences found: " + result.OccurrenceCount);
for (int i = 0; i < result.DocumentCount; i++)
{
    FoundDocument document = result.GetFoundDocument(i);
    Console.WriteLine("\\tDocument: " + document.DocumentInfo.FilePath);
    Console.WriteLine("\\tOccurrences: " + document.OccurrenceCount);
}

// Highlight occurrences in text
if (result.DocumentCount > 0)
{
    FoundDocument document = result.GetFoundDocument(0); // Getting the first found document
    string path = @"/Users/muhammadsohailismail/Output/Highlighted.html";
    OutputAdapter outputAdapter = new FileOutputAdapter(path); // Creating the output adapter to a file
    HtmlHighlighter highlighter = new HtmlHighlighter(outputAdapter); // Creating the highlighter object
    index.Highlight(document, highlighter); // Generating output HTML formatted document with highlighted search results

    Console.WriteLine();
    Console.WriteLine("Generated HTML file can be opened with Internet browser.");
    Console.WriteLine("The file can be found by the following path:");
    Console.WriteLine(Path.GetFullPath(path));
}
```

上面的代码生成以下输出和 [HTML 文件][11]。



{{< figure align=center src="images/Output.jpg" alt="">}}


## 使用 C# 在文档字段中搜索

分面搜索是通过将有效的文档字段名称设置为搜索来过滤搜索结果。分面搜索允许您仅在文档的某些字段中进行搜索，例如，仅在内容字段或文件名字段中进行搜索。下面介绍了一个简单的多面搜索示例，其中包含文本和对象形式的查询。

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.Add(documentsFolder);
 
// Search in the content field with text query
SearchResult result1 = index.Search("content: Einstein");
 
// Search in the content field with object query
SearchQuery wordQuery = SearchQuery.CreateWordQuery("Einstein");
SearchQuery fieldQuery = SearchQuery.CreateFieldQuery(CommonFieldNames.Content, wordQuery);
SearchResult result2 = index.Search(fieldQuery);
```

### 使用格式特定字段

对于每种文档格式，此类文档中可能存在标准字段。该库提供了以下类，其中包含具有标准文档字段名称的常量：[EpubFieldNames][12]、[FictionBookFieldNames][13]、[MailFieldNames][14]、[PresentationFieldNames][15]、[SpreadsheetFieldNames][16] , [WordsFieldNames][17]。

还有一些字段可能出现在任何类型的文档中。这些字段的名称在 [CommonFieldNames][18] 类中表示。

下面的例子展示了一个使用文档的标准字段名称的例子。

```
string indexFolder = @"c:\\MyIndex\\";
string documentsFolder = @"c:\\MyDocuments\\";
 
// Creating an index in the specified folder
Index index = new Index(indexFolder);
 
// Indexing documents from the specified folder
index.Add(documentsFolder);
 
// Search in the content field with text query
string query1 = WordsFieldNames.Company + ": Dycum";
SearchResult result1 = index.Search(query1);
 
// Search in the content field with object query
SearchQuery wordQuery = SearchQuery.CreateWordQuery("Dycum");
SearchQuery fieldQuery = SearchQuery.CreateFieldQuery(WordsFieldNames.Company, wordQuery);
SearchResult result2 = index.Search(fieldQuery);
```

有关分面搜索的详细信息，请参见页面 [分面搜索][19]。

## 结论

本文介绍了如何在文档（DOCX、PDF、Excel、文本文件）中搜索 C# 中的特定信息。它还解释了如何在文档字段中进行搜索。 GroupDocs.Search 包含其他几个功能，请查看 [文档][20] 以了解更多信息。







[1]: https://products.groupdocs.com/search
[2]: https://docs.groupdocs.com/display/searchnet/Supported+Document+Formats
[3]: https://docs.groupdocs.com/display/searchnet/About+Search+Engines
[4]: https://www.nuget.org/packages/GroupDocs.Search/
[5]: https://downloads.groupdocs.com/search/net
[6]: https://docs.groupdocs.com/display/searchnet/Creating+an+index
[7]: https://docs.groupdocs.com/display/searchnet/Search+index+events
[8]: https://docs.groupdocs.com/display/searchnet/Indexing
[9]: https://docs.groupdocs.com/display/searchnet/Searching
[10]: https://docs.groupdocs.com/display/searchnet/Search+results
[11]: https://www.dropbox.com/s/ioztnalgq2fjqcs/Highlighted.html?dl=0
[12]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/epubfieldnames
[13]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/fictionbookfieldnames
[14]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/mailfieldnames
[15]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/presentationfieldnames
[16]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/spreadsheetfieldnames
[17]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/wordsfieldnames
[18]: https://apireference.groupdocs.com/net/search/groupdocs.search.options/commonfieldnames
[19]: https://docs.groupdocs.com/display/searchnet/Faceted+search
[20]: https://docs.groupdocs.com/display/searchnet/Developer+Guide


