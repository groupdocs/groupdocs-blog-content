---
title: "'如何在 Java 中编辑 Excel 文件'"
date: Fri, 01 Apr 2022 09:54:00 +0000
draft: false
url: /zh/2022/04/01/edit-excel-files-in-java/
author: 'Shoaib Khan'
summary: "**XLS**、**XLSX** 和 **ODS** 是最常见和广泛使用的电子表格文件格式。我们通常使用支持这些格式的著名 Microsoft Excel 和 OpenOffice Calc 维护各种帐户和不同的电子表格。因此，作为开发人员，我们广泛需要在我们的应用程序中以编程方式编辑 Excel 文件。在本文中，我们将讨论**如何在 Java 中编辑 Excel 文件**。"
tags: ['Edit Excel Files', 'Edit Excel Files in Java', 'Excel Editing in Java', 'Excel Editing Java API']
categories: ['GroupDocs.Editor Product Family']
---

{{< figure align=center src="images/edit-excel-sheets-in-java.jpg" alt="用 Java 编辑 Excel 工作表">}}


**XLS**、**XLSX** 和 **ODS** 是最常见和广泛使用的电子表格文件格式。我们通常使用支持这些格式的著名 Microsoft Excel 和 OpenOffice Calc 维护各种帐户和不同的电子表格。因此，作为开发人员，我们广泛需要在我们的应用程序中以编程方式编辑 Excel 文件。在本文中，我们将讨论**如何在 Java 中编辑 Excel 文件**。

本文涵盖以下主题：

* [用于电子表格编辑的 Java API](#spreadsheet-editing-java-api)
* [用 Java 编辑电子表格](#edit-excel-files-in-java)

## 用于编辑 Excel 电子表格和自动化的 Java API {#spreadsheet-editing-java-api}

[GroupDocs.Editor](https://products.groupdocs.com/editor/) 提供用于电子表格编辑的 Java API，并允许开发人员使用所见即所得的 HTML 编辑器加载、编辑和保存各种文档格式。除了电子表格格式，API 还支持编辑文字处理文档、演示文稿、HTML、XML、TXT、CSV 和许多其他格式。

### 下载或配置

您可以从 [下载部分](https://downloads.groupdocs.com/editor) 下载 **JAR** 文件，或者只获取基于 **maven 的 pox.xml 的存储库和依赖项配置** Java 应用程序。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-editor</artifactId>
        <version>20.11</version> 
</dependency>
```

## 用 Java 编辑 Excel 电子表格 {#edit-excel-files-in-java}

您可以在设置 API 后立即编辑电子表格。您可以获取电子表格中的所有内容，包括图像。以下步骤将让您在 Java 中编辑电子表格 XLS/XLSX 电子表格。

*准备加载选项。
* 使用 [Editor](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor) 加载 Excel XLS/XLSX 电子表格。
* 设置工作表标签索引并使用 [edit()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()) 获取 [Editable Document](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument)。
* 您可以使用相应的 getter 方法获取加载的工作表选项卡的内容。
* 以编程方式或使用任何所见即所得编辑器编辑内容。
* 将编辑后的内容转换回可编辑文档。
* 使用相关的保存选项，使用适当的 [save()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)) 方法保存更新的电子表格。

以下 Java 代码允许您在应用程序中编辑 Excel 电子表格。

```
// 用 Java 编辑 Excel XLS/XLSX 文档
SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
loadOptions.setPassword("password-if-any");

// 加载电子表格
Editor editor = new Editor("path/sample_sheet.xlsx", loadOptions);

// 编辑电子表格的第一个选项卡
SpreadsheetEditOptions editOptions = new SpreadsheetEditOptions();
editOptions.setWorksheetIndex(0); // index is 0-based, so this is 1st tab
EditableDocument firstTab = editor.edit(editOptions);

String bodyContent = firstTab.getBodyContent();
String allContent = firstTab.getContent();
List<IImageResource> onlyImages = firstTab.getImages();
List<IHtmlResource> allResourcesTogether = firstTab.getAllResources();

String editedSheetContent = allContent.replace("Old Company Name","New Company Name");
EditableDocument editedDoc = EditableDocument.fromMarkup(editedSheetContent, null);

SpreadsheetSaveOptions saveOptions = new SpreadsheetSaveOptions(SpreadsheetFormats.Xlsx);
saveOptions.setPassword("new-password");
editor.save(editedDoc, "path/edited_spreadsheet.xlsx", saveOptions);

firstTab.dispose();
editor.dispose();
```

**加载** 您可以在加载电子表格时应用其他选项；就像在文档受到保护时提供密码一样。

**编辑** 加载后，您可以编辑加载的电子表格。上面的示例在 XLSX 电子表格的第一个选项卡中将所有出现的“旧公司名称”替换为“新公司名称”。

**保存** 在保存编辑后的电子表格时，您可以设置各种选项，如密码保护、文件格式等。

## 结论

最后，我们学习了如何使用文档和电子表格编辑 Java API 在 Java 中编辑 Excel 电子表格。您可以使用 API 和所见即所得的编辑器来直观地编辑电子表格。您可以构建自己的电子表格编辑 Java 应用程序。有关更多详细信息、选项和示例，您可以访问 [文档](https://docs.groupdocs.com/editor/java/) 和 [GitHub](https://github.com/groupdocs-editor)存储库。如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/c/assembly) 上的支持人员。

## 也可以看看

* [Java 中的水印 Excel 表格](https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/)
* [在 Java 中将 Excel 电子表格转换为 PDF](https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/)
* [在 Java 中将 Excel (XLS XLSX) 转换为 CSV，反之亦然](https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/)
* [使用 Java 在 Word、Excel、PowerPoint 中插入 OLE 对象](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)
* [用 Java 编辑 Word 文档](https://blog.groupdocs.com/2022/03/30/edit-word-documents-in-java/)





