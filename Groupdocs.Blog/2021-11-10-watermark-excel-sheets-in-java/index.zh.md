---
title: "Java中的水印Excel表格"
date: Wed, 10 Nov 2021 14:04:00 +0000
draft: false
url: /zh/2021/11/10/watermark-excel-sheets-in-java/
author: 'Shoaib Khan'
summary: 'Watermarks can be added to the documents either to protect the document from piracy, or to show any sumbol or message. In other posts, we discussed ways to watermark different [documents][1], [images][2], and [presentations][3]. In this article, you will learn **how to add watermark to Excel workbooks in different ways in Java**. We will be applyling watermarks separately using each approach.

本文涵盖以下主题：

* Java的水印API
* 添加**文本水印**到 Excel 表格
* 将水印应用到**特定的 Excel 工作表**
* 将水印添加到 Excel 工作表**作为背景**'
tags: ['add watermark in java', 'how to add watermark in Java', 'watermark excel', 'watermark excel sheets in Java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/add-watermark-to-excel-java.jpg" alt="用Java在Excel工作表中添加水印">}}


可以将水印添加到文档中以保护文档免受盗版或显示任何符号或消息。在其他帖子中，我们讨论了为不同的文档、图像和演示文稿添加水印的方法。在本文中，您将学习如何在 Java 中以不同方式向 Excel 工作簿添加水印。我们将使用每种方法分别应用水印。

以下主题涵盖以下内容：

* [Java 水印 API][4]
* [将**文本水印**添加到 Excel 表格][5]
* [将水印应用到**特定的 Excel 工作表**][6]
* [将水印添加到 Excel 工作表**作为背景**][7]

## Java API 到水印 Excel 表 {#watermarking-java-api}

[GroupDocs.Watermark for Java][8] 是自动化文档、演示文稿、图像和许多其他文件格式的水印的 API。 [文档][9] 中提供了支持的文档格式的完整列表。

您可以从 [下载部分][10] 下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][11] 配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## 使用 Java 为 Excel 表格添加水印 {#watermark-all-sheets}

水印 API 在将水印作为文本插入电子表格时提供自定义。以下是在 Java 中向 Excel 工作簿添加水印的步骤。

* 使用 [Watermarker][12] 和 [SpreadsheetLoadOptions][13] 加载源电子表格。
* 使用 [TextWatermark][14] 定义水印文本和外观属性。
* 使用 [add()][15] 方法将定义的水印添加到 Excel 工作表。
* 使用 [save()][16] 方法保存带有水印的结果电子表格。

以下 Java 代码示例将文本水印添加到 Excel 工作簿的所有工作表中，具有旋转和不透明度以及设置的对齐方式。

```
/*
 * Add watermark to all the sheets of the Excel Workbook in Java
 */
// 加载电子表格
String filename = "path/spreadsheet.xlsx";
Watermarker watermarker = new Watermarker(filename, new SpreadsheetLoadOptions());

// 设置文字水印外观
TextWatermark watermark = new TextWatermark("DRAFT", new Font("Segoe UI", 19));
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
watermark.setRotateAngle(-45);
watermark.setSizingType(SizingType.ScaleToParentDimensions);
watermark.setScaleFactor(0.5);
watermark.setOpacity(0.5);

// 添加水印并保存带有水印的电子表格
watermarker.add(watermark);
watermarker.save("path/watermark-all-spreadsheet.xlsx");
watermarker.close();
```

## 使用 Java 的水印特定 Excel 工作表 {#watermark-any-sheet}

同样，您也可以将水印插入工作簿的任何单张纸中。以下步骤指导如何将文本水印应用于 Java 中 Excel 工作簿的特定工作表。

* 使用 [Watermarker][17] 加载电子表格。
* 使用[TextWatermark][18]设置水印外观和文字。
* 设置工作表索引，以便水印仅应用于提到的工作表。
* 使用带有水印选项的 [add()][19] 方法将文本水印添加到 Excel 工作表。
* 使用 [save()][20] 方法保存带有水印的输出电子表格。

以下 Java 代码片段仅将文本水印应用于 Excel 工作簿的提及工作表。

```
/*
 * Add watermark only to the mentioned sheet of the Excel Workbook using Java
 */
// 加载电子表格
String filename = "path/spreadsheet.xlsx";
Watermarker watermarker = new Watermarker(filename, new SpreadsheetLoadOptions());

// 设置文本水印及其工作表索引
TextWatermark watermark = new TextWatermark("DRAFT", new Font("Segoe UI", 19));
SpreadsheetWatermarkModernWordArtOptions options = new SpreadsheetWatermarkModernWordArtOptions();               
options.setWorksheetIndex(0);

// 添加水印并保存带有水印的电子表格
watermarker.add(watermark, options);
watermarker.save("path/watermark-single-sheet.xlsx");
watermarker.close();
```

## 使用Java水印Excel表格作为背景 {#watermark-sheet-as-background}

同样，我们也可以添加水印作为电子表格的背景。对上述应用水印的方法会有一些修改。以下是在 Java 中将背景文本水印插入 Excel 电子表格的步骤。

* 使用 [Watermarker][21] 加载电子表格。
* 使用 [TextWatermark][22] 准备水印文本及其外观。
*通过获取内容和设置尺寸，使用水印选项设置水印设置以使其成为背景。
* 使用 [add()][23] 方法将水印添加到工作簿表中。
* 最后，使用 [save()][24] 方法保存带水印的电子表格。

以下代码示例可用于将背景文本水印添加到 Java 中的 Excel 电子表格。

```
/*
 * Add watermark as background to Excel Workbook in Java
 */
// 加载电子表格
String filename = "path/spreadsheet.xlsx";
Watermarker watermarker = new Watermarker(filename, new SpreadsheetLoadOptions());

// 设置文字水印外观
TextWatermark watermark = new TextWatermark("DRAFT", new Font("Segoe UI", 19));
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);
watermark.setRotateAngle(-45);
watermark.setSizingType(SizingType.ScaleToParentDimensions);
watermark.setScaleFactor(0.5);
watermark.setOpacity(0.5);

// 在背景中添加水印
SpreadsheetContent content = watermarker.getContent(SpreadsheetContent.class);
SpreadsheetBackgroundWatermarkOptions options = new SpreadsheetBackgroundWatermarkOptions();
options.setBackgroundWidth(content.getWorksheets().get_Item(0).getContentAreaWidthPx()); /* set background width */
options.setBackgroundHeight(content.getWorksheets().get_Item(0).getContentAreaHeightPx()); /* set background height */

// 保存带水印的电子表格
watermarker.add(watermark, options);
watermarker.save("path/watermark-background-spreadsheet.xlsx");
watermarker.close();
```



{{< figure align=center src="images/watermark-excel-sheets-programmatically.png" alt="以编程方式水印 Excel 工作表">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][25] 以便在没有评估限制的情况下使用 API。

## 结论

在本文中，我们讨论了如何在 Java 应用程序中以不同方式向 Excel 表格添加水印。我们学会了在 Excel 工作簿的所有工作表中插入文本水印，然后我们只将水印应用于特定工作表。后来，我们应用了水印作为背景。您现在可以使用此功能并构建自己的应用程序来为电子表格添加水印。

从 [文档][26] 中了解有关 API 的更多信息。如有疑问，请通过 [论坛][27] 联系我们。

## 也可以看看

* [使用 C# 给 Excel 表格加水印][28]
* [Java 中的水印 PDF 文件][29]
* [在Java中为图像添加水印][30]
* [使用 Java 的水印演示幻灯片][31]
* [在Java文档中查找和删除水印][32]







[1]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[3]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[4]: #watermarking-java-api
[5]: #watermark-all-sheets
[6]: #watermark-any-sheet
[7]: #watermark-sheet-as-background
[8]: https://products.groupdocs.com/watermark/
[9]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[10]: https://downloads.groupdocs.com/watermark
[11]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-watermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/SpreadsheetLoadOptions
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[16]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[19]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[20]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[21]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[22]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[23]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[24]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[25]: https://purchase.groupdocs.com/temporary-license
[26]: https://docs.groupdocs.com/watermark
[27]: https://forum.groupdocs.com/
[28]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[29]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[30]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[31]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[32]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/


