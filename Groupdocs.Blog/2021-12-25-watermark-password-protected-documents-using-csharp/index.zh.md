---
title: "使用 C# 的水印密码保护文档"
date: Sat, 25 Dec 2021 07:54:23 +0000
draft: false
url: /zh/2021/12/25/watermark-password-protected-documents-using-csharp/
aliases:
- /2019/11/22/watermark-password-protected-documents-using-groupdocs-watermark-net-api/
author: 'Shoaib Khan'
summary: "水印是保护您的文档免遭非法使用的方法之一；品牌化您的文件；将您的文件作为草稿或机密文件提及。为了以编程方式为您的文件添加水印，本文将指导您**如何使用 C#** 为受密码保护的文件添加水印。我们将分别研究向受保护文件添加文本和图像水印。"
tags: ['Document Watermarking', 'Watermark Protected Documents using CSharp', 'Watermark Protected Files using CSharp', 'watermark using csharp', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/watermark-protected-files-using-csharp.jpg" alt="使用 C# 的水印保护文档">}}


水印是保护您的文档免遭非法使用的方法之一；品牌化您的文件；将您的文件作为草稿或机密文件提及。为了以编程方式为您的文件添加水印，本文将指导您**如何使用 C#** 为受密码保护的文件添加水印。我们将分别研究向受保护文件添加文本和图像水印。

此处讨论了以下主题：

* [.NET API 到水印密码保护文件][1]
* [使用 C# 为受保护的文件添加水印][2]
    * [应用文字水印][3]
    * [应用图像水印][4]

## .NET API 到水印密码保护文件 {#watermarking-dotnet-api}

[GroupDocs.Watermark][5] 提供了水印解决方案并展示了 [.NET API，允许在 .NET 应用程序中使用水印][6]。我将使用此 API 将文本和图像水印添加到受密码保护的文件中。

您可以从 [下载部分][7] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Watermark
```

## 使用 C# 向受密码保护的文件添加水印 {#add-watermark-to-protected-files}

这很简单；只需几行代码，您就可以在文件中添加水印。只需按照以下步骤添加任一类型的水印。

* **加载**受保护的文档/文件。
* **应用**文本/图像水印。
* **保存**带水印的文件。

下面我们分别看看如何添加文字水印，然后是图片水印。

## 使用 C# 将文本水印添加到受保护的文件 {#text-watermark-to-protected-file}

文本水印最常用于将公司名称放在文档中；将文件提及为草稿或机密；或任何其他类似原因。以下步骤指导如何使用 C# 将文本水印插入受密码保护的文件。

* 使用现有密码准备[加载选项][9]。
* 使用 [Watermarker][10] 类和**加载选项**加载受保护的文件。
* 使用 [TextWatermark][11] 类准备水印。
* 设置水印的文字、外观、旋转、不透明度、颜色等属性。
* 使用 [Add()][12] 方法为文档添加水印。
* 使用[Save()][13]方法保存水印文件。

以下 C# 代码将文本水印插入到受保护的 PDF 文档中。

```
/*
 * Apply Text Watermark to document (PDF, Word, PPT, Excel, ...) using C#
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$$w0rd";
string filePath = "path/document.pdf";
using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
{
    // Prepare Watermark Text and appearance. 
    TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 12))
    {
        RotateAngle = -45,
        Opacity = .3,
        ForegroundColor = Color.Red,
    };
    // Add watermark to document and save.
    watermarker.Add(watermark);
    watermarker.Save("path/watermark-document.pdf");
}
```

## 使用 C# 将图像水印添加到受保护的文件 {#image-watermark-to-protected-file}

如果您想插入您的徽标或其他图像作为水印，您可以使用 ImageWatermark 类添加它。以下步骤允许您使用 C# 将图像水印添加到受密码保护的文档中。

* 使用现有密码准备[加载选项][14]。
* 使用 [Watermarker][15] 类和**加载选项**加载受保护的文件。
* 使用 [ImageWatermark][16] 类加载水印图像文件。
* 设置水印的外观、对齐方式、坐标、旋转、不透明度等属性。
* 使用 [Add()][17] 方法为文档添加水印。
* 使用[Save()][18]方法保存水印文件。

以下 C# 代码将图像水印插入到受保护的 MS Word DOCX 文档中。

```
/*
 * Apply Image Watermark to document (PDF, Word, PPT, Excel, ...) using C#
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.Password = "P@$$w0rd";
string filePath = "path/document.docx";
using (Watermarker watermarker = new Watermarker(filePath, loadOptions))
{
    // Prepare Watermark Text and appearance. 
    ImageWatermark watermark = new ImageWatermark("watermark-logo.png")
    {
        Opacity = 0.7,
        X = 70,
        Y = 350
    };    
    // Add image watermark to document and save.
    watermarker.Add(watermark);
    watermarker.Save("path/watermark-document.docx");
}
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证][19] 免费使用这些 API。

## 结论

总而言之，我们学会了使用 C# 在 .NET 应用程序中向受密码保护的文件中添加文本水印和图像水印。此外，我们在添加时为水印的外观添加了一些自定义项。

同样，您可以将水印应用于文档中的选择性**页面**、选定的**演示文稿幻灯片**和特定的**工作簿表**。详见[相关文章][20]。

要了解有关 [GroupDocs.Watermark for .NET][21] 的更多信息，请访问其 [文档][22]。如有疑问，请通过 [论坛][23] 联系我们。

## 相关文章 {#releated-articles}

* [在 C# 中查找并**删除文档中的水印**][24]
* [水印**Excel表格**使用C#][25]
* [水印**PDF**文件使用C#][26]
* [使用 C# 将水印添加到**演示幻灯片**][27]
* [使用 C# 将水印添加到**图像**][28]





[1]: #watermarking-dotnet-api
[2]: #add-watermark-to-protected-files
[3]: #text-watermark-to-protected-file
[4]: #image-watermark-to-protected-file
[5]: https://products.groupdocs.com/watermark/
[6]: https://products.groupdocs.com/watermark/net/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://www.nuget.org/packages/groupdocs.watermark
[9]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options/loadoptions
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.options/loadoptions
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[18]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[19]: https://purchase.groupdocs.com/temporary-license
[20]: #releated-articles
[21]: https://products.groupdocs.com/watermark/net/
[22]: https://docs.groupdocs.com/watermark/
[23]: https://forum.groupdocs.com/
[24]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[25]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[26]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[27]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[28]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/


