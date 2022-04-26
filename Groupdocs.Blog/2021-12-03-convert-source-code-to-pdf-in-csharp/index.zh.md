---
title: "在 C# 中将源代码转换为 PDF"
date: Fri, 03 Dec 2021 17:19:00 +0000
draft: false
url: /zh/2021/12/03/convert-source-code-to-pdf-in-csharp/
aliases:
- /2019/06/28/create-your-source-code-viewer-using-groupdocs.viewer-for-.net-19.6/
author: 'Shoaib Khan'
summary: "您有时需要将源代码文件转换为其他格式。它可能用于共享或分析目的。本文讨论**如何在 .NET 应用程序中将 Python**、PHP、Java、C#、C/C++** 源代码文件转换为 PDF** 格式。此外，我们将以编程方式对转换后的文件进行密码保护。"
tags: ['Convert Source Code to PDF in CSharp', 'document rendering API', 'Java to PDF', 'PHP to PDF', 'Python Code to PDF', 'Source Code to PDF', 'source code viewer']
categories: ['GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/convert-source-code-to-pdf-in-csharp.jpg" alt="使用 C# 将源代码转换为 PDF">}}


您有时需要将源代码文件转换为其他格式。它可能用于共享或分析目的。本文讨论**如何在 .NET 应用程序中将 Python**、PHP、Java、C#、C/C++** 源代码文件转换为 PDF** 格式。此外，我们将以编程方式对转换后的文件进行密码保护。

* [源代码转换.NET API][1]
* [Java 转 PDF 使用 C#][2]
* [Python 到 PDF 使用 C#][3]
* [PHP 转 PDF - 保护 PDF 文件][4]

## 用于源代码转换的 .NET API {#source-code-converter-dotnet-api}

[GroupDocs.Viewer for .NET][5] 是文档查看器 API，允许使用 .NET 应用程序将文档呈现为 PDF、HTML 和图像。今天，我们将在示例中使用该 API 将不同语言的源代码文件转换为 PDF 格式。

您可以从 [下载部分][6] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][7] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Viewer
```

## 使用 C# 将 Java 代码转换为 PDF {#java-to-pdf}

无需涉及复杂的配置，只需加载 Java 文件，并将其转换为 PDF。以下步骤将指导您如何使用 C# 将 Java 源代码文件转换为 PDF。

* 使用 [Viewer][8] 类加载 Java 文件。
* 使用 [PdfViewOptions][9] 类设置输出文件及其选项。
* 使用适当的 [View()][10] 方法将文件转换为 PDF。

以下 C# 示例将完整的 Java 源代码文件转换为 PDF 格式。

```
/*
 * Renders a Java file into PDF using C#
 */
using (Viewer viewer = new Viewer("path/HelloWorld.java"))
{
   PdfViewOptions viewOptions = new PdfViewOptions("path/HelloWorld.pdf");
   viewer.View(viewOptions);
}
```

这是使用上述 C# 代码突出显示的 Java 文件转换后的 PDF。您还可以为转换后的 PDF 文件添加安全性。要了解有关保护文件的信息，请跳到 [PHP 文件被转换][11] 的下方。



{{< figure align=center src="images/java-to-pdf-programmatically.jpg" alt="使用 C# 将 Java 源文件转换为 PDF">}}


## 使用 C# 将 Python 代码转换为 PDF {#python-to-pdf}

如果更改了源文件格式，为什么要更改代码？让 API 承受这种痛苦。只需将 .py 文件提供给正确的方法。以下步骤展示了如何使用 C# 将 Python 代码转换为 PDF。

* 使用 [Viewer][12] 类加载 Python 源文件。
* 使用 [PdfViewOptions][13] 类定义输出文件路径和配置。
* 使用正确的 [View()][14] 方法将 .py 文件转换为 PDF。

以下 C# 代码示例将 Python 源代码文件转换为 PDF 格式。

```
/*
 * Convert Python source file into PDF using C#
 */
 using (Viewer viewer = new Viewer("path/source.py"))
{
   PdfViewOptions viewOptions = new PdfViewOptions("path/python-source.pdf");
   viewer.View(viewOptions);
}
```

## 使用 C# 将 PHP 转换为 PDF {#php-to-pdf}

同样，您也可以转换 PHP 文件。此外，在转换源代码文件时，您可以为 PDF 文件添加安全性。让我们在转换代码时保护它。以下步骤显示了在 C# 中将 PHP 文件转换为具有安全性的 PDF 格式。

* 使用 [Viewer][15] 类加载 PHP 文件。
* 使用 [Security][16] 类定义 PDF 文件的预期安全性。
* 设置打开和编辑生成文件的密码。
* 使用 [PdfViewOptions][17] 类定义输出文件。
* 调用 [View()][18] 方法将加载的 PHP 文件渲染为受保护的 PDF。

以下 C# 代码片段将 PHP 源代码文件转换为受密码保护的 PDF 文件。

```
/*
 * Convert Php source file into PDF using C#
 */
 using (Viewer viewer = new Viewer("path/source.php"))
{
    Security security = new Security();
    security.DocumentOpenPassword = "OpEnD0c";
    security.PermissionsPassword = "Ple@se";
    security.Permissions = Permissions.AllowAll ^ Permissions.DenyPrinting;
    
    PdfViewOptions viewOptions = new PdfViewOptions("path/php-source.pdf");
    viewOptions.Security = security;
                    
    viewer.View(viewOptions);
}
```

同样，您可以将此代码用于其他 [支持的编程语言][19] 的源代码文件，例如 C#、C/C++、JS、Ruby 等。

## 获取免费 API 许可证

您可以[获得免费的临时许可证][20] 使用 API 而不受评估限制。

## 结论

综上所述，我们学会了使用C#将各种编程语言的源代码文件转换为PDF格式。这些示例显示了将 Java、Python 和 PHP 文件转换为 PDF 格式。此外，我们学会了保护生成的 PDF 文件。使用此 API，您可以开始构建自己的源代码查看器 .NET 应用程序。

从 [文档][21] 中了解有关 **GroupDocs.Viewer** 的更多信息，以构建您自己的源代码查看器应用程序。如有疑问，请通过 [论坛][22] 联系我们。

## 也可以看看

* [C#中图像到PDF的转换][23]
* [用 C# 将文件通过电子邮件发送到 PDF 转换][24]
* [使用 C# 将 Excel 电子表格转换为 PDF][25]
* [使用 C# 将 Word 文档作为 HTML 响应页面查看][26]


[1]: #source-code-converter-dotnet-api
[2]: #java-to-pdf
[3]: #python-to-pdf
[4]: #php-to-pdf
[5]: https://products.groupdocs.com/viewer/net/
[6]: https://downloads.groupdocs.com/viewer/net
[7]: https://www.nuget.org/packages/groupdocs.viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[11]: #php-to-pdf
[12]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/security
[17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[19]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[20]: https://purchase.groupdocs.com/temporary-license
[21]: https://docs.groupdocs.com/viewer
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[24]: https://blog.groupdocs.com/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
[25]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[26]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/


