---
title: "使用 C# 将 Word 文档作为 HTML 响应页面查看"
date: Sat, 28 Aug 2021 12:35:45 +0000
draft: false
url: /zh/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/
author: 'Shoaib Khan'
summary: "HTML 响应式网页旨在在不同的设备上看起来不错。这些页面会根据不同的屏幕尺寸自动调整。本文将指导您使用 C# 在 .NET 应用程序中自动转换并查看 Word 文档作为响应式 HTML 页面。"
tags: ['convert docx to html in csharp', 'docx to html responsive', 'view word as html responsive', 'Word to HTML in CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

HTML 响应式网页旨在在不同的设备上看起来不错。这些页面会根据不同的屏幕尺寸自动调整。本文将指导您使用 C# 在 .NET 应用程序中自动转换并查看 Word 文档作为响应式 HTML 页面。



{{< figure align=center src="images/word-to-responsive-html-layout-using-dotnet-1024x614.jpg" alt="使用 C# .NET API 的 Word 到响应式 HTML 布局">}}


下面将介绍以下主题：

* [.NET API for Word 和响应式 HTML 查看器][1]
* [使用 C# 将 Word 文档作为响应式 HTML 查看][2]

## 用于 Word 和响应式 HTML 查看器的 .NET API {#html-viewer-dotnet-api}

在下面的示例中，我将使用 [GroupDocs.Viewer for .NET][3] 将 Word 文档呈现为响应式 HTML 页面。该 API 是一个功能强大的 [支持呈现大量文档的文档查看器 .NET API][4]。它允许构建带有嵌入式和外部资源的**HTML 查看器**、通过呈现为 JPG 和 PNG 的**图像查看器**，以及最适合打印或与他人共享的**PDF 查看器**。

您可以从 [下载部分][5] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][6] 将其包添加到您的 .NET 应用程序来安装 API。

```
PM> Install-Package GroupDocs.Viewer
```

## 使用 C# 将 Word 文档转换为响应式 HTML 查看 {#word-to-html-responsive}

如果您有 MS Word DOC、DOCX 文档，并希望将这些文档呈现为响应式 HTML 页面，以便在所有不同的屏幕尺寸上看起来都很好，这里有适合您的步骤和 C# 代码。

以下步骤展示了如何使用 .NET API 将 Word 文档 (DOC/DOCX) 转换为响应式 HTML。

* 使用 [Viewer][7] 类加载 Word 文档 (DOC/DOCX)。
* 为 html 输出的嵌入式或外部资源设置 [HtmlViewOptions][8]。
* 将 [RenderResponsive][9] 设置为 true。
* 调用Viewer类的[View][10]方法生成加载的Word文档的响应式网页。

下面的四行源代码使用 C# 将 Word 文档呈现为具有嵌入式资源的响应式 HTML。

```
// 在 C# 中将 Word DOC/DOCX 文档转换为 HTML 响应页面
using (Viewer viewer = new Viewer(@"path/document.docx"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("path/page_{0}.html");
    options.RenderResponsive = true; // Set the Responsive as true
    viewer.View(options);
}
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][11] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，您已经学习了如何使用 C# 将 Word 文档呈现为响应式 HTML 页面。此外，您可以生成带有嵌入和外部资源的 HTML 页面。您必须有信心开始构建您自己的文档查看器 .NET 应用程序，例如 [由 GroupDocs 构建的][12]。

有关 API 的更多信息，您可以访问 [documentation][13] 和 [GitHub][14] 存储库。如果有进一步的疑问和歧义，请联系 [论坛][15] 上的免费支持。

## 也可以看看

* [如何使用 Java 将 Word 文档视为响应式 HTML][16]
* [使用 C# 查看 CAD 文档][17]
* [使用 C# 在网页中播放和暂停动画图像][18]
* [使用 C# 将 Word 文档呈现为缩小的 HTML][19]







[1]: #html-viewer-dotnet-api
[2]: #word-to-html-responsive
[3]: https://products.groupdocs.com/viewer/net/
[4]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/viewer
[6]: https://www.nuget.org/packages/groupdocs.viewer
[7]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/properties/renderresponsive
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://products.groupdocs.app/viewer/total
[13]: https://docs.groupdocs.com/viewer/net/
[14]: https://github.com/groupdocs-viewer
[15]: https://forum.groupdocs.com/c/assembly
[16]: https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/
[17]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[18]: https://blog.groupdocs.com/2021/02/28/play-pause-animated-gif-and-apng-in-web-pages-using-csharp/
[19]: https://blog.groupdocs.com/2022/02/25/render-word-documents-as-clean-html-using-csharp/


