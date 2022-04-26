---
title: "在 C# 中合并 PDF、Word 文档、电子表格、演示文稿文件"
date: Wed, 19 Aug 2020 18:20:42 +0000
draft: false
url: /zh/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
author: 'Shoaib Khan'
summary: "今天，我们将学习使用 C# 以编程方式合并 PDF、Word 文档、电子表格、演示文稿。在之前的一篇文章中，我们已经看到了[使用 Java 合并和拆分文档][1]。"
tags: ['Merge Documents in CSharp', 'Merge Excel Sheets in CSharp', 'Merge PDF Files in CSharp', 'Merge PPT PPTX in CSharp', 'Merge Word Docs in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

今天，我们将学习使用 C# 以编程方式合并 PDF、Word 文档、电子表格、演示文稿。在之前的一篇文章中，我们已经看到了[使用 Java 合并和拆分文档][2]。



{{< figure align=center src="images/merge-documents-with-csharp-dotnet.png" alt="使用 csharp dotnet 合并多个 pdf、word、excel、ppt 文件">}}


本文还将向您展示有关以下方面的代码示例：

* [合并PDF文件][3]
* [合并Word文档][4]
* [合并选择性页面][5]
* [合并电子表格和演示文稿][6]

我将在下面的所有示例中使用 [GroupDocs.Merger for .NET][7]。在继续之前，您可以从以下任一选项中获取 API：

* 从 [NuGet][8] Packages Gallery 安装包。
* [下载][9] GroupDocs 下载部分的 MSI 或 DLL。

## 在 C# 中合并 PDF 文件 {#merge-pdf-in-csharp}

以下简单的 3 行代码将 2 个 PDF 文件合并为 1 个 PDF 文档。

* 使用 [Merger][10] 类从第一个文档开始。
* 调用Merger类的[Join][11]方法，传入第二个文档进行合并。
* 调用[Save][12]方法保存合并的文档。

```
// Merge 2 PDF files in C#
using (Merger merger = new Merger(@"document1.pdf"))
{
    merger.Join(@"document2.pdf");
    merger.Save(@"merged.pdf");
}
```

[Join][13] 方法有几个重载方法，允许通过文件路径、使用流或远程 URL 合并文档或不同文档的选择性页面。

## 在 C# 中合并多个 Word 文档 {#merge-word-files-in-csharp}

上面类似的代码允许组合两个或多个 MS Word 和 OpenDocument 格式的文件，而不会丢失格式。只是给出一个想法，您可以合并 .doc、.docx、.docm、.dot、.dotx、.dotm、.rtf、.odt、.ott 等。下面是合并两个 MS Word DOCX 文件的 3 行代码.

```
// Merge Word files in C#
using (Merger merger = new Merger(@"c:\\document1.docx"))
{
    merger.Join(@"c:\\document2.docx");
    merger.Save(@"c:\\merged.docx");
}
```

## 合并多个文件的页面 - C# {#merge-pages-in-csharp}

不仅是整个文档，我们还可以合并来自多个文档的选择性页面以获得组合的单个文档。

```
// Merge selective pages
string filePath = @"c:\\sample.docx";
string filePath2 = @"c:\\sample2.docx";
string filePathOut = @"c:\\output\\result.docx";

JoinOptions joinOptions = new JoinOptions(1, 4, RangeMode.OddPages);

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.Join(filePath2, joinOptions);
    merger.Save(filePathOut);
}
```

## 在 C# 中合并电子表格、演示文稿和其他文档 {#merge-documents-in-csharp}

除了 PDF 和 Word 等文档，我们还可以合并演示文稿、电子表格和许多其他格式。只需更改文件名并在上面的代码中相应地键入，您将获得合并的文档。

```
using (Merger merger = new Merger(@"filepath1.xxx"))
{
    merger.Join(@"filepath2.xxx");
    merger.Save(@"xyz.xxx");
}
```

## 首先检查文件格式支持

您的要求可能有点不同的文件类型，因此最好先了解 API 是否支持合并所需的文档。以下代码获取 Merger API 支持的所有文件类型。

```
foreach (FileType fileType in FileType
        .GetSupportedFileTypes()
        .OrderBy(fileType => fileType.Extension))
{
    Console.WriteLine(fileType);
}
```

这是上面显示文件格式的代码的输出。

```
Bitmap Image File (.bmp)
Comma Separated Values File (.csv)
Excel Binary Spreadsheet (.xlsb)
Excel Macro-Enabled Add-In (.xlam)
Excel Open XML Macro-Enabled Spreadsheet (.xlsm)
Excel Open XML Macro-Enabled Spreadsheet Template (.xltm)
Excel Open XML Spreadsheet (.xlsx)
Excel Open XML Spreadsheet Template (.xltx)
Excel Spreadsheet (.xls)
Excel Template File (.xlt)
Hypertext Markup Language File (.html)
JPEG Image (.jpeg)
LaTeX Source Document (.tex)
MHTML Web Archive (.mht)
MIME HTML File (.mhtml)
OneNote Document (.one)
Open eBook File (.epub)
OpenDocument Document Template (.ott)
OpenDocument Presentation (.odp)
OpenDocument Presentation Template (.otp)
OpenDocument Spreadsheet (.ods)
OpenDocument Text Document (.odt)
Plain Text File (.txt)
Portable Document Format File (.pdf)
Portable Network Graphic (.png)
PostScript File (.ps)
PowerPoint Open XML Presentation (.pptx)
PowerPoint Open XML Slide Show (.ppsx)
PowerPoint Presentation (.ppt)
PowerPoint Slide Show (.pps)
Rich Text Format File (.rtf)
Tab Separated Values File (.tsv)
Visio Drawing (.vsdx)
Visio Drawing Template (.vstx)
Visio Drawing XML File (.vdx)
Visio Macro-Enabled Drawing (.vsdm)
Visio Macro-Enabled Drawing Template (.vstm)
Visio Macro-Enabled Stencil File (.vssm)
Visio Stencil File (.vssx)
Visio Stencil XML File (.vsx)
Visio Template XML File (.vtx)
Word Document (.doc)
Word Document Template (.dot)
Word Open XML Document (.docx)
Word Open XML Document Template (.dotx)
Word Open XML Macro-Enabled Document (.docm)
Word Open XML Macro-Enabled Document Template (.dotm)
XML Paper Specification File (.xps)
```

## 了解有关 .NET Merger API 的更多信息

如果您想了解有关 GroupDocs 的 .NET Merger API 的更多信息，请访问 [文档][14] 或在 [论坛][15] 上与我们联系以了解任何问题。

谢谢。







[1]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[2]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[3]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-pdf-in-csharp
[4]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-word-files-in-csharp
[5]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-pages-in-csharp
[6]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-documents-in-csharp
[7]: https://products.groupdocs.com/merger/net
[8]: https://www.nuget.org/packages/GroupDocs.Merger/
[9]: https://downloads.groupdocs.com/merger/net
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[14]: https://docs.groupdocs.com/merger/net/getting-started/
[15]: https://forum.groupdocs.com/c/merger


