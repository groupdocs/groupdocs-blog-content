---
title: "使用 C# 查看 CAD 文档"
date: Tue, 27 Apr 2021 20:23:00 +0000
draft: false
url: /zh/2021/04/27/view-cad-documents-using-csharp/
aliases:
- /2021/04/27/view-cad-documents-using-charp/
author: 'Shoaib Khan'
summary: '**CAD** (**C**omputer-**A**ided **D**esign) drawings are normally used to create architectural plans and models using CAD software programs. Some of the well-known AutoCAD file formats are **DWG, DXF, DGN, DWF**. We discussed [viewing the CAD drawings using Java][1] in a separate article. Today, in this article, we will discuss how to programmatically view CAD files using C# within .NET applications.

本文简要介绍了以下主题：

* .NET API 来渲染 CAD 文件。
* 将 CAD 文件转换为 HTML、JPG、PNG 或 PDF。
* 获取 DWG 的布局和图层。
* 渲染 DWG 图纸的 CAD 图层。
* 渲染 DWG 图纸的 CAD 布局。

[继续阅读...][2]'
tags: ['CAD Viewer in CSharp', 'Convert DWG to HTML in CSharp', 'Convert DWG to JPG in CSharp', 'DWG Viewer using CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

**CAD**（_计算机辅助设计_）图纸通常用于使用 CAD 软件程序创建建筑计划和模型。一些著名的 AutoCAD 文件格式是 **DWG、DXF、DGN、DWF**。我们在另一篇文章中讨论了[使用 Java 查看 CAD 图纸][3]。今天，在本文中，我们将讨论如何在 .NET 应用程序中使用 C# 以编程方式查看 CAD 文件。

以下主题简要介绍如下：

* [.NET API 渲染 CAD 文件][4]。
* [将 CAD 文件转换为 HTML、JPG、PNG 或 PDF][5]。
* [获取 DWG 的布局和图层][6]。
* [渲染 DWG 图纸的 CAD 图层][7]。
* [渲染 DWG 图纸的 CAD 布局][8]。

## .NET CAD 查看器 API – DWG、DXF、DWF、DGN {#dotnet-api-to-render-cad-files}

在本文中，我将使用 [GroupDocs.Viewer for .NET][9]，它允许在 .NET 应用程序中以编程方式将 DWG 等 CAD 文件渲染为 PDF、JPG、PNG 和 HTML。除了 DWG，API 还支持 DWF、DGN、DWT、DXF、IFC、STL、绘图仪文档和 [更多][10]。

除了 CAD 文件格式，API 还为文字处理文档、电子表格、演示文稿、网页、图像、矢量、电子书、Visio 绘图、许多不同编程语言的源代码文件提供相同的渲染功能。

从 [下载部分][11] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][12] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Viewer
```

## 在 C# 中将 CAD 绘图转换为 HTML、PNG、JPG 或 PDF 格式 {#convert-cad-to-html-jpg-jpg-pdf-in-csharp}

在本文中，我仅使用 DWG 格式进行转换和渲染为其他格式，并附有示例。让我们从 DWG 设计文件的转换开始，使用 C# 将其呈现为带有嵌入式和外部资源选项的 HTML。

### 使用 C# 中的嵌入式资源将 DWG 转换为 HTML

以下是如何将 DWG 文件转换为 HTML 渲染的步骤。

* 使用 [Viewer][13] 类加载 DWG 文件。
* 使用 _[forEmbeddedResources][15]_ 方法创建 [HtmlViewOptions][14]。
* 使用 _[View][16]_ 方法将 .dwg 渲染为 HTML。

以下源代码转换 DWG 文件并使用 C# 将其呈现为带有嵌入资源的 HTML。

```
// 使用 C# 将 DWG CAD 绘图渲染为带有嵌入式资源的 HTML
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources("page_{0}.html");
    viewer.View(viewOptions);
}
```

### 使用 C# 中的外部资源将 DWG 转换为 HTML

以下是转换 DWG 文件并将其渲染为具有外部资源的 HTML 文件的步骤。

* 使用 [Viewer][17] 类加载 DWG 文件。
* 使用 _[forExternalResources][19]_ 方法创建 [HtmlViewOptions][18]。
* 使用 _[View][20]_ 方法将 .dwg 渲染为 HTML。

以下源代码将 DWG 文件呈现为带有 C# 中的外部资源的 HTML。

```
// 使用 C# 将 C# CAD 绘图渲染为带有外部资源的 HTML
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    HtmlViewOptions viewOptions = HtmlViewOptions.ForExternalResources(
        "page_{0}.html","page_{0}/resource_{1}","page_{0}/resources");

    viewer.View(viewOptions);
}
```

### 在 C# 中将 DWG 转换为 PDF、JPG 和 PNG

就像转换为 HTML 格式一样，DWG 文件可以使用各自的 [ViewOptions][21] 呈现为 PDF、PNG 和 JPG 格式，如下所示：

* **HTML** 使用 [HtmlViewOptions][22] 呈现。
* **JPG** 使用 [JpgViewOptions][23] 渲染。
* **PNG** 使用 [PngViewOptions][24] 渲染。
* **PDF** 使用 [PdfViewOptions][25] 渲染。

## 在 C# 中获取 DWG 的布局和图层 {#get-layout-and-layers-of-dwg-in-csharp}

CAD 文件可以包含多个布局和图层，您可以使用以下步骤获取这些布局和图层。

* 使用 [Viewer][26] 类加载 DWG 文件。
* 为 HTML 视图渲染创建 [ViewInfoOptions][27]。
* 使用查看器，获取具有布局的 [CadViewInfo][28]。
* 从 CadViewInfo 获取布局并对其进行迭代。
* 同样，从 CadViewInfo 获取图层并对其进行迭代。

以下代码显示了如何使用 C# 获取 ا DWG 文件的布局和图层。

```
// 在 C# 中获取 DWG CAD 绘图的布局和图层
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    ViewInfoOptions viewInfoOptions = ViewInfoOptions.ForHtmlView();
    CadViewInfo viewInfo = viewer.GetViewInfo(viewInfoOptions) as CadViewInfo;

    Console.WriteLine("File type: " + viewInfo.FileType);
    Console.WriteLine("Pages count: " + viewInfo.Pages.Count);

    foreach (Layout layout in viewInfo.Layouts)
        Console.WriteLine(layout);

    foreach (Layer layer in viewInfo.Layers)
        Console.WriteLine(layer);
}
```

## 在 C# 中渲染 DWG 文件的 CAD 图层 {#render-layers-of-dwg-in-csharp}

如果您不想渲染所有图层，而只想渲染 DWG 的某些特定图层，则可以通过设置图层名称来完成。

* 使用 [Viewer][29] 类加载 DWG 绘图。
* 创建视图选项。
* **将 CAD 图层添加到视图选项**
* 使用 _[View][30]_ 方法将 DWG 渲染为 HTML。

以下代码以 C# 呈现 DWG 格式的 CAD 文件的图层。

```
// 在 C# 中渲染 .dwg CAD 绘图的图层
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources();
    viewOptions.CadOptions.Layers = new List<Layer>
    {
        new Layer("Walls"),
        new Layer("Windows")
    };
    viewer.View(viewOptions);
}
```

## 在 C# 中渲染 DWG 文件的 CAD 布局 {#render-layouts-of-dwg-in-csharp}

默认情况下，我们仅在渲染 CAD 文件时获得模型演示。我们可以设置属性来渲染所有非空布局以及模型。

* 使用 [Viewer][31] 类加载 DWG 绘图。
* 创建视图选项。
* **将渲染布局属性设置为 true。**
* 使用 _[View][32]_ 方法将 DWG 渲染为 HTML。

以下代码以 C# 中的 DWG 格式呈现所有非空布局以及 CAD 绘图模型。

```
// 在 C# 中渲染 .dwg CAD 绘图的布局
using (Viewer viewer = new Viewer("drawing.dwg"))
{
   HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources();
   viewOptions.CadOptions.RenderLayouts = true;
   viewer.View(viewOptions);
}
```

## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][33] 以便在没有评估限制的情况下使用 API。

## 结论

最后，我希望您已经学会了如何在 .NET 应用程序中使用 C# 查看 CAD 文件。此外，您还了解了如何在应用程序中获取和显示 CAD 文件的模型、布局和图层。您必须有信心使用 C# 构建自己的 CAD 查看器。您可以[体验在线应用程序以查看您的任何文件][34]。这些是使用 GroupDocs.Viewer 构建的。

您可以使用 [文档][35] 了解有关 .NET 的 GroupDocs.Viewer 的更多信息。如果您有任何疑问，请随时通过我们的 [论坛][36] 告诉我们。

## 也可以看看

* [使用 Java 查看 CAD 文档][37]
* [在 C# 中将 CAD 绘图转换为 PDF][38]
* [使用 C# 将 Word 文档呈现为干净的 HTML][39]







[1]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[2]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[3]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[4]: #dotnet-api-to-render-cad-files
[5]: #convert-cad-to-html-jpg-jpg-pdf-in-csharp
[6]: #get-layout-and-layers-of-dwg-in-csharp
[7]: #render-layers-of-dwg-in-csharp
[8]: #render-layouts-of-dwg-in-csharp
[9]: https://products.groupdocs.com/conversion/net
[10]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[11]: https://downloads.groupdocs.com/viewer/net
[12]: https://www.nuget.org/packages/groupdocs.viewer
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/methods/forembeddedresources/index
[16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/methods/forexternalresources/index
[20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[21]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewoptions
[22]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
[24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
[25]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[26]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[27]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions
[28]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo
[29]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[30]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[31]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[32]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[33]: https://purchase.groupdocs.com/temporary-license
[34]: https://products.groupdocs.app/viewer/family
[35]: https://docs.groupdocs.com/viewer/net/
[36]: https://forum.groupdocs.com/
[37]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[38]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[39]: https://blog.groupdocs.com/2022/02/25/render-word-documents-as-clean-html-using-csharp/


