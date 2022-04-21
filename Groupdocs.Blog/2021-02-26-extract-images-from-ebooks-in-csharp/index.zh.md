---
title: "在 C# 中从 EPUB、FB2、CHM 电子书中提取图像"
date: Fri, 26 Feb 2021 07:26:57 +0000
draft: false
url: /zh/2021/02/26/extract-images-from-ebooks-in-csharp/
author: 'Shoaib Khan'
summary: "An electronic book, popularly known as **eBook**, is a book in digital form that is readable on various electronic devices. These devices include dedicated eReaders like Kindle, or laptops, desktop computers, and smartphones. There are many popular file formats of eBooks in-use in the market that include; **EPUB**, FictionBook **FB2**, Microsoft Compiled HTML Help - **CHM**, **DjVu**, **MOBI**, **PDF**, and many others. As a programmer, this article will help you to **programmatically extract images from eBooks in C#** within .NET applications."
tags: ['Extract Images from CHM in CSharp', 'Extract Images from eBooks in CSharp', 'Extract Images from EPUB in CSharp', 'Extract Images from FB2 in CSharp', 'Parse eBooks in CSharp', 'Parse eBooks to Extract Images in CSharp']
categories: ['GroupDocs.Parser Product Family']
---

电子书，俗称**eBook**，是一种数字形式的书，可在各种电子设备上阅读。这些设备包括专用电子阅读器，如 [Kindle][2]，或笔记本电脑、台式电脑和智能手机。市场上有许多流行的电子书文件格式，包括： **EPUB**、FictionBook **FB2**、Microsoft 编译的 HTML 帮助 - **CHM**、**DjVu**、**MOBI**、**PDF** 等等。作为一名程序员，本文将帮助您在 .NET 应用程序中**以 C# 语言从电子书中以编程方式提取图像**。

下面将介绍以下主题：

* [用于从电子书中提取图像的 .NET API][3]
* [用 C# 从 EPUB 电子书中提取图像][4]
* [在 C# 中从 FB2、CHM 电子书中提取图像][5]

## 用于从电子书中提取图像的 .NET API {#image-extraction-dotnet-api-for-ebooks}

对于从电子书中提取图像，我将在本文的 C# 示例中使用 [GroupDocs.Parser for .NET][6] API。与电子书一起，此 API 支持从文字处理文档、电子表格、PDF、演示文稿、电子邮件、ZIP 档案和许多其他文档格式中解析和提取图像。

您可以从 [下载部分][7] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][8] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Parser
```

## 在 C# 中从 EPUB 电子书中提取图像 {#extract-images-from-epub-in-csharp}

让我们从 EPUB 电子书开始解析它的图像。 C# 代码后面的步骤解析 EPUB 电子书并提取其中的所有图像。

* 创建 [Parser][9] 类对象。
* 使用 [GetImages][10] 方法提取 EPUB 电子书的所有图像。
* 将提取的图像一张一张地遍历到[save][11]这些。



{{< figure align=center src="images/alice.png" alt="爱丽丝 EPUB" caption="Adobe 的 EPUB 电子书 [示例电子书库][12]">}}


下面的 C# 代码实现了上面提到的解析步骤，以解析到上面显示的 EPUB 电子书，并将提取的图像一一保存到磁盘。

```
// 解析电子书以从 EPUB、FB2、CHM 文件中提取图像并用 C# 保存到磁盘
using (Parser parser = new Parser("ebook.epub"))
{
    // Extract images from the eBook
    IEnumerable<PageImageArea> images = parser.GetImages();
    ImageOptions options = new ImageOptions(ImageFormat.Jpeg);
    int imageNumber = 0;
    // Iterate over extracted images
    foreach (PageImageArea image in images)
    {
        image.Save(("Image-" + imageNumber.ToString() + image.FileType.Extension), options);
        imageNumber++;
    }
}
```



{{< figure align=center src="images/alice-image-from-epub.jpg" alt="在 C# 中从 EPUB 中提取图像">}}


结果，所有可用的图像都将被保存。这是作为示例显示的图像之一。

您可以将提取的图像保存为以下任何受支持的图像文件格式：

* JPG
* PNG
* WEBP
* 动图
* BMP

## 从 C# 中的 FB2、CHM 电子书中提取图像 {#extract-images-from-fb2-chm-in-csharp}

如果您有 FB2、CHM 或其他格式的电子书，您可以以相同的方式提取其图像。您只需在创建对象时将您的电子书传递给 **Parser** 构造函数。然后 **GetImages** 方法将使用相同的 C# 代码从任何提供的电子书中提取图像。

```
// Pass the FB2, CHM, PDF, or any other eBook to Parser contructor
Parser parser = new Parser("ebook.fb2"); // FB2
// Parser parser = new Parser("ebook.chm"); // CHM
// Parser parser = new Parser("ebook.pdf"); // PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```

## 结论

我希望您现在能够在您的 .NET 应用程序中以编程方式从具有 EPUB、FB2、CHM 和其他文件格式的电子书中获取所有图像。您甚至可以使用 [GroupDocs.Parser for .NET][13] API 构建自己的图像提取器应用程序。

有关 API 的更多信息，您可以访问 [文档][14] 或 GitHub 上的开源示例。对于任何其他问题，您可以在 [论坛][15] 上联系快速支持。

## 也可以看看

* [从 Word、Excel 中提取图像。 PPT文件使用C#][16]
* [使用 C# 从 PDF 文档中提取图像][17]
* [使用Java从文档中提取图像][18]







[1]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[2]: https://en.wikipedia.org/wiki/Amazon_Kindle
[3]: #image-extraction-dotnet-api-for-ebooks
[4]: #extract-images-from-epub-in-csharp
[5]: #extract-images-from-fb2-chm-in-csharp
[6]: https://products.groupdocs.com/parser/net
[7]: https://downloads.groupdocs.com/parser/net
[8]: https://www.nuget.org/packages/groupdocs.parser
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[10]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getimages/index
[11]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data/pageimagearea/methods/save/index
[12]: https://www.adobe.com/solutions/ebook/digital-editions/sample-ebook-library.html
[13]: https://products.groupdocs.com/parser/net
[14]: https://docs.groupdocs.com/parser/net/
[15]: https://forum.groupdocs.com/c/parser/
[16]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[17]: https://blog.groupdocs.com/2019/10/04/extract-images-from-pdf-files-in-csharp/
[18]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/


