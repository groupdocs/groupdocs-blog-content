---
title: "'使用 C# 将 Word 文档呈现为干净的 HTML'"
date: Fri, 25 Feb 2022 05:38:00 +0000
draft: false
url: /zh/2022/02/25/render-word-documents-as-clean-html-using-csharp/
author: 'Shoaib Khan'
summary: "HTML 的清理和缩小可以提高网页的加载时间和带宽使用率。据观察，当使用某些工具将一个文档转换为 HTML 格式时，会注入一些不必要的代码。您可以在 .NET 应用程序中删除这些不需要的代码。本文讨论**如何使用 C# 将 Word 文档呈现为缩小的 HTML**。"
tags: ['Minify HTML using CSharp', 'Word to Clean HTML', 'Word to Minified HTML']
categories: ['GroupDocs.Viewer Product Family']
---

HTML 的清理和缩小可以提高网页的加载时间和带宽使用率。据观察，当使用某些工具将一个文档转换为 HTML 格式时，会注入一些不必要的代码。您可以在 .NET 应用程序中删除这些不需要的代码。本文讨论**如何使用 C# 将 Word 文档呈现为缩小的 HTML**。



{{< figure align=center src="images/render-word-to-clean-html-using-dotnet.jpg" alt="使用 C# 将 Word 呈现为干净的 HTML">}}


## .NET API 呈现为缩小的 HTML {#stl-viewer-dotnet-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) 提供了一个[文档查看 API](https://products.groupdocs.com/viewer/net/)，允许将各种文档呈现为 HTML， .NET 应用程序中的 PDF 和图像格式。我将在示例中使用此 API 将 DOCX 文件转换为干净的 HTML 文件。

您可以从 [下载部分](https://downloads.groupdocs.com/viewer/net) 下载 DLL 或 MSI 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.viewer)。

```
PM> Install-Package GroupDocs.Viewer
```

## 使用 C# 将 Word DOC/DOCX 渲染为缩小的 HTML {#stl-to-pdf}

可以使用相应的方法通过嵌入式或外部资源获取 HTML 文件。以下步骤展示了如何使用 C# 将 Word 文档 (DOC/DOCX) 转换为缩小的 HTML。

* 使用 [Viewer](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer) 类加载 DOCX 文件。
* 使用 [HtmlViewOptions](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions) 类准备 HTML 呈现选项。
* 通过将其设置为 true 来启用 Minify 选项。
* 使用带有创建选项的 [View()](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view) 将 DOCX 文件呈现为缩小的 HTML。

以下 C# 代码示例将 Word DOCX 文件呈现为缩小的 HTML。

```
// 使用 C# 将 Word DOC/DOCX 转换为缩小的 HTML
using (Viewer viewer = new Viewer("path/document.docx"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("path/page_{0}.html");
    options.Minify = true;

    viewer.View(options);
}
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证](https://purchase.groupdocs.com/temporary-license) 免费使用这些 API，而不受评估限制。

## 结论

总而言之，我们讨论了如何使用 C# 将 DOC/DOCX 文件呈现为缩小的 HTML。您可以构建自己的在线转换器和清理器，允许用户将文档转换为缩小的 HTML。此外，您可以从其[文档](https://docs.groupdocs.com/viewer/) 中了解有关 [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net/) 的更多信息.如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [C#源代码转PDF](https://blog.groupdocs.com/2021/12/03/convert-source-code-to-pdf-in-csharp/)
* [使用 C# 的 STL 文件查看器](https://blog.groupdocs.com/2021/12/28/stl-file-viewer-using-csharp/)
* [使用 C# 查看 CAD 文档](https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-csharp/)
* [使用 C# 将 Word 文档作为 HTML 响应页面查看](https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/)





