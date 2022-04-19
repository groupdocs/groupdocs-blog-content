---
title: "在 C# 中将 CAD 绘图转换为 PDF"
date: Sun, 08 Nov 2020 04:03:43 +0000
draft: false
url: /zh/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "今天，我们将学习如何在 C# 中以编程方式将 CAD 图纸转换为 PDF 格式。以前，在 [早期文章][1] 中，我们做了同样的事情，但使用的是 Java。我们希望通过代码示例将 DWG、DGN 和 DWF 文件转换为 PDF 文档。让我们使用 .NET 的文档转换 API 在 C# 中完成。"
tags: ['convert cad to pdf', 'convert cad to pdf in csharp', 'convert dgn to pdf in csharp', 'convert dwf to pdf in csharp', 'convert dwg to pdf in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

今天，我们将学习如何在 C# 中以编程方式将 CAD 图纸转换为 PDF 格式。以前，在 [较早的帖子][2] 中，我们做了同样的事情，但使用的是 Java。我们希望通过代码示例将 DWG、DGN 和 DWF 文件转换为 PDF 文档。让我们在 C# 中使用 .NET 的文档转换 API 来完成。



{{< figure align=center src="images/convert-cad-drawings-to-pdf-using-dotnet.png" alt="在 .NET 中将 CAD 绘图转换为 PDF">}}


本文将介绍以下主题：

* [C# API 转换 CAD 图纸][3]
* [在 C# 中将 CAD 绘图（DWG、DWF、DGN）转换为 PDF][4]

## 用于转换 CAD 绘图的 C# API {#cad-conversion-dotnet-lib}



{{< figure align=center src="images/groupdocs-conversion-net.png" alt="使用 .NET 转换文档和图像">}}


[GroupDocs.Conversion for .NET][5] 是任何 .NET 应用程序中文档和图像的高级转换 API。它支持多种文件格式，包括文字处理文档、电子表格、演示文稿、图像、CAD 图纸等等。

本文将使用 GroupDocs.Conversion for .NET API **将 CAD 图纸转换为 C# 中的 PDF**。您可以 [下载][6] DLL 或使用 [NuGet][7] 安装它。

```
PM> Install-Package GroupDocs.Conversion
```

## 在 C# 中将 CAD 绘图（DWG、DWF、DGN）转换为 PDF {#convert-cad-dwg-dwf-dgn-to-pdf-in-java}

以下步骤将允许将具有许多选项的 CAD 图纸轻松转换为个性化的 PDF 文件。

* **加载** CAD图纸。
* 指定**布局**和**选项**。
* **转换** CAD 与 PDF 选项。

### 加载 CAD 图纸

使用 [CadLoadOptions][8] 类加载 CAD 文件。

```
CadLoadOptions loadOptions =  new CadLoadOptions();
```

### 指定布局和其他选项

您可以在加载 CAD 文件时指定某些 [属性][9]。这些属性包括**布局名称**、**宽度**、**高度**和**格式**。指定布局名称将允许您仅转换提到的布局。

```
Contracts.Func<LoadOptions> getLoadOptions = () => new CadLoadOptions
{
    LayoutNames = new \[\]{ "Layout1", "Layout3" },
    Width = 1920,
    Height = 1080
};
```

### 在 C# 中将 CAD 绘图 - DWG、DWF 转换为 PDF

现在使用 Converter 类的 Convert 方法，可以使用设置选项轻松地将 DWG 或 DWF 文件转换为 PDF 格式。

```
using (Converter converter = new Converter("with\_layers\_and\_layouts.dwf", getLoadOptions))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("converted.pdf", options);
}
```

### 完整代码

这是完整的 C# 代码，您可以使用该代码将 DWG 或 DWF 文件转换为 PDF，方法是使用 **Load** -> Specify **Layout and Options** -> **Convert**。

```
// 使用 GroupDocs.Conversion for .NET 将 CAD 绘图 - DWF 转换为 C# 中的 PDF
// 加载选项
Contracts.Func<LoadOptions> getLoadOptions = () => new CadLoadOptions
{
  LayoutNames = new []{ "Layout1", "Layout3" }, // Specifying Layouts
  // Width = 1920,
  // Height = 1080
};
using (Converter converter = new Converter("filePath/CAD-Drawing.dwf", getLoadOptions))
{
  PdfConvertOptions options = new PdfConvertOptions();
  converter.Convert("filePath/cadToPDF-NET.pdf", options);
}
```

生成的 PDF 格式还有许多其他自定义选项，可以在将任何文档转换为 PDF 格式时控制输出结果。您可以在以下文档文章中查看这些高级选项。

[使用 .NET 中的高级选项转换为 PDF][10]

稍作改动，我们就可以相应地转换其他 CAD 文件，如 DGN 和 DWG 文件。我们只需要在上面的代码中提供正确的文件名及其格式。对于不支持布局的文件格式，我们不会设置**LayoutNames**。对于如此小的修改，您可以访问[文档][11]。

## 结论

我希望您现在对使用 .NET 和 Java 应用程序中的 GroupDocs.Conversion 将 DWG、DGN 和 DWF 等 CAD 文件转换为 C# 中的 PDF 充满信心。您现在可以使用任何平台构建您自己的转换应用程序，就像@www.groupdocs.app 提供的[免费应用程序][12]。

如果有任何进一步的疑问，您可以联系**免费支持团队**，该团队随时可以在 [论坛][13] 上为您提供帮助。

## 相关文章

* [在 Java 中将 CAD 图纸转换为 PDF][14]
* [使用 C# 将 Excel 电子表格转换为 PDF][15]
* [加载 CAD 文档][16]
* [将文档和图像转换为 PDF][17]







[1]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[3]: #cad-conversion-java-lib
[4]: #convert-cad-dwg-dwf-dgn-to-pdf-in-java
[5]: https://products.groupdocs.com/conversion/net
[6]: https://downloads.groupdocs.com/conversion/net
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/cadloadoptions/properties/index
[10]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[11]: https://docs.groupdocs.com/conversion/net/
[12]: https://products.groupdocs.app/conversion/total
[13]: https://forum.groupdocs.com/c/conversion
[14]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[15]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[16]: https://docs.groupdocs.com/conversion/net/load-cad-document-with-options/
[17]: https://docs.groupdocs.com/conversion/net/convert/pdf/


