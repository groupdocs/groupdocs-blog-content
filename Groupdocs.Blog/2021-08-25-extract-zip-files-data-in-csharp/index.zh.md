---
title: "在 C# 中提取 ZIP 文件数据"
date: Wed, 25 Aug 2021 12:43:51 +0000
draft: false
url: /zh/2021/08/25/extract-zip-files-data-in-csharp/
author: 'Shoaib Khan'
summary: "**ZIP、RAR、TAR、GZIP、BZIP2** 等档案通常用于在单个容器中存储多个文件和文件夹。归档文件的另一个主要原因是使用压缩算法减小文件总大小。就像从各种文件格式的文档中解析和提取数据一样，您可以以相同的方式处理归档文件。您可以从存档中压缩的文件中提取文本、图像甚至元数据。在本文中，我们将讨论**如何在您的 .NET 应用程序中使用 C#** 提取 ZIP 存档数据。"
tags: ['Extract Archives in CSharp', 'Extract from ZIP in C#', 'unzip data in C#']
categories: ['GroupDocs.Parser Product Family']
---

**ZIP、RAR、TAR、GZIP、BZIP2** 等档案通常用于在单个容器中存储多个文件和文件夹。归档文件的另一个主要原因是使用压缩算法来减小总文件大小。就像从各种文件格式的文档中解析和提取数据一样，您可以以相同的方式处理归档文件。您可以从存档中压缩的文件中提取文本、图像甚至元数据。在本文中，我们将讨论**如何在您的 .NET 应用程序中使用 C#** 提取 ZIP 存档数据。

以下主题涵盖以下内容：

* [.NET API 用于 ZIP 文件数据提取][1]
* [如何提取ZIP文件数据][2]

## .NET API 提取 ZIP 文件数据 {#dotnet-zip-files-extraction-api}

[GroupDocs.Parser][3] 为开发者提供文档解析解决方案。我将在本文的 C# 示例中使用其 [.NET API 来提取 ZIP 文件数据][4]。该 API 还允许从一长串 [支持的文档格式][5] 中提取文本、图像和元数据，例如文字处理文档、演示文稿、电子表格、电子邮件、数据库、电子书等。

您可以从 [下载部分][6] 下载 **DLLs** 或 **MSI** 安装程序，或者通过 [NuGet][7] 将其包添加到您的 .NET 应用程序来安装 API。

```
PM> Install-Package GroupDocs.Parser
```

## 如何在 C# 中提取 ZIP 文件数据 {#how-to-extract-zip-data}

[GroupDocs.Parser for .NET][8] 支持从各种压缩文件格式（如 ZIP、RAR、TAR、BZIP2 和 GZIP）中提取数据。从压缩文件中检索文件集合后，您可以进一步从每个文件中提取任何类型的数据。

以下步骤显示了如何提取 ZIP 文件数据并从 C# 中的每个包含的文件中检索文本。

* 使用 **[Parser][9]** 类加载 ZIP 存档。
* 使用**_[GetContainer][10]_**方法获取附件
* 遍历附件集合。
* 对于每个附件，您可以使用 **Parser** 类的相应方法获取其不同类型的数据。

源代码显示了如何使用 C# 提取 ZIP 文件数据。在此示例中，我将从 ZIP 存档中的所有文件中提取整个文本。

```
// 在 C# 中提取 ZIP 存档数据
using (Parser parser = new Parser(@"path/sample.zip"))
{
    // Extract attachments from the container
    IEnumerable<ContainerItem> attachments = parser.GetContainer();

    // Iterate over collection of entities
    foreach (ContainerItem item in attachments)
    {
        // Print the FILE INFO
        Console.WriteLine("-----------------------------------");
        Console.WriteLine("Name: " + item.Name);
        Console.WriteLine("File Size: " + item.Size + " Bytes");
        Console.WriteLine("-----------------------------------");

        try
        {
            using (Parser attachmentParser = item.OpenParser())
            {
                // Extract the ZIP entity text
                using (TextReader reader = attachmentParser.GetText())
                {
                    Console.WriteLine(reader == null ? "No text" : reader.ReadToEnd());
                }
            }
        }
        catch (UnsupportedDocumentFormatException)
        {
            Console.WriteLine("Isn't supported.");
        }
    }
}
```

上述源代码的输出显示了从 ZIP 文件中的 PDF 文件之一检索到的文本。

```
 -----------------------------------
 Name: sample.pdf
 File Size: 33370 Bytes
 -----------------------------------

 Heading

 This is the first paragraph of the sample document that contains some sample
 text, bulleted list, numbered list and more.

    •  Bullet Item 1
    •  Bullet Item 2
    •  Bullet Item 3
 
 This is the second paragraph of the sample document and after this, there is a
 numbered list: 

    1. Numbered Item 1
    2. Numbered Item 2
    3. Numbered Item 3 
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][11] 以便在没有评估限制的情况下使用 API。

## 结论

总之，您学习了如何在 .NET 应用程序中使用 C# 提取 ZIP 存档数据。更具体地说，您现在可以从 ZIP、RAR、TAR、GZIP 和 BZIP 文件中提取数据。您甚至可以为压缩文件构建自己的数据提取 .NET 应用程序。有关 API 的更多详细信息或了解，请访问 [文档][12]。如有疑问，请通过 [论坛][13] 联系我们。

## 也可以看看

* [使用 C# 从文档中提取图像][14]
* [用 C# 从 EPUB、FB2、CHM 电子书中提取图像][15]
* [使用 C# 读取 PDF 表单域][16]







[1]: #dotnet-zip-files-extraction-api
[2]: #how-to-extract-zip-data
[3]: https://products.groupdocs.com/parser/
[4]: https://products.groupdocs.com/parser/net/
[5]: https://docs.groupdocs.com/parser/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/parser
[7]: https://www.nuget.org/packages/groupdocs.parser
[8]: https://products.groupdocs.com/parser/net/
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[10]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getcontainer
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/parser/
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[15]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[16]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/


