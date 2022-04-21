---
title: "'如何使用 C# 编辑 Excel 文件'"
date: Sun, 06 Feb 2022 13:45:16 +0000
draft: false
url: /zh/2022/02/06/edit-excel-files-in-csharp/
author: 'Shoaib Khan'
summary: "最常见和广泛使用的电子表格文件格式是 **XLS**、**XLSX** 和 **ODS**。著名的 Microsoft Excel 和 OpenOffice Calc 支持这些格式，我们通常使用这些格式来维护帐户和不同的电子表格。因此，作为开发人员，我们广泛需要在我们的应用程序中以编程方式编辑 Excel 文件。在本文中，我们将讨论**如何使用 .NET API 在 C# 中编辑 Excel 文件。"
tags: ['Edit Excel file in CSharp', 'Edit Excel Files', 'Edit XLS in CSharp', 'Edit XLSX in CSharp', 'Spreadsheet Editing in CSharp']
categories: ['GroupDocs.Editor Product Family']
---

最常见和广泛使用的电子表格文件格式是 **XLS**、**XLSX** 和 **ODS**。著名的 Microsoft Excel 和 OpenOffice Calc 支持这些格式，我们通常使用这些格式来维护帐户和不同的电子表格。因此，作为开发人员，我们广泛需要在我们的应用程序中以编程方式编辑 Excel 文件。在本文中，我们将讨论**如何使用 .NET API 在 C# 中编辑 Excel 文件。

以下是本文简要讨论的主题：

* [.NET API - Excel 电子表格编辑](#excel-editing-dotnet-api)
* [在 C# 中编辑 Excel 电子表格文件](#edit-excel-files)

## 用于 Excel 电子表格编辑和自动化的 .NET API {#excel-editing-dotnet-api}

GroupDocs 展示了用于电子表格编辑的 .NET API。我将在本文的 C# 示例中使用它。它是文档编辑 API，允许开发人员使用 WYSIWYG HTML 编辑器加载、编辑和保存各种文档格式。除了 XLS、XLSX 和 ODS 电子表格格式之外，API 还支持编辑各种其他 [电子表格和 MS Excel 支持的格式](https://docs.groupdocs.com/editor/net/supported-document-formats/)例如 CSV、TSV、DSV、XLT、XLTX、XLTM、XLSM、XLSB、XLAM、SXC、SpreadsheetML、FODS、DIF。

从 [下载部分](https://downloads.groupdocs.com/editor/net) 下载 **DLL** 或 **MSI** 安装程序，或通过 [NuGet](https://www.nuget.org/packages/groupdocs.editor) 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Editor
```

## 在 C# 中编辑 Excel 文件 {#edit-excel-files}

希望您已成功引用 API。现在您可以快速开始编辑您的 Excel 文档。以下步骤将让您使用 C# 编辑电子表格文档。

* **加载** Excel 文件。
* **编辑**相应的选项。
* **保存**已编辑的文档。

### 加载 Excel 电子表格

首先，通过提供文档路径/流和密码（如果文档受密码保护) 来加载电子表格。

```
// 使用 C# 加载 Excel 文件
Options.SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
loadOptions.Password = "password"; // if any

// 加载电子表格
Editor editor = new Editor("path/spreadsheet.xlsx", delegate { return loadOptions; });
```

### 编辑 Excel 文件

加载后，您可以根据需要编辑加载的电子表格。现在我们将在电子表格的第一个选项卡中将所有出现的“旧公司名称”替换为“新公司名称”。以下步骤允许您在 C# 中相应地编辑 excel 文件。

* 使用 [Editor](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor) 和[加载选项](https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/spreadsheetloadoptions)加载 Excel 文件。
* 准备 [电子表格编辑选项](https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/spreadsheeteditoptions) 以提取准确的表格/选项卡。
* [提取](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/index) 选项卡的内容。
* 修改标签的内容。
* 您可以从选定的选项卡中提取图像和所有资源。
* 使用修改后的内容创建新的 [EditableDocument](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument)。
* 使用适当的 [Save()](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/save/index) 方法保存编辑电子表格。

以下 C# 源代码编辑 excel 文件并更改其内容。

```
// 使用 C# 编辑 Excel 电子表格

Options.SpreadsheetLoadOptions loadOptions = new SpreadsheetLoadOptions();
// loadOptions.Password = "密码";

// 加载电子表格
Editor editor = new Editor("path/spreadsheet.xlsx", delegate { return loadOptions; });

// 获取电子表格的第一个选项卡
SpreadsheetEditOptions sheetTab1EditOptions = new SpreadsheetEditOptions();
sheetTab1EditOptions.WorksheetIndex = 0; // first worksheet

// 从某个 EditableDocument 实例获取 HTML 标记
EditableDocument firstTab = editor.Edit(sheetTab1EditOptions);
string bodyContent = firstTab.GetBodyContent(); // HTML markup from inside the HTML -> BODY element
string allContent = firstTab.GetContent();      // Full HTML markup of all document, with HTML -> HEAD header and all its content

List<IImageResource> onlyImages = firstTab.Images;
List<IHtmlResource> allResourcesTogether = firstTab.AllResources;

string editedContent = allContent.Replace("Company Name", "New Company Name");
EditableDocument afterEdit = EditableDocument.FromMarkup(editedContent, allResourcesTogether);
```

### 使用选项保存编辑后的 Excel 文件

编辑后，在保存编辑后的电子表格内容的同时，您可以设置各种选项。这些选项包括：设置密码、输出格式、保护等。我在下面提到的代码中设置了上述选项，并将编辑的电子表格保存为受密码保护和写保护的 XLSX 文件。

```
// 使用 C# 保存包含更新内容的 Excel 文件
// 创建保存选项
SpreadsheetFormats xlsxFormat = SpreadsheetFormats.Xlsx;
Options.SpreadsheetSaveOptions saveOptions = new SpreadsheetSaveOptions(SpreadsheetFormats.Xlsx);

// 设置新的开启密码
saveOptions.Password = "newPassword";
saveOptions.WorksheetProtection = new WorksheetProtection(WorksheetProtectionType.All, "WriteProtectionPassword");

// 创建输出流
using (FileStream outputStream = File.Create("path/editedSpreadsheet.xlsx"))
{
    editor.Save(afterEdit, outputStream, saveOptions);
}
```

## 获得免费许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们讨论了如何使用 .NET 应用程序的文档编辑 API 在 C# 中编辑 Excel 文档。您可以将 API 与 WYSIWYG 编辑器一起使用，以可视化编辑您的文档。之后，您可以继续构建自己的在线电子表格编辑器。

有关更多详细信息、选项和示例，您可以访问 [文档](https://docs.groupdocs.com/editor/net) 和 [GitHub](https://github.com/groupdocs-editor) 存储库.如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/c/assembly) 上的支持人员。

## 相关文章

* [在 C# 中编辑 Word 文档](https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/)
* [使用 C# 编辑 XML 文件数据](https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/)

## 也可以看看

* [本地文档编辑 API](https://products.groupdocs.com/editor/family)
* [文档编辑和自动化云 API](https://products.groupdocs.cloud/editor/family)
* [在线编辑 Excel 文件](https://products.groupdocs.app/editor/excel)





