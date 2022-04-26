---
title: "在 C# 中从文档中查找和删除水印"
date: Fri, 27 Nov 2020 14:21:34 +0000
draft: false
url: /zh/2020/11/27/从文档中的 csharp 中查找并删除水印/
author: 'Shoaib Khan'
summary: "今天，我们将看看**如何在 C# 中查找和删除文档中的水印**。文档中可以有基于文本和图像的水印。我们可以轻松地从许多 PDF、Word、Excel、PowerPoint 和 Visio 支持的文档中搜索和以编程方式删除此类水印。"
tags: ['find and remove watermarks in csharp', 'find watermarks in csharp', 'remove watermarks in csharp', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark Product Family']
---

今天，我们将看看**如何在 C# 中查找和删除文档中的水印**。文档中可以有基于文本和图像的水印。我们可以轻松地从许多 PDF、Word、Excel、PowerPoint 和 Visio 支持的文档中搜索和以编程方式删除此类水印。

本文将涵盖以下主题：

* [用于去除水印的.NET API][1]
* [使用C#在文档中查找水印][2]
* [去除C#文档中的水印][3]



{{< figure align=center src="images/find-and-remove-watermarks-using-groupdocs.watermark-1.png" alt="使用 GroupDocs API 从文档中查找和删除水印">}}


## 用于去除水印的 .NET API {#watermark-removing-api-for-dotnet}



{{< figure align=center src="images/groupdocs-watermark-net.png" alt=".NET 的水印 API - GroupDocs">}}


[GroupDocs.Watermark for .NET][4] 是一种快速高效的水印 API，不需要额外的软件。它允许以第三方工具难以删除的方式向文档和图像添加水印。它还让 C# 开发人员可以轻松地从**文字处理文档**、**电子表格**、**演示文稿**、**Visio 绘图*的许多 **Microsoft** 和 **OpenOffice** 文件格式中删除水印* 和 .NET 应用程序中的 **PDF** 文档。 [文档][6] 中提到了所有[支持的文件格式][5]。

现在，我将展示查找和删除水印的示例。因此，如果您按照任何合适的选项预先准备好环境会更好：

* [NuGet][7]
*   [Direct Download][8]: MSI installer and DLLs
* **包管理器控制台：**

```
PM> Install-Package GroupDocs.Watermark
```

## 使用 C# 在文档中查找水印 {#find-watermarks-in-documents-using-csharp}

[Watermarker][9]、[PossibleWatermarkCollection][10]（[PossibleWatermark][11]的集合是API的类，用于在具有各种搜索条件的文档中查找各种水印并快速删除它们。以下是步骤用于使用 C# 对任何提供的文档中的所有水印进行基本搜索。您可以进一步优化对水印的搜索，这将在本文后面显示。

* 使用源文档文件创建 **Watermarker** 类对象。
* 调用**搜索**方法。它将返回文档中所有可能的水印。
* 遍历水印集合以显示数据或对每个水印执行任何操作。

```
// 使用 C# 查找 Word、Excel、PowerPoint、Visio 和 PDF 文档中的所有水印
using (Watermarker watermarker = new Watermarker("filepath/documentWithWatermarks.pdf"))
{
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search();
    foreach (PossibleWatermark possibleWatermark in possibleWatermarks)
    {
        if (possibleWatermark.ImageData != null)
        {
            Console.WriteLine(possibleWatermark.ImageData.Length);
        }
        Console.WriteLine(possibleWatermark.Text);
        Console.WriteLine(possibleWatermark.X);
        Console.WriteLine(possibleWatermark.Y);
        Console.WriteLine(possibleWatermark.RotateAngle);
        Console.WriteLine(possibleWatermark.Width);
        Console.WriteLine(possibleWatermark.Height);
    }
}
```

## 在 C# 中从文档中删除水印 {#remove-watermarks-from-documents-in-csharp}

从所有搜索到的水印中，我们可以一次删除任何水印或所有水印。这里的主要内容是，您是否已成功找到要删除的水印。如果文档中有很多不同类型的水印怎么办？ API 提供了各种选项来优化您的水印搜索。以下代码通过使用 C# 指定集合的索引来从 PDF 文档中删除水印。

```
// 使用 C# 从 PDF 和其他文档中删除水印
using (Watermarker watermarker = new Watermarker("filepath/documentWithWatermarks.pdf"))
{
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search();

    // Remove watermark at the specified index from the document.
    possibleWatermarks.RemoveAt(0);

    // Remove specified watermark from the document.
    possibleWatermarks.Remove(possibleWatermarks[0]);

    watermarker.Save("filepath/noWatermarks.pdf");
}
```

## 更多水印搜索标准

还有许多其他方法可以找到具有特定标准的水印。在选择性搜索之后，我们可以相应地使用 **Remove**、**RemoveAt** 或 **Clear** 方法从集合中删除水印。以下是从提供的文档中查找水印的一些方法：

* 查找并删除带有特定文本的水印
* 使用 RegEx（正则表达式）搜索水印并删除
* 搜索指定文本格式的水印
* 查找和删除超链接水印

### 查找和删除带有特定文本的水印

您可以通过使用以下 C# 代码指定确切的字符串来搜索文本水印：

```
 // Find possible watermarks containing the specified text
TextSearchCriteria textSearchCriterion = new TextSearchCriteria("© 2020");
PossibleWatermarkCollection possibleWatermarks = watermarker.Search(textSearchCriterion);
```

### 使用正则表达式搜索水印并删除

如果水印的文本中有某种模式，您可以提供正则表达式 (RegEx) 来搜索这些水印，并可以在以后使用以下 C# 代码相应地删除。此代码将获取所有带有 ©YYYY 的水印。

```
// Search Watermarks by Regular Expression
Regex regex = new Regex(@"^© \\d{4}$");
TextSearchCriteria textSearchCriterion = new TextSearchCriteria(regex);
PossibleWatermarkCollection possibleWatermarks = watermarker.Search(textSearchCriterion);
```

### 查找和删除具有特定文本格式的水印

您还可以找到具有某些特定文本格式的水印，例如字体名称、最小/最大字体大小、粗体/斜体/下划线等。

```
TextFormattingSearchCriteria criterion = new TextFormattingSearchCriteria()
{
    FontName = "Arial",
    MinFontSize = 19,
    MaxFontSize = 42,
    FontBold = true
};
PossibleWatermarkCollection watermarks = watermarker.Search(criterion);
watermarks.Clear();
```

### 查找和删除超链接水印

您可以使用 RegEx 在内容中查找具有超链接的文本水印。稍后您可以在搜索结果中检查是否有超链接水印。这些可以通过任何去除方法去除。以下 C# 代码删除所有带有超链接的水印。

```
PossibleWatermarkCollection watermarks = watermarker.Search(new TextSearchCriteria(new Regex(@"anyurl\\.com")));
for (int i = watermarks.Count - 1; i >= 0; i--)
{
    // Is watermark the hyperlink?
    if (watermarks\[i\] is HyperlinkPossibleWatermark)
    {
        watermarks.RemoveAt(i);
    }
}
```

还有许多其他方法可以优化您的[搜索水印][12]。您可以访问 [文档][13] 了解更多详细信息。如需查询，请访问 [论坛][14]。

## 结论

我相信您现在将更有信心在 .NET 应用程序中使用 C# 从 Word 文档、Excel 电子表格、Powerpoint 演示文稿、PDF 文档和 Visio 绘图中查找和删除文本水印和图像水印。

## 也可以看看

* [使用C#为图像或文档中的图像添加水印][15]
* [在Java中为图像添加水印][16]
* [在Java文档中查找和删除水印][17]







[1]: #watermark-removing-api-for-dotnet
[2]: #find-watermarks-in-documents-using-csharp
[3]: #remove-watermarks-from-documents-in-csharp
[4]: https://products.groupdocs.com/watermark/net
[5]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[6]: https://docs.groupdocs.com/watermark/net/
[7]: https://www.nuget.org/packages/groupdocs.watermark
[8]: https://downloads.groupdocs.com/watermark/net
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermark)
[12]: https://docs.groupdocs.com/watermark/net/searching-watermarks/
[13]: https://docs.groupdocs.com/watermark/net/
[14]: https://forum.groupdocs.com/c/watermark
[15]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
[16]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[17]: https://blog.groupdocs.com/2019/10/10/find-and-remove-watermarks-from-documents-in-java/


