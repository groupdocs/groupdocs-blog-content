---
title: "使用 C# 在 Word、Excel、PowerPoint 中插入 OLE 对象"
date: Sat, 16 May 2020 13:06:31 +0000
draft: false
url: /zh/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/
author: 'Shoaib Khan'
summary: "**OLE** 代表 [对象链接和嵌入][1]。它由 Microsoft 提供，允许您创建和编辑包含由各种应用程序创建的项目或对象的文档。"
tags: ['embed OLE object in word in csharp', 'Insert OLE objects in csharp', 'insert OLE objects in excel in csharp', 'insert OLE objects in presentations in csharp']
categories: ['GroupDocs.Merger Product Family']
---

**OLE** 代表 [对象链接和嵌入][2]。它由 Microsoft 提供，允许您创建和编辑包含由各种应用程序创建的项目或对象的文档。

例如，您可以将电子表格、图像和声音剪辑作为 OLE 对象嵌入到 Word 文档中。您可以在 Word 文档中使用这些 OLE 对象，而不必担心一次又一次地切换到多个应用程序。您可以在 C# 中使用 OLE 以编程方式嵌入或插入此类对象。

本文将指导您如何：

* [将 OLE 对象插入 MS Word 文档][3]
* [将 OLE 对象插入 Excel 电子表格][4]
* [将 OLE 对象添加到 PowerPoint 演示文稿中][5]

本文中的步骤和代码示例使用 [GroupDocs.Merger for .NET][6]。因此，请确保通过以下任一方法安装 API：

* 使用 [NuGet][7] 包管理器安装。
* [下载][8] DLL 并将其引用到项目中。

## 在 C# 中将 PDF 作为 OLE 对象插入到 MS Word 文档中 {#insert-ole-obj-into-word-in-csharp}



{{< figure align=center src="images/PDF-in-Word.png" alt="在 C# 中的 Word 文档中将 PDF 作为 OLE 插入">}}


以下是展示**如何将 PDF 文件作为 OLE 对象嵌入 Word 文档**的步骤和 C# 代码示例：

1. 使用嵌入选项和要嵌入 Word 文档的文档实例化 [OleWordProcessingOptions][9]。
2. 现在使用**源 Word 文档** 路径或流实例化 [Merger][10] 对象。
3. 调用 [ImportDocument][11] 方法并传递在步骤 1 中设置的 **OLE 文字处理选项** 的对象。
4. 就是这样。调用 [Save][12] 方法以获取具有 PDF 文档作为 OLE 对象的结果 Word 文档。

```
// Embed a PDF file into a Word document as an OLE Object in C#
int pageNumber = 2;
OleWordProcessingOptions oleWordProcessingOptions = new OleWordProcessingOptions(@"embedded-doc.pdf", pageNumber)
{ 
    Width = 300, // Just setting the height & width, you have more options.
    Height = 300
};
// Use Merger class to start with source Word document and embed PDF as OLE object.
using (Merger merger = new Merger(@"source-doc.docx"))
{
    merger.ImportDocument(oleWordProcessingOptions);
    merger.Save(@"word-document-with-OLE.docx");
}
```

## 在 C# 中将 Word 文档作为 OLE 对象插入 Excel 电子表格 {#insert-ole-obj-into-excel-in-csharp}



{{< figure align=center src="images/Word-in-Excel.png" alt="在 C# 的 Excel 电子表格中插入 Word 文件的 OLE">}}


我们可以将 OLE 对象嵌入到 Excel 电子表格中。 CSharp 代码示例和以下步骤说明**如何将 Word 文档作为 OLE 对象添加到 Excel 电子表格中**：

1. 使用嵌入选项和要嵌入 Excel 电子表格的文档实例化 [OleSpreadsheetOptions][13]。
2. 现在使用 **source Spreadsheet** 路径或流实例化 [Merger][14] 对象。
3. 现在调用 [ImportDocument][15] 方法并传递在步骤 1 中设置的 **OLE 电子表格选项** 的对象。
4. 最后，调用 [Save][16] 方法来获取生成的 Excel 电子表格，其中包含一个 Word 文档作为 OLE 对象。

```
// Embed a Word file into an Excel Spreadsheet as an OLE Object in C#
int pageNumber = 2;
OleSpreadsheetOptions oleSpreadsheetOptions = new OleSpreadsheetOptions(@"embedded-doc.docx", pageNumber)
{
    RowIndex = 2, // Setting the Row & height Index, you have more options.
    ColumnIndex = 2
};
// Using Merger class with source spreadsheet and embedding a Word document as an OLE object.
using (Merger merger = new Merger(@"sample-doc.xlsx"))
{
    merger.ImportDocument(oleSpreadsheetOptions);
    merger.Save(@"excel-sheet-with-ole.xlsx");
}
```

## 在 C# 中将 PDF 作为 OLE 对象添加到 PowerPoint 演示文稿 {#insert-ole-obj-into-presentation-in-csharp}



{{< figure align=center src="images/PDF-in-PPT.png" alt="在 C# 的 PowerPoint 演示文稿中将 PDF 作为 OLE 插入">}}


同样，这里我们在 PowerPoint 演示文稿中插入对象。

1. 使用嵌入选项和要嵌入 PowerPoint 演示文稿的文档实例化 [OlePresentationOptions][17]。
2. 现在使用 **source Presentation** 路径或流实例化 [Merger][18] 对象。
3. 调用 [ImportDocument][19] 方法并传递在步骤 1 中设置的 **OLE Presentation Options** 的对象。
4. 最后，调用 [Save][20] 方法以获取生成的 PowerPoint 演示文稿，其中 PDF 文档作为 OLE 对象。

```
// Embed a PDF file into an Excel Spreadsheet as an OLE Object in C#
int pageNumber = 2;
OlePresentationOptions olePresentationOptions = new OlePresentationOptions(@"embedded.pdf", pageNumber)
{
    X = 10, // Setting only X & Y coordinates, you can customize more.
    Y = 10
};
// Using Merger class to embed a PDF file as an OLE object in the PowerPoint presentation.
using (Merger merger = new Merger(@"sample-presentation.ppt"))
{
    merger.ImportDocument(olePresentationOptions);
    merger.Save(@"powerpoint-presentation-with-ole.ppt");
}
```

## 结论

我们已经讨论了在 C# 中以编程方式在 Word、Excel 或 PowerPoint 文档中插入 OLE 对象是多么容易和快速。每个目标的代码只有很小的差异，即不同的 OLE 选项类及其针对每种文件格式的选项：

* **OleWordProcessingOptions** 在 **Word 文档** 中嵌入 OLE 对象。
* **OleSpreadsheetOptions** 在**Excel 电子表格** 中嵌入 OLE 对象。
* **OlePresentationOptions** 在**PowerPoint 演示文稿** 中嵌入 OLE 对象。

您可以从 [documentation][21] 或 **Let's talk more @** [Free Support Forum.][22] 中了解有关 API 的更多信息。







[1]: https://docs.microsoft.com/en-us/cpp/mfc/ole-background
[2]: https://docs.microsoft.com/en-us/cpp/mfc/ole-background
[3]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/#insert-ole-obj-into-word-in-csharp
[4]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/#insert-ole-obj-into-excel-in-csharp
[5]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/#insert-ole-obj-into-presentation-in-csharp
[6]: https://products.groupdocs.com/merger/net
[7]: https://www.nuget.org/packages/GroupDocs.Merger
[8]: https://downloads.groupdocs.com/merger/net
[9]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/olewordprocessingoptions
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/importdocument
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/olespreadsheetoptions
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/importdocument
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/olepresentationoptions
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/importdocument
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
[21]: https://docs.groupdocs.com/merger/net/import-documents/
[22]: https://forum.groupdocs.com/c/merger


