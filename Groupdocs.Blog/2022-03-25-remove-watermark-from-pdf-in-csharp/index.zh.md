---
title: "'在 C# 中从 PDF 文档中删除水印'"
date: Fri, 25 Mar 2022 19:29:00 +0000
draft: false
url: /zh/2022/03/25/remove-watermark-from-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "水印通常用于避免任何非法使用机密文件。当不再需要保密时，您最好从此类文档中删除水印。文档中可以有基于文本和图像的水印。今天，我们将看看**如何使用 C# 去除 PDF 文档中的水印**。"
tags: ['delete watermark', 'how to remove watermark in c sharp', 'remove watermark', 'remove watermark from pdf', 'remove watermark using csharp', 'Watermark Remover', 'watermark remover application']
categories: ['GroupDocs.Watermark Product Family']
---

水印通常用于避免任何非法使用机密文件。当不再需要保密时，您最好从此类文档中删除水印。文档中可以有基于文本和图像的水印。今天，我们将看看**如何使用 C# 去除 PDF 文档中的水印**。



{{< figure align=center src="images/removing-watermark-from-pdf.jpg" alt="从 PDF 文档中删除水印">}}


## .NET API 删除 PDF 水印

[GroupDocs.Watermark](https://products.groupdocs.com/watermark) 展示了 .NET API 来处理不同[文件格式](https://docs.groupdocs.com/conversion/net) 文档和图像中的水印/支持的文档格式/) 。如果您正在制作_水印去除应用程序_，它为您提供了一些有用的方法：

* 删除 PDF 中的所有水印
*删除具有特定文本格式的水印
* 去除超链接水印

让我们了解 C# 开发人员如何使用 [GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net/) API 以不同方式从 PDF 中删除水印。

## 使用 C# 从 PDF 文档中删除所有水印 {#RemovingFoundWatermarks-RemoveWatermark}

API 使您能够轻松找到并删除文档中的特定水印和所有水印。以下代码使用 C# 从 PDF 文档中删除所有水印。

* 使用 [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker) 加载 PDF 文件。
* 使用搜索将所有 [可能的水印](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) 作为集合获取。
* 遍历整个集合并删除每个水印或符合您标准的水印。
* 保存更新后的 PDF，不要再添加水印。

以下 C# 代码从 PDF 文档中删除所有水印。

```
// 使用 C# 从 PDF 和其他文档中删除水印
using (Watermarker watermarker = new Watermarker("filepath/documentWithWatermarks.pdf"))
{
    PossibleWatermarkCollection possibleWatermarks = watermarker.Search();

    // Remove every watermark by mentioning the index within document.
    for (int i = 0; i < possibleWatermarks.Count; i++)
    {
        possibleWatermarks.RemoveAt(0);
    }
    watermarker.Save("filepath/no-watermarks.pdf");
}
```

## 使用 C# 从具有特定文本格式的 PDF 中删除水印 {#RemovingFoundWatermarks-RemoveWatermarkwithParticularTextFormatting}

使用 API，您可以根据文本格式搜索和删除水印。您可以提供包含名称、字体、大小、颜色等的搜索条件，API 将找到具有匹配属性的水印。以下代码片段演示了如何使用 C# 从具有特定文本格式的 PDF 文件中搜索和删除水印。

* 使用 [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker) 加载 PDF 文件。
* 使用 [TextFormattingSearchCriteria](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search.searchcriteria/textformattingsearchcriteria) 定义搜索条件。
* 提及所有必需的格式属性。
* 执行 **Search()** 并通过提供定义的条件获取所有 [可能的水印](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) 作为集合。
* 使用 **Clear()** 方法删除所有搜索到的水印。
* 使用定义的属性保存更新后的没有水印的 PDF。

以下 C# 代码删除具有指定文本格式的 PDF 文档中的水印。

```
// 使用 C# 从 PDF 中删除具有特定文本格式的水印
using (Watermarker watermarker = new Watermarker("path/Watermarks.pdf"))
{
    TextFormattingSearchCriteria criteria = new TextFormattingSearchCriteria();
    criteria.ForegroundColorRange = new ColorRange();
    criteria.ForegroundColorRange.MinHue = -5;
    criteria.ForegroundColorRange.MaxHue = 10;
    criteria.ForegroundColorRange.MinBrightness = 0.01f;
    criteria.ForegroundColorRange.MaxBrightness = 0.99f;
    criteria.BackgroundColorRange = new ColorRange();
    criteria.BackgroundColorRange.IsEmpty = true;
    criteria.FontName = "Arial";
    criteria.MinFontSize = 19;
    criteria.MaxFontSize = 42;
    criteria.FontBold = true;

    PossibleWatermarkCollection possibleWatermarks = watermarker.Search(criteria);
    possibleWatermarks.Clear();

    watermarker.Save("path/removed-watermarks.pdf");
}
```

## .NET 中的超链接水印去除器

文档水印 .NET API 允许您在任何支持的文档格式的文档中搜索和删除超链接。以下步骤允许使用 C# 从 .NET 应用程序中的 PDF 文档中删除超链接水印。

* 使用 [Watermarker](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker) 加载 PDF 文件。
* 使用搜索将所有 [可能的水印](https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.search/possiblewatermarkcollection) 作为集合获取。
*遍历整个集合并删除每个水印或符合您标准的水印。
* 保存更新后的 PDF，不要再添加水印。

以下 C# 代码示例展示了如何从 PDF 文档中查找和删除具有特定 URL 的超链接水印。

```
// 使用 C# 从 PDF 中删除超链接水印
using (Watermarker watermarker = new Watermarker("path/Hyperlink-Watermarks.pdf"))
{
    PossibleWatermarkCollection watermarks = watermarker.Search(new TextSearchCriteria(new Regex(@"someurl\.com")));
    for (int i = 0 ; i < watermarks.Count; i++)
    {
        if (watermarks[i] is HyperlinkPossibleWatermark)
        {
            Console.WriteLine("Removing: " + watermarks[i].Text);
            watermarks.RemoveAt(i);
        }
    }
    watermarker.Save("path/no-hyperlink-watermarks.pdf");
}
```

## 结论

总而言之，今天我们学习了使用 C# 从 PDF 文档中删除不同的水印。我相信您现在将更有信心构建自己的 .NET 应用程序来查找和删除 PDF 文档中的文本水印和图像水印。此外，您可以添加删除具有指定格式的水印和超链接水印的功能。

此外，您可以从其 [文档](https://docs.groupdocs.com/watermark/) 中了解有关 [GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net/) 的更多信息.如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [使用 C# 的水印密码保护文档](https://blog.groupdocs.com/2021/12/25/watermark-password-protected-documents-using-csharp/)
* [使用 C# 为 PDF 文件添加水印](https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/)
* [使用 C# 为图像添加水印](https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/)
* [在 Java 中查找和删除文档中的水印](https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/)





