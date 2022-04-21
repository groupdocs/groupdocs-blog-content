---
title: "在 C# 中比较两个或更多文件"
date: Tue, 10 Mar 2020 22:25:55 +0000
draft: false
url: /zh/2020/03/10/compare-excel-word-pdf-files-in-csharp/
aliases:
- /2020/03/10/compare-two-files-or-more-in-csharp-word-document-excel-spreadsheet/
- /2015/01/14/groupdocs-comparsion-for-dot-net-sample-compare-two-documents-in-csharp-and-display-diffs-on-aps-net-sites/
author: 'Shoaib Khan'
summary: "文档比较是当今编程世界最常见的要求之一。 无论是比较word文件、比较excel文件、PDF文档，甚至是比较文本文件或任何其他文件格式，准确性都是比较的关键因素。"
tags: ['compare documents', 'compare excel files', 'compare PDF files', 'compare text files', 'compare two documents', 'compare two excel files', 'compare two files', 'compare two word documents', 'compare word documents', 'document comparison', 'file compare']
categories: ['GroupDocs.Comparison Product Family']
---

文档比较是当今编程世界最常见的要求之一。无论是比较word文件、比较excel文件、PDF文档，甚至是比较文本文件或任何其他文件格式，准确性都是比较的关键因素。



{{< figure align=center src="images/groupdocs-comparison-net-90x90-no-border.png" alt="使用面向 .NET 开发人员的文档比较 API 比较文件">}}


本文将向您介绍 **[GroupDocs.Comparison][1]** 如何帮助程序员以多种方式比较任何两个或多个文档。 [On-Premise][2] GroupDocs.Comparison 的 API 目前可用于 [.NET][3] 和 [Java][4]，但是，本文倾向于 C# 开发人员。

## 比较 Excel、Word 文件或 C# 中的任何文档

[GroupDocs.Comparison][5] 允许开发人员比较两个文档（[实际上超过 2 个][6]。生成的文档显示了比较两个文件之间的变化。下面提到的代码显示了如何比较两个 excel 文件只需 3 行 C# 代码。

1. 使用源文档路径实例化 [Comparer][7] 对象。
2. 调用[Add][8]方法指定目标文档路径。
3. 调用[比较][9]方法。
4. 就是这样。

```
using (Comparer comparer = new Comparer(“source.xlsx”))
{
    comparer.Add(“target.xlsx”);
    comparer.Compare(“result.xlsx”);
}
```

比较 excel 电子表格或 Microsoft Word 文档只是 GroupDocs.Comparison 的 .NET API 支持的比较子集之一。以下是支持的格式列表。您可以访问 [文档][10] 以保持更新。

<figure class="wp-block-table is-style-stripes"><table class=""><tbody><tr><td>**文件类型</td><td><strong>文件格式**</strong></td></tr><tr><td><a href="https://wiki.fileformat.com/word-processing/">字处理</a></td><td>DOC、DOCX、DOCM、DOT、DOTX、DOTM、RTF、TXT</td></tr><tr><td><a href="https://wiki.fileformat.com/spreadsheet/">电子表格</a></td><td>XLS、XLSX、XLSM、XLT、XLTM、XLSB、XLSM、CSV</td></tr><tr><td><a href="https://wiki.fileformat.com/presentation/">演示文稿</a></td><td>PPT、PPTX、PPS、PPSX、POT、POTX</td></tr><tr><td><a href="https://wiki.fileformat.com/word-processing/">打开文档</a></td><td>ODT、ODP、OTP、ODS、OTT</td></tr><tr><td><a href="https://wiki.fileformat.com/view/pdf/">便携的</a></td><td>PDF格式</td></tr><tr><td><a href="https://docs.fileformat.com/visio/">微软 Visio 绘图</a></td><td>VSD、VSDX、VSS、VST、VDX</td></tr><tr><td><a href="https://wiki.fileformat.com/note-taking/">做笔记</a></td><td>一</td></tr><tr><td><a href="https://wiki.fileformat.com/web/">网络</a></td><td>HTM、HTML、MHT、MHTML</td></tr><tr><td><a href="https://wiki.fileformat.com/ebook/">电子书</a></td><td>摩比</td></tr><tr><td><a href="https://wiki.fileformat.com/image/">图片</a></td><td>BMP、GIF、JPG、JPEG、PNG、DICOM、DJVU、DWG、DXF</td></tr><tr><td><a href="https://wiki.fileformat.com/email/">电子邮件</a></td><td>EML、EMLX、味精</td></tr></tbody></table></figure>

## 在 C# 中比较两个或多个电子表格或 OneNote 文档

在 .NET 20.2 的 GroupDocs.Comparison 发布后，API 现在支持：

* 两个以上 **Microsoft Excel** 和 **OpenOffice** **电子表格**（XLS、XLSX、ODS、CSV 等）的比较
* 比较多个 Microsoft OneNote 文档。

API 已经支持比较各种文档格式的多个文件。以下代码片段显示了在 C# 中可以多快地比较多个 excel 文件。

```
using (Comparer comparer = new Comparer(“source.xlsx”)
{
    comparer.Add(“target1.xlsx”);
    comparer.Add(“target2.xlsx”);
    comparer.Add(“target3.xlsx”);
    comparer.Compare(“result.xlsx”);
}
```

## 在 C# 中比较流中的文档

作为程序员，您不仅可以比较本地存储中可用的文档，事实上，我们还可以比较流中的文档。

1. 只需使用源文档流初始化 [Comparer][11] 对象。
2. 调用 [Add][12] 方法并指定目标流。
3. 调用[比较][13]方法

```
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”))
{
    comparer.Add(File.OpenRead(“target1.docx”));
    comparer.Add(File.OpenRead(“target2.docx”));
    comparer.Add(File.OpenRead(“target3.docx”));
    comparer.Compare(File.Create(“result.docx”));
}
```

## 在 C# 中比较受密码保护的 Word 文档/Excel 电子表格

密码保护在官方文档中很常见。使用文档比较 .NET API，它允许其用户/开发人员比较受密码保护的文档。

与用于比较不受密码保护的文档的代码相比，代码只需稍作改动。加载文档时，使用 [LoadOptions][14] 指定文档密码。以下是为您提供帮助的示例比较代码。

```
using (Comparer comparer = new Comparer("source.docx", new LoadOptions() { Password = "1234" }))
{
    comparer.Add("target1.docx", new LoadOptions() { Password = "5678" });
    comparer.Add("target2.docx", new LoadOptions() { Password = "5678" });
    comparer.Add("target3.docx", new LoadOptions() { Password = "5678" });
    comparer.Compare("result.docx");
}
```

## 具有特定设置的文档比较

比仅比较领先一步，使用类似于下面提到的代码，您可以将多个文档与您的自定义比较设置进行比较。

[CompareOptions][15] 让您有机会指定比较选项，例如检测到更改的字体样式等。

```
using (Comparer comparer = new Comparer(“source.docx”)
{
    comparer.Add(“target1.docx”);
    comparer.Add(“target2.docx”);
    comparer.Add(“target3.docx”);
    CompareOptions compareOptions = new CompareOptions()
    {
        InsertedItemStyle = new StyleSettings()
        {
            FontColor = System.Drawing.Color.Yellow
        }
    };
    comparer.Compare(“result.docx”, compareOptions);
}
```

## 比较 C# 中的编程语言文件

GroupDocs 不断增加对比较更多文件格式的支持。在发布 v 20.2 之后，您现在还可以使用 .NET API 比较 JSON 文件。以下是最近添加到 [支持的文档格式列表][16] 中的编程语言文件格式：

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td>动作脚本</td><td>目标 C/C++</td></tr><tr><td>汇编器</td><td>Perl</td></tr><tr><td>基于 C 的</td><td>PHP</td></tr><tr><td>夏普</td><td>Python</td></tr><tr><td>时髦的</td><td>红宝石</td></tr><tr><td>JavaScript</td><td>斯卡拉</td></tr><tr><td>爪哇</td><td>Shell/批处理脚本、日志、差异、配置、LESS</td></tr><tr><td> JSON</td><td> SQL</td></tr></tbody></table></figure>

## 让我们谈谈

您可以使用上面突出显示的功能构建自己的应用程序。如果您在 [论坛][17] 上与我们联系以讨论、解决问题或分享您的反馈，我们将非常高兴。







[1]: https://products.groupdocs.com/comparison
[2]: https://products.groupdocs.com/comparison/family
[3]: https://products.groupdocs.com/comparison/net
[4]: https://products.groupdocs.com/comparison/java
[5]: https://products.groupdocs.com/comparison/family
[6]: https://docs.groupdocs.com/display/comparisonnet/Compare+multiple+documents)
[7]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[8]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[9]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[10]: https://docs.groupdocs.com/comparison/net
[11]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[12]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/loadoptions
[15]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/compareoptions
[16]: https://docs.groupdocs.com/comparison/net
[17]: https://forum.groupdocs.com/c/comparison


