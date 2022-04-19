---
title: "'如何使用 C# 重新排列 PDF 页面'"
date: Tue, 22 Feb 2022 12:10:45 +0000
draft: false
url: /zh/2022/02/22/move-pdf-pages-using-csharp/
author: 'Shoaib Khan'
summary: "在这个数字时代，PDF 是最常用的文件格式之一，并且因其便携性而广受欢迎。另一方面，大多数时候我们不能编辑 PDF 文件。当我们将多个文档和页面合并在一起形成一个组合的综合文档时，经常会发生我们以错误的顺序完成页面组合的情况。本文讨论，**如何使用 C# 以编程方式重新排列 PDF 页面**。"
tags: ['Rearrange Document', 'Rearrange PDF Pages', 'Rearrange PDF Pages in CSharp']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-pdf-pages-using-csharp-dotnet.jpg" alt="使用 C# .NET 重新排列 PDF 页面">}}


在这个数字时代，PDF 是最常用的文件格式之一，并且因其便携性而广受欢迎。另一方面，大多数时候我们不能编辑 PDF 文件。当我们将多个文档和页面合并在一起形成一个组合的综合文档时，经常会发生我们以错误的顺序完成页面组合的情况。本文讨论，**如何使用 C# 以编程方式重新排列 PDF 页面**。

## .NET API 重新排列 PDF 页面和合并文档

为了重新排列文档中的页面，GroupDocs 提供了 [GroupDocs.Merger for .NET](https://products.groupdocs.com/merger/net/)。该 API 支持在 .NET 应用程序中移除、拆分和提取页面、更改页面方向以及旋转文档页面。有关 API 的详细信息和其他功能，您可以访问[文档](https://docs.groupdocs.com/merger/net/)。

您可以从[下载部分](https://downloads.groupdocs.com/merger)下载 DLL 或 MSI 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.merger) 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 使用 C# 重新排列 PDF 页面

以下是使用 C# 重新排列 PDF 文档页面的步骤。

* 在 [MoveOptions](https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/moveoptions) 类中定义页面的现有位置和新位置。
* 使用 [Merger](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger) 类加载 PDF 文档。
* 使用 [MovePage()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/movepage) 方法根据定义的选项重新排序。
* 使用 [Save()](https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index) 方法以新的页面顺序保存 PDF 文件。

以下 C# 代码重新排列 PDF 文档的页面。准确地说，它将文档的第 6 页移动到第 1 位。

```
// 使用 C# 重新排列 PDF 文档的页面
int pageNumber = 6;
int newPageNumber = 1;

MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
using (Merger merger = new Merger("path\document.pdf"))
{
    merger.MovePage(moveOptions);
    merger.Save("path\rearranged-document.pdf");
}
```

这是上述代码的输出。



{{< figure align=center src="images/Screenshot-1024x454.png" alt="">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们学习了如何在 .NET 应用程序中使用 C# 对 PDF 文件的页面进行重新排序。我们看到了改变页面位置的运行示例。您可以尝试构建一个简单的应用程序，该应用程序可以通过轻松打乱它们的页面来组织 PDF 文件。

有关 API 的更多详细信息，请访问 [文档](https://docs.groupdocs.com/merger/)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [如何在 Java 中重新排列 PDF 页面](https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/)
* [使用 C# 密码保护 PDF 文件](https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/)
* [使用 C# 拆分 PDF 文件](https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/)
* [使用 C# 将多种文件类型合并到一个文档中](https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/)





