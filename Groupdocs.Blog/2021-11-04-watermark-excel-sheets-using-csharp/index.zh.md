---
title: "使用 C# 给 Excel 表格添加水印"
date: Thu, 04 Nov 2021 18:46:00 +0000
draft: false
url: /zh/2021/11/04/watermark-excel-sheets-using-csharp/
author: 'Shoaib Khan'
summary: "我们已经讨论了为不同的[文档][1]、[图像][2]和[演示文稿][3]添加水印的方法。今天，我们将讨论如何在 .NET 应用程序中使用 C# 以不同方式向 Excel 工作簿添加水印。"
tags: ['add watermark in csharp', 'how to add watermark in csharp', 'watermark dotnet api', 'watermark excel', 'watermark excel sheets in csharp']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermark-to-excel-using-csharp.jpg" alt="使用 C# 将水印添加到 Excel 工作表">}}


我们已经讨论了为不同的[文档][4]、[图像][5]和[演示文稿][6]添加水印的方法。今天，我们将讨论如何在 .NET 应用程序中使用 C# 以不同方式向 Excel 工作簿添加水印。

以下主题涵盖以下内容：

* [.NET 水印 API][7]
* [将**文本水印**添加到 Excel 表格][8]
* [将水印应用到**特定的 Excel 工作表**][9]
* [将水印添加到 Excel 工作表**作为背景**][10]

## .NET API 到水印 Excel 表 {#watermarking-dotnet-api}

[GroupDocs.Watermark][11] 为各种文件格式的文档和图像提供 .NET API。我们将使用 [GroupDocs.Watermark for .NET][12] 使用 C# 以不同方式在电子表格中应用水印。

您可以从 [下载部分][13] 下载 DLL 或 MSI 安装程序，或从 [NuGet][14] 获取它。

```
Install-Package GroupDocs.Watermark
```

## 使用 C# 给 Excel 表格添加水印 {#watermark-all-sheets}

API 允许您将文本作为具有不同自定义的水印插入电子表格。以下是使用 C# 和 .NET 应用程序向 Excel 工作簿添加水印的步骤。

* 准备电子表格的加载选项。
* 使用 [Watermarker][15] 加载电子表格。
* 使用 [TextWatermark][16] 定义水印文本和外观。
* 使用 [Add][17] 方法将文本水印添加到 Excel 工作表。
* 使用 [Save][18] 方法保存带有水印的结果电子表格。

以下 C# 代码示例将文本水印应用到具有旋转和不透明度的 Excel 工作簿的所有工作表。

```
/*
 * Add watermark to all the sheets of the Excel Workbook using C#
 */
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
using (Watermarker watermarker = new Watermarker(@"path/spreadsheet.xlsx", loadOptions))
{
    // Add text watermark to the worksheet
    TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 100))
    {
        RotateAngle = -45,
        Height = 200,
        Width = 500,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue
    };
    // Add watermark and save the watermarked spreadsheet.
    watermarker.Add(textWatermark);
    watermarker.Save(@"path/allpages-watermark-spreadsheet.xlsx");
}
```

## 使用 C# 的水印特定 Excel 工作表 {#watermark-any-sheet}

同样，您可以仅将水印应用于任何特定工作表，而不是将它们应用于工作簿的所有工作表。以下步骤指导如何使用 C# 将文本水印插入 Excel 工作簿的特定工作表。

*准备加载选项。
* 使用 [Watermarker][19] 类加载电子表格。
* 使用 [TextWatermark][20] 类定义水印外观和文本。
* 设置工作表索引，以便水印仅应用于提到的工作表。
* 使用带有水印选项的 [Add][21] 方法将文本水印添加到 Excel 工作表。
* 使用 [Save][22] 方法保存带有水印的输出电子表格。

以下代码片段仅将文本水印应用于 Excel 工作簿的提及工作表。

```
/*
 * Add watermark only to the mentioned sheet of the Excel Workbook using C#
 */
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
using (Watermarker watermarker = new Watermarker(@"path/spreadsheet.xlsx", loadOptions))
{
    // Add text watermark to the worksheet
    TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 100))
    {
        RotateAngle = -45,
        Height = 200,
        Width = 500,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue
    };
    // Define the worksheet index
    SpreadsheetWatermarkShapeOptions textWatermarkOptions = new SpreadsheetWatermarkShapeOptions()
    {
        WorksheetIndex = 1
    };
    // Add watermark and save the watermarked spreadsheet.    
    watermarker.Add(textWatermark, textWatermarkOptions);
    watermarker.Save(@"path/onepage-watermark-spreadsheet.xlsx");
}
```

## 使用 C# 水印 Excel 工作表作为背景 {#watermark-sheet-as-background}

同样，我们也可以添加水印作为电子表格的背景。上述应用水印的技术会有一点变化。以下是允许使用 C# 将背景文本水印插入 Excel 电子表格的步骤。

*准备加载电子表格的加载选项。
* 使用 [Watermarker][23] 加载电子表格。
* 使用 [TextWatermark][24] 定义水印文本和外观（旋转、位置、尺寸、不透明度、颜色等）。
* 通过获取内容和设置尺寸来设置背景水印选项。
* 设置工作表的索引以应用水印。 （选修的）
* 使用 [Add][25] 方法将水印添加到电子表格中。
* 使用[Save][26]方法保存带水印的电子表格。

以下代码示例显示了如何在 .NET 应用程序中使用 C# 将背景水印添加到 Excel 电子表格。

```
/*
 * Add watermark as background to Excel Workbook using C#
 */
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
using (Watermarker watermarker = new Watermarker(@"path/spreadsheet.xlsx", loadOptions))
{
    // Define Watermark Appearance
    TextWatermark textWatermark = new TextWatermark("DRAFT", new Font("Arial", 100))
    {
        RotateAngle = -45,
        X = 200,
        Y = 200,
        Height = 200,
        Width = 500,
        Opacity = .2,
        ForegroundColor = Color.DarkBlue
    };
    // Get dimensions of the spreadsheet content
    SpreadsheetContent content = watermarker.GetContent<SpreadsheetContent>();
    SpreadsheetBackgroundWatermarkOptions options = new SpreadsheetBackgroundWatermarkOptions();
    options.BackgroundWidth = content.Worksheets[0].ContentAreaWidthPx; /* set background width */
    options.BackgroundHeight = content.Worksheets[0].ContentAreaHeightPx; /* set background height */
    options.WorksheetIndex = 0;

    // Add watermark and save the watermarked spreadsheet.
    watermarker.Add(textWatermark, options);
    watermarker.Save(@"path/background-watermark-spreadsheet.xlsx");
}
```



{{< figure align=center src="images/watermark-excel-sheets-programmatically.png" alt="以编程方式水印 Excel 工作表">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][27] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们讨论了使用 C# 向 Excel 工作表添加水印的不同方法。首先，我们在 Excel 工作簿的所有工作表中添加了文本水印。然后我们只将水印应用于特定的工作表。最后，我们将基于文本的水印作为背景插入到 Excel 工作簿中。

访问产品 [文档][28] 以了解有关 API 的更多信息。如有疑问，请通过 [论坛][29] 联系我们。

## 也可以看看

* [Java 中的水印 Excel 工作表][30]
* [使用 C# 为 PDF 文件添加水印][31]
* [使用 C# 为演示幻灯片添加水印][32]
* [使用 C# 为图像添加水印][33]







[1]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[2]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[3]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[4]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[5]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[6]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[7]: #watermarking-dotnet-api
[8]: #watermark-all-sheets
[9]: #watermark-any-sheet
[10]: #watermark-sheet-as-background
[11]: https://products.groupdocs.com/watermark/
[12]: https://products.groupdocs.com/watermark/net/
[13]: https://downloads.groupdocs.com/watermark/net
[14]: https://www.nuget.org/packages/GroupDocs.Watermark/
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[19]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[20]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[21]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[22]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[23]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[24]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[25]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[26]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[27]: https://purchase.groupdocs.com/temporary-license
[28]: https://docs.groupdocs.com/watermark
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[31]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[32]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[33]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/


