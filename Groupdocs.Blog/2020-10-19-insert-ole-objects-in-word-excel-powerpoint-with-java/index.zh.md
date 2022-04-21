---
title: "使用 Java 在 Word、Excel、PowerPoint 中插入 OLE 对象"
date: Mon, 19 Oct 2020 06:02:40 +0000
draft: false
url: /zh/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/
author: 'Shoaib Khan'
summary: "今天，我们将学习使用 Java **将 PDF** 和其他不同的文档**作为 OLE 对象嵌入 Word、Excel、PowerPoint 文件中**。为了通过**对象链接和嵌入**嵌入文档，我们将使用 Java API 的 GroupDocs.Merger，它还允许我们以最少的 Java 代码行有效地组合/合并和拆分多个文档。"
tags: ['embed OLE objects using Java', 'insert OLE objects in Excel using Java', 'insert OLE objects in java', 'insert OLE objects in presentations using Java', 'insert OLE objects in Word using Java']
categories: ['GroupDocs.Merger Product Family']
---

在之前的一篇文章中，我们学习了如何以编程方式[使用 C# 在文档中插入 OLE 对象][1]。今天，在本文中，我们将使用 Java 将 PDF 和其他不同的文档作为 **OLE 对象嵌入 Word 文档、Excel 电子表格、PowerPoint 演示幻灯片中**。

本文将指导您：

* [用于 OLE 对象的 Java API][2]
* [使用 Java 将 OLE 对象插入 MS Word 文档][3]
* [使用 Java 将 OLE 对象添加到 Excel 电子表格中][4]
* [使用 Java 通过 OLE 将文档插入演示文稿][5]

## 用于 OLE 对象的 Java API {#java-api-for-ole-objects}



{{< figure align=center src="images/groupdocs-merger-java-90x90-no-reply.png" alt="GroupDocs.Merger for Java">}}


本文中的步骤和示例使用 [GroupDocs.Merger for Java][6] 通过 OLE（_Object Linking and Embedding_）将文档插入到其他文档中。这个 API 还允许我们用最少的 Java 代码行有效地组合和拆分多个文档。在继续之前，如果您以任何相关方式准备环境会更好：

1. **从 [下载][7] 部分下载** API。
2. 对于 **基于 Maven 的**项目，以下是您的 **pom.xml** 的配置

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>20.7</version> 
</dependency>
```

## 使用 Java 将 PDF 作为 OLE 对象插入 MS Word 文档 {#insert-ole-object-into-word-in-java}



{{< figure align=center src="images/PDF-in-Word.png" alt="在 Word 文档中插入 PDF">}}


下面的步骤和代码示例**使用 GroupDocs.Merger API 将 PDF 文档作为 Java 中的 OLE 对象插入 Word 文档。

1. 使用源_字处理文档_路径或流实例化 [Merger][8] 对象。
2. 使用将嵌入 Word 文档中的 PDF 文档的路径初始化 [OleWordProcessingOptions][9]。
3. 调用合并类的[importDocument][10]方法。
4. 通过调用 [save][11] 方法保存生成的 word 文档。

```
// 将 PDF 作为 OLE 对象嵌入 Word 文档
int pageNumber = 1;
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions("PDF-document.pdf", pageNumber);
oleWordsOptions.setWidth(200); // Setting the width and height of embedded document
oleWordsOptions.setHeight(200);
// 将 PDF 导入 Word 文档
Merger merger = new Merger("document.docx"); // Source Word document
merger.importDocument(oleWordsOptions);
merger.save("output-document.docx");
```

## 使用 Java 将 Word 文档作为 OLE 对象插入 Excel 电子表格 {#insert-ole-object-into-excel-in-java}



{{< figure align=center src="images/Word-in-Excel.png" alt="在 Excel 电子表格中插入 Word 文件">}}


电子表格还可以嵌入其他文档，如 Word 文档、电子表格、演示文稿、图像或声音剪辑等。在这里，我将 Word 文档作为 OLE 对象添加到电子表格中。

1. 通过提供将嵌入电子表格的 Word 文档的路径来初始化 [OleSpreadsheetOptions][12] 类对象。
2. 设置行和列位置等选项。
3. 用电子表格文档的路径初始化 [Merger][13] 类对象。
4. 通过提供已设置的 OLE 电子表格选项来调用 [importDocument][14] 方法。
5. 通过调用 [save][15] 方法保存具有嵌入 Word 文档的结果电子表格。

```
// 将 Word 文档作为 OLE 对象嵌入 Excel 电子表格
int pageNumber = 1;
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions("document.docx", pageNumber);
oleCellsOptions.setRowIndex(2); // Set row & column number of Spreasheet to embedded document
oleCellsOptions.setColumnIndex(1);
// 将 Word 文档导入电子表格
Merger merger = new Merger("spreadsheet.xlsx"); // Source Spreadsheet
merger.importDocument(oleCellsOptions);
merger.save("output-spreadsheet.xlsx");
```

## 使用 Java 将 Excel 工作表作为 OLE 对象插入到演示文稿中 {#insert-ole-object-into-ppt-in-java}



{{< figure align=center src="images/Add-Excel-Sheet-in-PPT-Presentation-OLE.png" alt="在 PowerPoint 中插入 Excel 工作表">}}


同样，如果我们需要在演示文稿中添加任何外部文档，可以使用下面提到的几行 Java 代码将它们插入到精确位置：

1. 初始化 [OlePresentationOptions][16] 类对象并传递电子表格文档的路径。
2. 为即将到来的嵌入式电子表格设置 OLE 演示选项，例如 x 和 y 坐标、高度和宽度。
3. 使用演示文档路径作为参数实例化 [Merger][17] 类对象。
4. 使用 Merger 类的 [importDocument][18] 方法将电子表格嵌入到演示文稿中。
5. 调用 [save][19] 方法获取生成的演示文件。

```
// 将电子表格作为 OLE 对象嵌入到演示文稿中
int pageNumber = 1;
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions("spreadsheet.xlsx", pageNumber);
// 设置坐标和尺寸
oleSlidesOptions.setX(10);
oleSlidesOptions.setY(10);
oleSlidesOptions.setHeight(200);
oleSlidesOptions.setWidth(200);
// 将电子表格导入演示文稿
Merger merger = new Merger("presentation.pptx");
merger.importDocument(oleSlidesOptions);
merger.save("output-presentation.pptx");
```

## 结论

我们已经了解，**如何使用 Java 以编程方式在 Word、Excel 和 Powerpoint 文档中插入 OLE 对象**。将文档嵌入到各种源文档中的主要区别只是使用了各自的 OLE 选项类。就是这样。

要了解有关 Java 合并 API 的更多信息，请访问 [文档][20]。如有任何疑问，GroupDocs 支持团队将非常乐意在 [免费支持论坛][21] 上为您提供帮助。

## 也可以看看

* [使用 C# 在 Word、Excel、PowerPoint 中插入 OLE 对象][22]







[1]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/
[2]: #java-api-for-ole-objects
[3]: #insert-ole-object-into-word-in-java
[4]: #insert-ole-object-into-excel-in-java
[5]: #insert-ole-object-into-ppt-in-java
[6]: https://products.groupdocs.com/merger/java/
[7]: https://downloads.groupdocs.com/merger/java
[8]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[9]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OleWordProcessingOptions
[10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OleSpreadsheetOptions
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OlePresentationOptions
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[20]: https://docs.groupdocs.com/merger/java/
[21]: https://forum.groupdocs.com/c/merger
[22]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/


