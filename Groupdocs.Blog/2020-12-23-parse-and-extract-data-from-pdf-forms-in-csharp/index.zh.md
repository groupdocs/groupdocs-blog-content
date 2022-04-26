---
title: "使用 C# 读取 PDF 表单字段"
date: Wed, 23 Dec 2020 12:39:01 +0000
draft: false
url: /zh/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/
author: 'Shoaib Khan'
summary: "在本文中，我们将学习**如何读取和解析 PDF 文档，然后在 C# 中以编程方式提取 PDF 表单字段值**。早些时候，我们已经看到[如何在 Java 中从 PDF 表单中提取值][1]。阅读这些文章后，如果您填写了反馈表，您可以提取 .NET 和 Java 应用程序中的值进行分析或将它们保存在数据库中。"
tags: ['Extract Text from PDF Forms in CSharp', 'Parse PDF Forms in CSharp', 'Read PDF Form Fields in CSharp']
categories: ['GroupDocs.Parser Product Family']
---

在本文中，我们将学习**如何读取和解析 PDF 文档，然后在 C# 中以编程方式提取 PDF 表单字段值**。早些时候，我们已经看到[如何在 Java 中从 PDF 表单中提取值][2]。阅读这些文章后，如果您填写了反馈表，您可以提取 .NET 和 Java 应用程序中的值进行分析或将它们保存在数据库中。



{{< figure align=center src="images/Extract-from-PDF-Form-in-csharp.jpeg" alt="解析 PDF 表单以提取 C# 中的值">}}


## .NET API 从 PDF 表单中解析和提取值

[GroupDocs.Parser for .NET][3] 是一个易于使用且功能强大的 .NET 应用程序解析和数据提取 API。它支持从文字处理和 PDF 文档、电子表格、演示文稿、电子邮件、标记、电子书、档案等中提取文本、元数据和图像。其中一个重要的功能也将在下面显示，它是解析可填写的 PDF 表单以使用一小段 C# 代码提取表单字段值。

要测试下面提到的 API 示例和其他示例，您可以从 [NuGet][4] 下载并安装 API，或直接从 GroupDocs 下载中[下载][5]。

```
PM> Install-Package GroupDocs.Parser
```

## 使用 C# 从 PDF 表单字段中提取数据

以下简单步骤介绍了如何解析 PDF，然后在 C# 中提取 PDF 表单字段值。

* 使用 [Parser][6] 类加载 PDF 文件。
* 使用 [ParseForm][7] 方法解析 PDF 表单。
* 遍历解析后的集合，提取表单字段值。

以下 C# 代码示例显示了在 .NET 应用程序中提取已填充 PDF 表单的字段值。

```
// 解析填充的 PDF 表单以提取 C# 中的字段值
using (Parser parser = new Parser("filePath/PDFForm.pdf"))
{
    // Extract data from PDF Form
    DocumentData data = parser.ParseForm();
    // Iterate over the extracted PDF Form fields data
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

```
COMPANY: GroupDocs
EMAIL: everything@groupdocs.com
COUNTRY: Australia
```

## 结论

我相信，您现在可以轻松地开发自己的基于 .NET 的应用程序，该应用程序可以解析 PDF 文件并快速准确地从可填写的 PDF 表单字段中获取值。要添加更多功能，您可以从 [文档][8] 文章和 [GitHub][9] 上的 C# 示例中了解有关 API 的更多信息。

如需查询和快速回复，请在 [论坛][10] 上联系。

## 也可以看看

* [使用 Java 读取 PDF 表单域][11]
* [从C#文档中提取图像][12]







[1]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
[2]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
[3]: https://products.groupdocs.com/parser/net
[4]: https://www.nuget.org/packages/groupdocs.parser
[5]: https://downloads.groupdocs.com/parser/net
[6]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[7]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/parseform
[8]: https://docs.groupdocs.com/parser/net/
[9]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET
[10]: https://forum.groupdocs.com/c/parser
[11]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
[12]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/


