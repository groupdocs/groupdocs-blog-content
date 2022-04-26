---
title: "C# 中的图像比较以发现差异"
date: Wed, 06 Jan 2021 17:52:00 +0000
draft: false
url: /zh/2021/01/06/compare-images-in-csharp-dotnet/
aliases:
- /2019/09/12/compare-two-images-in-c-.net-and-java/
- /2019/09/12/compare-two-images-in-csharp-.net-and-java/
- /2019/09/12/compare-two-images-in-csharp-dotnet-and-java/
author: 'Shoaib Khan'
summary: "无论您是想构建一个具有发现差异功能的应用程序，还是想在任何基于 .NET 的图像处理应用程序中比较两个图像，您都来对了地方。在本文之后，您可以轻松地将 JPG、PNG、BMP 或图像与其他一些文件格式进行比较。不浪费时间，让我们使用 [.NET API 进行文档和图像转换][1] 比较 C# 中的图像。"
tags: ['compare images in csharp', 'compare jpg or png in csharp', 'Image Comparison', 'image comparison in csharp']
categories: ['GroupDocs.Comparison Product Family']
---

无论您是想构建具有发现差异功能的应用程序，还是想在任何基于 .NET 的图像处理应用程序中以编程方式比较两个图像，您都来对了地方。在本文之后，您可以轻松地将 JPG、PNG、BMP 或图像与其他一些文件格式进行比较。不要浪费时间，让我们使用 [.NET API for document and image comparison][2] 在 C# 中比较图像。



{{< figure align=center src="images/compare-images-to-find-differences-in-dotnet.jpg" alt="使用 .NET 比较图像的差异">}}


## .NET 图像比较 API

在本文中，我将使用 [GroupDocs.Comparison for .NET][3] API 来比较图像。此 API 支持比较**JPG、PNG、BMP、DICOM、DCM、DjVu** 图像以及许多其他[支持的文件格式][4]。

您可以从 [下载部分][5] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Comparison
```

## 比较 C# 中的图像以突出显示差异

使用 .NET 应用程序中的 GroupDocs.Comparison 在 C# 中比较两个图像太容易了。以下步骤解释了我们如何比较任意两个 JPG、PNG、BMP 或任何其他图像。它成功检测到更改并在输出/结果图像中突出显示它们。

* 使用 [Comparer][7] 类定义第一张图片。
* 使用 Comparer 对象的 [Add][8] 方法添加第二张图片。
* 调用 [Compare][9] 方法比较两个图像并保存突出显示两个图像之间差异的结果图像。

下面的代码显示了如何在 C# 中比较两个图像。例如，它比较两个 JPG 图像并保存有差异的输出。

```
// 使用 C# 中的 .NET 图像比较 API 比较 JPG、PNG、GIF、BMP 图像格式
using (Comparer comparer = new Comparer("filepath/soureImage.jpg"))
{
    CompareOptions options = new CompareOptions();
    options.GenerateSummaryPage = false; // To get the difference summary, set it 'true'

    comparer.Add("filepath/targetImage.jpg");
    comparer.Compare("filepath/comparisonResultImage.jpg", options);
}
```

本文开头显示的图像用于此代码。比较左侧的图像，右侧显示输出以突出显示差异。

## 结论

在本文中，我们学习了如何使用图像比较 API 在 C# 中比较两个图像。现在您可以构建自己的图像比较应用程序，该应用程序可以比较图像并向用户突出显示发现的差异。

要全面了解 API 的功能，您可以浏览 [文档][10]。您还可以联系 [免费支持团队][11] 或 [免费咨询团队][12]，他们甚至会根据您的要求编写代码来帮助您了解 GroupDocs API 的使用。

## 也可以看看

* [比较Java中的图像以发现差异][13]
* [比较 C# 中的 Excel、Word、PDF 或 PowerPoint 文件][14]







[1]: https://products.groupdocs.com/comparison/net
[2]: https://products.groupdocs.com/comparison/net
[3]: https://products.groupdocs.com/comparison/net
[4]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/comparison/net
[6]: https://www.nuget.org/packages/groupdocs.comparison
[7]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[8]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[10]: https://docs.groupdocs.com/comparison/net/
[11]: https://forum.groupdocs.com/c/comparison
[12]: https://groupdocs-free-consulting.github.io/
[13]: https://blog.groupdocs.com/2021/06/16/compare-images-in-java/
[14]: https://blog.groupdocs.com/2020/03/10/compare-excel-word-pdf-files-in-csharp/


