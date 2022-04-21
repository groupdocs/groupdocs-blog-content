---
title: "用于比较文本文件的 C# Diff 库"
date: Thu, 30 Apr 2020 14:41:00 +0000
draft: false
url: /zh/2020/04/30/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
aliases:
- /2014/07/04/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
author: 'Muhammad Sohail'
summary: "[GroupDocs.Comparison for .NET][1] 是一个 C# 库，可让您比较文档并找出差异。比较和合并 Microsoft Word、Excel、PowerPoint、OpenDocument、PDF、文本、HTML 和 [许多其他文档][2]，检索源文档和目标文档之间的更改列表，应用或拒绝更改并使用 GroupDocs 保存结果.比较 API。除此之外，GroupDocs.Comparison 可以识别样式和格式更改 - 如粗体、斜体、下划线、删除线、字体类型等。"
tags: ['compare text files', 'diff view library', 'GroupDocs Comparison']
categories: ['GroupDocs.Comparison Product Family']
---



{{< figure align=center src="images/groupdocs-comparison-128x128-1.png" alt="">}}


[GroupDocs.Comparison for .NET][3] 是一个 C# 库，可让您比较文档并找出差异。比较和合并 Microsoft Word、Excel、PowerPoint、OpenDocument、PDF、文本、HTML 和 [许多其他文档][4]，检索源文档和目标文档之间的更改列表，应用或拒绝更改并使用 GroupDocs 保存结果.比较 API。除此之外，GroupDocs.Comparison 可以识别样式和格式更改 - 如粗体、斜体、下划线、删除线、字体类型等。

[GroupDocs.Comparison][5] 使用的变化检测算法允许检测不同文档部分和块中的差异：

* 文本块 - 段落、单词和字符；
* 表格；
* 图片;
* 形状等

以下是比较两个文本文件并显示差异的简单步骤：

* 使用源文档路径或流实例化 [Comparer][6] 对象；
* 调用[Add][7]方法并指定目标文档路径或流；
* 调用[比较][8]方法。

以下代码片段演示了使用几行代码进行文档比较的最简单情况。

### 比较本地文件中的文档

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare(“result.docx”);
}
```

### 比较流中的文档
```
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”)))
{
    comparer.Add(File.OpenRead(“target.docx”));
    comparer.Compare(File.Create(“result.docx”));
}
```

假设您有两份 DOCX 格式的合同，它们是在不同年份签订的。如果你使用上面的代码比较这些合约，你会得到一个 DOCX 文件，其中删除的元素标记为红色，添加的元素标记为蓝色，修改的元素标记为绿色，如下所示：



{{< figure align=center src="images/FreelanceContract.png" alt="">}}


## 接受或拒绝检测到的差异

[GroupDocs.Comparison][9] 提供了在源文档和目标文档之间应用或丢弃特定更改并保存带有（或不带有）选定更改的结果文档的能力。

以下是对结果文档应用/拒绝更改的步骤。

* 使用源文档路径或流实例化 [Comparer][10] 对象；
* 调用_[A][11]_[dd][12]方法并指定path目标文档路径或流；
* 调用[比较][13]方法；
* 调用[GetChanges][14]方法，获取检测到的变化列表；
* 将所需变更对象的[ComparisonAction][15]设置为[ComparisonAction.Accept][16]或[ComparisonAction.Reject][17]值；
* 调用 [ApplyChanges][18] 方法并将更改集合传递给它。

以下代码示例显示了如何接受/拒绝检测到的差异。

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges(File.Create(“result.docx”), new SaveOptions(), new ApplyChangeOptions() { Changes = changes });
}
```

## 生成文档页面预览

[GroupDocs.Comparison][19] 允许使用 [Document][21] 类的 [GeneratePreview][20] 方法为源、目标和结果文档生成页面预览。

[PreviewOptions][22] 类用于管理预览生成过程 - 指定所需的页码、图像格式等。

以下是使用 GroupDocs.Comparison API 生成文档预览的步骤：

* 创建[Comparer][23]类的新实例，并将源文档路径作为构造函数参数传递；
* 使用 [Add][24] 方法将目标文档添加到比较中；
* [Comparer][27] 对象的 [Source][25] 和 [Targets][26] 属性允许访问源文档和目标文档并提供 [GeneratePreview][28] 方法；
* 实例化 [PreviewOptions][29] 对象：
    * 为每个页面流创建委托（请参阅事件处理程序 CreatePageStream）；
    * 图片预览格式——PNG/JPG/BMP；
    * 要处理的页码；
    * 预览图像的自定义大小（如果需要）。
* 调用 [Source][31] 和 [Targets][32] 文档的 [GeneratePreview][30] 方法并将 [PreviewOptions][33] 传递给它。

### 获取结果文档的页面预览

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare(“result.docx”);
    Document document = new Document(File.OpenRead(“result.docx”));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(“C:\\”, $"result\_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    document.GeneratePreview(previewOptions);
}
```

## 比较多个文档

[GroupDocs.Comparison][34] 允许比较两个以上的文档。以下代码示例显示了如何以编程方式比较多个文档。

```
using (Comparer comparer = new Comparer(“source.docx”)
{
    comparer.Add(“target1.docx”);
    comparer.Add(“target2.docx”);
    comparer.Add(“target3.docx”);
    comparer.Compare(“result.docx”);
}
```

## 安装

[NuGet][35] 是下载和安装 GroupDocs.Comparison for .NET 的最简单方法。请[获得临时许可证][36] 以不受任何功能限制地测试库。

请查看 [文档][37] 以了解有关该库的更多信息。我们还提供免费技术支持，因此请随时[联系我们][38] - 我们很乐意提供帮助。


[1]: https://products.groupdocs.com/comparison/net
[2]: https://docs.groupdocs.com/comparison/net
[3]: https://products.groupdocs.com/comparison/net
[4]: https://docs.groupdocs.com/comparison/net
[5]: https://apireference.groupdocs.com/comparison/net
[6]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[7]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[8]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[9]: https://products.groupdocs.com/comparison/net
[10]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[11]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[12]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/getchanges/index
[15]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/changeinfo/properties/comparisonaction
[16]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/comparisonaction
[17]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/comparisonaction
[18]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/applychanges/index
[19]: https://products.groupdocs.com/comparison/net
[20]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[21]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document
[22]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[23]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[24]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[25]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/source
[26]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/targets
[27]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[28]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[29]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[30]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[31]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/source
[32]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/targets
[33]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[34]: https://products.groupdocs.com/comparison/net
[35]: https://www.nuget.org/packages/GroupDocs.Comparison/
[36]: https://purchase.groupdocs.com/temporary-license
[37]: https://docs.groupdocs.com/display/comparisonnet/Home
[38]: https://forum.groupdocs.com/


