---
title: "使用 C# 的 STL 文件查看器"
date: Tue, 28 Dec 2021 11:00:00 +0000
draft: false
url: /zh/2021/12/28/stl-file-viewer-using-csharp/
author: 'Shoaib Khan'
summary: 'STL (STereoLithography) file format is used for 3D CAD drawings and 3D printing. There are several requirements when the developers are required to programmatically render STL files into various other formats. One of the reasons for conversion is better portability. In this article, you will learn how to render the STL files into PDF format using C#. Additionally, we will convert the STL files to HTML, JPG, and PNG format within .NET application using examples.

本文讨论了以下主题：

* STL 查看器 .NET API
* 以 PDF 格式查看 STL
* 以 HTML、JPG、PNG 格式查看 STL'
tags: ['STL as HTML', 'STL as JPG', 'STL as PNG', 'STL Viewer', 'STL Viewer using C#', 'View STL', 'View STL as PDF']
categories: ['GroupDocs.Viewer Product Family']
---

STL (**ST**ereo**L**ithography) 文件格式用于 3D CAD 绘图和 3D 打印。当要求开发人员以编程方式将 STL 文件呈现为各种其他格式时，有几个要求。转换的原因之一是更好的便携性。在本文中，您将学习**如何使用 C# 将 STL 文件呈现为 PDF 格式**。此外，我们将使用示例在 .NET 应用程序中将 **STL 文件转换为 HTML、JPG 和 PNG 格式**。

下面讨论以下主题：

* [STL 查看器 .NET API][1]
* [以 PDF 格式查看 STL][2]
* [以 HTML、JPG、PNG 格式查看 STL][3]

## .NET API 查看 STL 文件 {#stl-viewer-dotnet-api}

[GroupDocs.Viewer][4] 展示了 [文档查看器 .NET API][5]，它允许在 .NET 应用程序中将文档呈现为 PDF、HTML 和图像。在本文中，我们将在示例中使用它来将 STL 文件转换为不同的其他文件格式。

您可以从 [下载部分][6] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Viewer
```

## 使用 C# 以 PDF 格式查看 STL 文件 {#stl-to-pdf}

由于其高便携性，通常需要将立体光刻 STL 格式转换为 PDF 格式。以下步骤展示了如何使用 C# 将 STL 文件转换为 PDF 格式。

* 使用 [Viewer][8] 类加载 STL 文件。
* 使用 [PdfViewOptions][9] 类准备 PDF 渲染选项。
* 使用 [View()][10] 方法将 STL 文件呈现为 PDF。

以下 C# 代码示例将 STL 文件呈现为 PDF 格式。

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    PdfViewOptions options = new PdfViewOptions("path/stl-output.pdf");
    viewer.View(options);
}
```

## 使用 C# 以 HTML、JPG 或 PNG 格式查看 STL 文件 {#convert-stl-using-csharp}

同样，您可以根据需要将 STL 文件转换为其他格式。以下步骤可帮助您使用 C# 将 STL 文件呈现为各种其他格式。

* 使用 [Viewer][11] 类加载 **STL** 文件。
* 根据转换格式准备渲染选项：
    * **HTML** 渲染需要 [](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions)[HtmlViewOptions][12] 类。 （您可以使用嵌入式或外部资源）
    * **JPG** 渲染使用 [JpgViewOptions][13] 类。
    * **PNG** 渲染需要 [PngViewOptions][14] 类。
* 使用 [View()][15] 方法将 STL 文件呈现为 HTML、JPG 或 PNG。

以下是使用相应格式选项将 STL 文件单独呈现为每种格式的 C# 示例。

### STL 到 HTML 使用 C# {#stl-to-html}

以下 C# 代码将 STL 文件转换为带有嵌入资源的 HTML。同样，您可以使用外部资源转换为 HTML。

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("path/stl-output.html");
    viewer.View(options);
}
```

### STL 到 JPG 使用 C# {#stl-to-jpg}

以下 C# 代码将 STL 文件转换为 JPG 图像格式。

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    JpgViewOptions options = new JpgViewOptions("path/stl-output.jpg");
    viewer.View(options);
}
```

### STL 到 PNG 使用 C# {#stl-to-png}

以下 C# 代码将 STL 文件转换为 PNG 图像格式。

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    PngViewOptions options = new PngViewOptions("path/stl-output.png");
    viewer.View(options);
}
```

## 获取免费 API 许可证

您可以通过[获得临时许可证][16]免费使用 API。

## 结论

最后，我们学习了如何将 STL 文件呈现为其他格式。具体来说，我们使用 C# 示例将 STL 文件转换为 PDF、HTML、JPG 和 PNG 格式。您可以构建自己的 STL 查看器应用程序，例如 [Groupdocs.Viewer Online App][17]。

要了解有关 [GroupDocs.Viewer for .NET][18] 的更多信息，请访问其 [文档][19]。如有疑问，请通过 [论坛][20] 联系我们。

## 也可以看看

* [C#源代码转PDF][21]
* [使用 C# 查看 CAD 文档][22]
* [使用 C# 将 Word 文档作为 HTML 响应页面][23]



[1]: #stl-viewer-dotnet-api
[2]: #stl-to-pdf
[3]: #convert-stl-using-csharp
[4]: https://products.groupdocs.com/viewer/
[5]: https://products.groupdocs.com/viewer/net/
[6]: https://downloads.groupdocs.com/viewer/net
[7]: https://www.nuget.org/packages/groupdocs.viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[11]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[12]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://products.groupdocs.app/viewer
[18]: https://products.groupdocs.com/viewer/net/
[19]: https://docs.groupdocs.com/viewer/
[20]: https://forum.groupdocs.com/
[21]: https://blog.groupdocs.com/2021/12/03/convert-source-code-to-pdf-in-csharp/
[22]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-csharp/
[23]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/


