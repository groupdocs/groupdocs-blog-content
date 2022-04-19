---
title: 'How to Edit Excel Files using C#'
date: Sun, 06 Feb 2022 13:45:16 +0000
draft: false
url: /2022/02/06/edit-excel-files-in-csharp/
author: 'Shoaib Khan'
summary: 'The most common and widely used spreadsheet file formats are **XLS**, **XLSX**, and **ODS**. The famous Microsoft Excel and OpenOffice Calc support these formats and we normally use these formats for maintaining accounts and different spreadsheets. Therefore, as a developer, we widely need to edit Excel files within our applications programmatically. In this article, we will discuss **how to edit Excel files in C#** using the .NET API.'
tags: ['Edit Excel file in CSharp', 'Edit Excel Files', 'Edit XLS in CSharp', 'Edit XLSX in CSharp', 'Spreadsheet Editing in CSharp']
categories: ['GroupDocs.Editor Product Family']
---

The most common and widely used spreadsheet file formats are **XLS**, **XLSX**, and **ODS**. The famous Microsoft Excel and OpenOffice Calc support these formats and we normally use these formats for maintaining accounts and different spreadsheets. Therefore, as a developer, we widely need to edit Excel files within our applications programmatically. In this article, we will discuss **how to edit Excel files in C#** using the .NET API.

The following are the topics discussed briefly in this article:

*   [.NET API - Excel Spreadsheets Editing](#excel-editing-dotnet-api)
*   [Edit Excel Spreadsheets Files in C#](#edit-excel-files)

## .NET API for Excel Spreadsheets Editing and Automation {#excel-editing-dotnet-api}

GroupDocs showcases the .NET API for spreadsheet editing. I will use it in the C# examples of this article. It is the document editing API and allows developers to load, edit, and save various document formats using WYSIWYG HTML editors. In addition to the XLS, XLSX, and ODS spreadsheet formats, the API supports editing of various other [spreadsheets & MS Excel supported formats](https://docs.groupdocs.com/editor/net/supported-document-formats/) like CSV, TSV, DSV, XLT, XLTX, XLTM, XLSM, XLSB, XLAM, SXC, SpreadsheetML, FODS, DIF.

Download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/editor/net) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.editor).

```
PM> Install-Package GroupDocs.Editor
```

## Edit Excel Files in C# {#edit-excel-files}

Hope you have successfully referenced the API. Now you can quickly start editing your Excel documents. The following steps will let you edit the spreadsheet documents using C#.

*   **Load** the Excel file.
*   **Edit** accordingly with options.
*   **Save** the edited document.

### Load the Excel Spreadsheet

Firstly, load the spreadsheet by providing the document path/stream and the password (if the document is password protected).

{{< gist GroupDocsGists a1079591c84b3338b58097d884bb2f0d "LoadExcelDocument.cs" >}}

### Edit the Excel File

After loading, you can edit the loaded spreadsheet as needed. Now we are going to replace all the occurrences of "Old Company Name" with "New Company Name" in the first tab of the spreadsheet. The following steps allow you to edit the excel file accordingly in C#.

*   Load the Excel file using [Editor](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor) and [loading options](https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/spreadsheetloadoptions).
*   Prepare the [Spreadsheet Editing Options](https://apireference.groupdocs.com/editor/net/groupdocs.editor.options/spreadsheeteditoptions) to extract the exact sheet/tab.
*   [Extract](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument/methods/index) the content of the tab.
*   Modify the tab's content.
*   You can extract the images and all the resources from the selected tab.
*   Create the new [EditableDocument](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editabledocument) using the modified content.
*   Save the editing spreadsheet using the appropriate [Save()](https://apireference.groupdocs.com/editor/net/groupdocs.editor/editor/methods/save/index) method.

The following C# source code edits the excel file and changes its content.

{{< gist GroupDocsGists a1079591c84b3338b58097d884bb2f0d "EditExcelDocument.cs" >}}

### Save the Edited Excel File with Options

After editing, while saving the edited spreadsheet content, you can set various options. These options include; setting password, output format, protection, etc. I am setting the above options in the below-mentioned code and saving the edited spreadsheet as a password-protected and write-protected XLSX file.

{{< gist GroupDocsGists a1079591c84b3338b58097d884bb2f0d "SaveExcelDocument.cs" >}}

## Get a Free License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we discussed how to edit Excel documents in C# using document editing API for .NET applications. You can use the API with the WYSIWYG editors for the visual editing of your documents. After that, you can move ahead to build your own online spreadsheet editor.

For more details, options, and examples, you can visit the [documentation](https://docs.groupdocs.com/editor/net) and the [GitHub](https://github.com/groupdocs-editor) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/c/assembly).

## Related Articles

*   [Edit Word Documents in C#](https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/)
*   [Edit XML files Data using C#](https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/)

## See Also

*   [On-Premise Document Editing APIs](https://products.groupdocs.com/editor/family)
*   [Document Editing and Automation Cloud APIs](https://products.groupdocs.cloud/editor/family)
*   [Edit Excel Files Online](https://products.groupdocs.app/editor/excel)




