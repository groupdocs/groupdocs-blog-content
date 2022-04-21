---
title: "'如何使用 C# 在 Word 中重新排列页面'"
date: Sat, 05 Feb 2022 08:19:00 +0000
draft: false
url: /zh/2022/02/05/move-word-pages-using-csharp/
author: 'Shoaib Khan'
summary: "在数字世界中，文字处理文档是用于创建和编辑文档的最常用的文件格式之一。在处理大型文档时，在不丢失格式的情况下移动页面确实很不容易。当我们尝试[合并多个不同类型的文档](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/) 或者我们只是[将相同类型的文件](https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/) 合并到一个文档中。为了重新排列页面，本文讨论了**如何使用 C# 以编程方式在 Word 文档 (DOC/DOCX) 中移动页面**。"
tags: ['Move Pages in CSharp', 'Move Pages in DOC/DOCX', 'Rearrange Document', 'Rearrange Document Pages in CSharp', 'Rearrange pages in CSharp', 'Rearrange pages in Word']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-word-pages-using-csharp-dotnet.jpg" alt="使用 C# .NET 重新排列 Word 页">}}


在数字世界中，文字处理文档是用于创建和编辑文档的最常用的文件格式之一。在处理大型文档时，在不丢失格式的情况下移动页面确实很不容易。当我们尝试[合并多个不同类型的文档](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/) 或者我们只是[将相同类型的文件](https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/) 合并到一个文档中。为了重新排列页面，本文讨论了**如何使用 C# 以编程方式在 Word 文档 (DOC/DOCX) 中移动页面**。

## .NET API 移动 Word 文档页面

**GroupDocs.Merger** 提供了 .NET API，它可以在 .NET 应用程序中移动、删除、拆分文档和提取页面、更改页面方向以及旋转文档页面。今天，我们将使用这个 API 来使用 C# 移动 DOC/DOCX 文件的页面。有关 API 的详细信息和其他功能，您可以访问[文档](https://docs.groupdocs.com/merger/)。

您可以从[下载部分](https://downloads.groupdocs.com/merger)下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.merger) 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 使用 C# 在 Word 文档中移动页面

页面的移动很简单。只需命令该特定页面移动到其新位置。以下是使用 C# 重新排列 Word 文档页面的步骤。

* 使用 [MoveOptions](https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/moveoptions) 类定义目标页面的页码及其新位置。
* 使用 [Merger](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger) 类加载 DOC/DOCX 文档。
* 使用 [MovePage()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/movepage) 方法移动页面。
* 使用 [Save()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index) 方法保存重新排列的文档。

以下 C# 代码有助于重新排列 Word 文档的页面。准确地说，它会将 DOCX 文档的第 7 页移至第 2 位。

```
// 使用 C# 重新排列文字处理文档 (DOC/DOCX) 的页面
int pageNumber = 7;
int newPageNumber = 2;

MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
using (Merger merger = new Merger("path\document.docx"))
{
    merger.MovePage(moveOptions);
    merger.Save("path\rearranged-document.docx");
}
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们学习了如何在 .NET 应用程序中使用 C# 更改 Word 文档中的页面顺序。我们看到了更改 DOCX 文件中页面位置的源代码示例。您可以构建自己的应用程序，通过轻松打乱页面来在线重新排列 Word 页面。

有关 API 的更多详细信息，请访问 [文档](https://docs.groupdocs.com/merger/net)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [比较 Word 文档](https://blog.groupdocs.com/2021/12/01/compare-word-documents-using-csharp/)
* [编辑 Word 文档](https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/)
* [使用密码保护/取消保护 Word 文件](https://blog.groupdocs.com/2021/11/27/password-protect-word-documents-using-csharp/)
* [将 Word 文档作为 HTML 响应页面查看](https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/)
* [添加或删除注释或标记 Word 文件](https://blog.groupdocs.com/2021/06/23/annotate-word-documents-using-csharp/)





