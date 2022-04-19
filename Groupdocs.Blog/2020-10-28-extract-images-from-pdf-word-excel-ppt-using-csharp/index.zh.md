---
title: "使用 C# 从文档中提取图像"
date: Wed, 28 Oct 2020 18:27:00 +0000
draft: false
url: /zh/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
author: 'Shoaib Khan'
summary: "在本文中，我们将学习**使用文档解析 .NET API 在 C#** 应用程序中以编程方式从 PDF、Excel、PowerPoint 和 Word 文档中提取图像。 [GroupDocs.Parser for .NET][1] 是文档解析和数据提取的 .NET API。它支持**文档解析**和**从**文字处理文档**、**电子表格**、**演示文稿、档案**和**提取图像、文本**和**元数据** **电子邮件**文件。"
tags: ['csharp parser', 'Dcoument Parsing API', 'extract images from PDF in csharp', 'extract images in csharp', 'Image extractor']
categories: ['GroupDocs.Parser Product Family']
---

在 [previous post][2] 中，我们讨论了如何从 Java 文档中提取图像。今天，我们将寻求使用 C# 实现相同的目标。如果您还没有访问过最后一篇文章，请不要担心。在本文中，我们将学习**使用文档解析 .NET API 在 C#** 应用程序中以编程方式从 PDF、Excel、PowerPoint 和 Word 文档中提取图像。



{{< figure align=center src="images/extract-images-from-documents-in-csharp-dotnet.png" alt="从 .NET 中的文档中提取图像">}}


此处将涵盖以下主题：

* [图像、文本和元数据提取 .NET API][3]
* [从PDF文档中提取图像][4]
* [从 Word、Excel、PowerPoint 文档中提取图像][5]
* [从特定页面提取图像][6]
* [支持的图像提取格式][7]

## 图像、文本和元数据提取 .NET API {#image-extraction-dotnet-api}



{{< figure align=center src="images/groupdocs-parser-net.png" alt="在 .NET 中解析文档和提取数据">}}


[GroupDocs.Parser for .NET][8] 是文档解析和数据提取的 .NET API。它支持**文档解析**和**从**文字处理文档**、**电子表格**、**演示文稿、档案**和**提取图像、文本**和**元数据** **电子邮件**文件。在文章的最后，[提到][9] API 支持的用于图像提取的文档格式。

在本文中，我们将使用此 API，因此我建议[下载][10] 其二进制文件或从 [NuGet][11] 安装 API 以准备环境。

## 在 C# 中从 PDF 文档中提取图像 {#extract-images-from-pdf-in-csharp}



{{< figure align=center src="images/PDF-with-Images.png" alt="提取图像的 PDF 文档">}}


按照这些简单的步骤，您可以轻松地从任何 PDF 文档中检索所有图像。

1. 使用源文档实例化 [Parser][12] 类对象。
2. 调用 **Parser** 类的 [GetImages][13] 方法获取 [PageImageArea][14] 对象中所有图像的集合。
3. 遍历 **PageImageArea** 以获取每个图像。
4. 使用 **PageImageArea** 的 [Save][15] 方法将图像保存在磁盘上。

提取的图像可以保存为 **BMP**、**GIF**、**JPEG**、**PNG** 和 **WebP** 格式。下面显示了完整的代码来演示整个步骤。

```
// 使用 GroupDocs.Parser for .NET 从 C# 中的 Word、Excel、PPT、PDF 中提取图像
using (Parser parser = new Parser("path/document.pdf"))
{
    IEnumerable<PageImageArea> images = parser.GetImages();
    ImageOptions options = new ImageOptions(ImageFormat.Png);
    int imageNumber = 0;
    // Iterate over retrieved images
    foreach (PageImageArea image in images)
    {
        // Save Image and print page index, rectangle and image type:
        Console.WriteLine(string.Format("Page: {0}, R: {1}, Type: {2}", image.Page.Index, image.Rectangle, image.FileType));
        image.Save("imageFilePath/image-" + imageNumber.ToString() + ".png", options);
        imageNumber++;
    }
}
```



{{< figure align=center src="images/Extracted-Images-from-PDF-using-GroupDocs.Parser-for-Java.png" alt="使用 GroupDocs.Parser 从文档中提取图像">}}


## 在 C# 中从 Word、Excel、PowerPoint 文件中提取图像 {#extract-images-from-word-excel-ppt-in-csharp}

不仅限于 PDF 格式，我们可以从文字处理文档、电子表格、演示文稿中取出所有图像，并使用未更改的代码库。只需使用文件扩展名更改源文档路径，您的文档将被解析以提取所有图像并将其保存到磁盘。

```
using (Parser parser = new Parser("path/document.docx")) // Word Document
// using (Parser parser = new Parser("path/document.xlsx")) // Excel Spreadhseet
// using (Parser parser = new Parser("path/document.pptx")) // Presentation
// using (Parser parser = new Parser("path/document.pdf")) // PDF Document
```

## 从 C# 中的特定文档页面提取图像 {#extract-images-from-specific-page-in-csharp}

如果要从文档的特定页面中提取图像，可以使用下面提到的步骤和 C# 代码轻松完成。

* 使用[GetDocumentInfo][16]方法获取文档信息。
* 从文档信息中取出总[PageCount][17]等信息。
* 使用 [GetImages(pageIndex)][18] 方法并将您的目标页面索引传递给它。
* 要保存检索到的图像，遍历图像集合，并使用 [Save][19] 方法保存单个图像。

```
// 使用 GroupDocs.Parser for .NET 从 C# 中的 Word、Excel、PowerPoint、PDF 的特定页面中提取图像
using (Parser parser = new Parser("path/document.pdf"))
{
    // Get the document info
    IDocumentInfo documentInfo = parser.GetDocumentInfo();
    ImageOptions options = new ImageOptions(ImageFormat.Png);
    int imageNumber = 0;

    // Iterate over pages
    for (int pageIndex = 0; pageIndex < documentInfo.PageCount; pageIndex++)
    {
        // Print a page number 
        Console.WriteLine(string.Format("Page {0}/{1}", pageIndex + 1, documentInfo.PageCount));
        // Iterate over images. Ignoring null-check in the example
        foreach (PageImageArea image in parser.GetImages(pageIndex))
        {
            // Print a rectangle and image type
            Console.WriteLine(string.Format("R: {0}, Text: {1}", image.Rectangle, image.FileType));
            image.Save("imageFilePath/image-" + imageNumber.ToString() + ".png", options);
            imageNumber++;
        }
    }
}
```

## C# 中支持的图像提取格式 {#supported-formats-for-image-extraction}

以下是 _GroupDocs.Parser for .NET_ API 支持的用于图像提取的文档格式。

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**文字处理文件</td><td>DOC、DOCX、DOCM、DOT、DOTX、DOTM、ODT、OTT、RTF</td></tr><tr><td><strong>电子表格</strong></td><td>XLS、XLSX、XLSM、XLSB、XLT、XLTX、XLTM、ODS、OTS、XLA、XLAM、数字</td></tr><tr><td><strong>演示文稿</strong></td><td>PPT、PPTX、PPTM、PPS、PPSX、PPSM、POT、POTX、POTM、ODP、OTP</td></tr><tr><td><strong>便携式文件</strong></td><td>PDF格式</td></tr><tr><td><strong>电子邮件</strong></td><td>EML、EMLX、味精</td></tr><tr><td><strong>档案**</strong></td><td>压缩</td></tr></tbody></table></figure>

## 更多关于 GroupDocs.Parser

* [文档][20]
* [源代码示例][21]
* [API 参考][22]
* 系列（[本地 API][23]|[云 API][24]|[免费在线应用程序][25]

让我们多聊聊@[免费支持论坛][26]

## 相关文章

* [使用Java从文档中提取图像][27]
* [使用Python从云端文档中提取图像][28]







[1]: https://products.groupdocs.com/parser/net
[2]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[3]: #image-extraction-dotnet-api
[4]: #extract-images-from-pdf-in-csharp
[5]: #extract-images-from-word-excel-ppt-in-csharp
[6]: #extract-images-from-specific-page-in-csharp
[7]: #supported-formats-for-image-extraction
[8]: https://products.groupdocs.com/parser/net
[9]: #supported-formats-for-image-extraction
[10]: https://downloads.groupdocs.com/parser/net
[11]: https://www.nuget.org/packages/GroupDocs.Parser/
[12]: https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser
[13]: https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser/methods/getimages
[14]: https://apireference.groupdocs.com/net/parser/groupdocs.parser.data/pageimagearea
[15]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data.pageimagearea/save/methods/1
[16]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getdocumentinfo
[17]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.options/idocumentinfo/properties/pagecount
[18]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.parser/getimages/methods/2
[19]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data.pageimagearea/save/methods/1
[20]: https://docs.groupdocs.com/parser/
[21]: https://github.com/groupdocs-parser/
[22]: https://apireference.groupdocs.com/parser
[23]: https://products.groupdocs.com/parser/family
[24]: https://products.groupdocs.cloud/parser/family
[25]: https://products.groupdocs.app/parser)
[26]: https://forum.groupdocs.com/c/parser
[27]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[28]: https://blog.groupdocs.cloud/2020/10/25/extract-images-from-word-excel-ppt-pdf-using-python/


