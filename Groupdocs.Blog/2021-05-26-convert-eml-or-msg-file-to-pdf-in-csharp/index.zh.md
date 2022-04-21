---
title: "在 C# 中将 EML 或 MSG 文件转换为 PDF"
date: Wed, 26 May 2021 12:50:00 +0000
draft: false
url: /zh/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
aliases:
- /2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "For sharing and referencing the email content, you may need to convert your email message to PDF format. In this article, you will learn the **conversion of email message files like EML and MSG into PDF using C#**. In one of the other blog posts, we have already discussed the [conversion of emails to PDF using Java][1]. This will help to automate the email conversions within your desktop or web-based applications."
tags: ['document conversion', 'email to pdf', 'eml to pdf in csharp', 'msg to pdf in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

要共享和引用电子邮件内容，您可能需要将电子邮件信息转换为 PDF 格式。在本文中，您将学习**使用 C# 将 EML 和 MSG 等电子邮件文件转换为 PDF **。在其他一篇博文中，我们已经讨论了[使用 Java 将电子邮件转换为 PDF][3]。这将有助于在您的桌面或基于 Web 的应用程序中自动执行电子邮件转换。



{{< figure align=center src="images/convert-emails-to-pdf-in-dotnet.jpg" alt="在 C# 中将电子邮件消息转换为 PDF">}}


以下主题涵盖以下内容：

* [.NET 的电子邮件转换库][4]
* [味精转PDF][5]
* [将 EML 转换为 PDF][6]

## 用于电子邮件转换的 .NET API {#dotnet-email-conversion-library}

GroupDocs.Conversion for .NET 是允许将电子邮件消息转换为其他格式的 API。在本文中，我们将使用该 API 使用 C# 将 MSG 和 EML 消息转换为 PDF 格式。此外，API 允许在您的 .NET 应用程序中来回转换文字处理文档、电子表格、演示文稿、电子书、图像和许多其他文件格式。

您可以从 [下载部分][7] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 MSG 转换为 PDF {#msg-to-pdf-in-csharp}

以下是将 Outlook MSG 文件转换为 PDF 格式的步骤。

1. 使用 [Converter][9] 类加载 MSG 文件。
2. 使用 [PdfConvertOptions][10] 类创建 PDF 转换选项。
3. 调用 [Convert][11] 方法将 MSG 文件转换为 PDF 格式。

以下源代码使用 C# 将 MSG 文件转换为 PDF。

```
// 在 C# 中将 MSG 消息转换为 PDF
using (Converter converter = new Converter("emailMessage.msg"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("msg-Message.pdf", options);
}
```

下面显示的是 Microsoft Outlook MSG 文件。此外，此处还显示了使用上述代码从 MSG 文件转换后获得的 PDF 文件。



{{< figure align=center src="images/MSG-message.png" alt="要转换为 PDF 的 MSG 文件" caption="味精文件">}}




{{< figure align=center src="images/converted-msg-to-pdf-in-java.png" alt="从 MSG 转换的 PDF 文件" caption="使用上述 C# 代码从 MSG 格式转换的 PDF 文件。">}}


## 使用 C# 将 EML 转换为 PDF {#eml-to-pdf-in-csharp}

如果您想将以 EML 格式存储的电子邮件消息转换为 PDF 格式，可以使用类似的代码行有效地完成。以下是将 EML 文件转换为 PDF 的步骤。

1. 使用 [Converter][12] 类加载 EML 消息文件。
2. 使用 [PdfConvertOptions][13] 类，为 PDF 文件创建转换选项。
3. 调用 [Convert][14] 方法将 EML 文件转换为 PDF 格式。将生成的 PDF 文件的路径和转换选项作为参数传递。

```
// 在 C# 中将 EML 消息转换为 PDF
using (Converter converter = new Converter("emailMessage.eml"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("eml-Message.pdf", options);
}
```

下面是使用上述代码转换的 EML 文件和转换后的 PDF 文件截图。



{{< figure align=center src="images/EML-message.png" alt="要转换为 PDF 的 EML 文件" caption="EML 文件">}}




{{< figure align=center src="images/converted-eml-to-pdf-in-java.png" alt="从 EML 转换的 PDF 文件" caption="使用 C# 从 EML 格式转换的 PDF 文件。">}}


此外，您可以根据需要更改输出 PDF 文件的外观。您可以访问 [documentation][15] 用于此类目的和更多功能。

## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][16] 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们学习了如何使用 .NET Conversion API 将 EML 和 MSG 文件转换为 PDF。此外，我们可以以编程方式对 PDF 文件应用自定义，以获得所需样式的结果。

您可以使用 [documentation][17] 了解有关 .NET 的 GroupDocs.Conversion 的更多信息。 [GitHub][18] 上提供了更多示例。如有疑问，请通过 [论坛][19] 联系我们。

## 也可以看看

* [用 C# 将 Excel 电子表格转换为 PDF][20]
* [用 C# 将图像转换为 PDF][21]
* [C# 中的 PDF 演示文稿][22]
* [](https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/)[用 Java 将电子邮件转为 PDF][23]







[1]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
[3]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
[4]: #dotnet-email-conversion-library
[5]: #msg-to-pdf-in-csharp
[6]: #eml-to-pdf-in-csharp
[7]: https://downloads.groupdocs.com/conversion
[8]: https://www.nuget.org/packages/groupdocs.conversion
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[15]: https://docs.groupdocs.com/conversion/
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/conversion/
[18]: https://github.com/groupdocs-conversion
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[21]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[22]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[23]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/


