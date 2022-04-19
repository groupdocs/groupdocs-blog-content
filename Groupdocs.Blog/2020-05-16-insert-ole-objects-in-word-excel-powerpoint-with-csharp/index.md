---
title: 'Insert OLE Objects in Word, Excel, PowerPoint with C#'
date: Sat, 16 May 2020 13:06:31 +0000
draft: false
url: /2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/
author: 'Shoaib Khan'
summary: '**OLE** stands for [Object Linking and Embedding][1]. It is provided by Microsoft and allows you to create and edit documents containing items or objects that are created by various applications.'
tags: ['embed OLE object in word in csharp', 'Insert OLE objects in csharp', 'insert OLE objects in excel in csharp', 'insert OLE objects in presentations in csharp']
categories: ['GroupDocs.Merger Product Family']
---

**OLE** stands for [Object Linking and Embedding][2]. It is provided by Microsoft and allows you to create and edit documents containing items or objects that are created by various applications.

As an example, you can embed spreadsheets, images, and sound clips as OLE objects in a Word document. You can use these OLE objects in the Word document and do not worry about switching to multiple applications again and again. You can embed or insert such objects programmatically using OLE in C#.

This article will guide you about how you can:

*   [Insert OLE Object into MS Word Documents][3]
*   [Insert OLE Object into Excel Spreadsheets][4]
*   [Add OLE Object into PowerPoint Presentations][5]

Steps in this article and code samples are using [GroupDocs.Merger for .NET][6]. So please make sure to install the API from any of the following methods:

*   Install using [NuGet][7] Package Manager.
*   [Download][8] the DLL and reference it into the project.

## Insert PDF as OLE Object into MS Word Document in C# {#insert-ole-obj-into-word-in-csharp}



{{< figure align=center src="images/PDF-in-Word.png" alt="Insert PDF as OLE in Word Document in C#">}}


Here are the steps and C# code sample to show **how to embed a PDF file into a Word document as an OLE Object**:

1.  Instantiate the [OleWordProcessingOptions][9] with embedding options and the document to embed in a Word document.
2.  Now instantiate the [Merger][10] object with the **source Word document** path or stream.
3.  Call the [ImportDocument][11] method and pass the object of **OLE Word Processing Options** that are set in step 1.
4.  That's it. Call the [Save][12] method to get the resultant Word document having a PDF document as an OLE object.

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

## Insert Word Document as OLE Object into Excel Spreadsheet in C# {#insert-ole-obj-into-excel-in-csharp}



{{< figure align=center src="images/Word-in-Excel.png" alt="Insert Word File s OLE in Excel Spreadsheet in C#">}}


We can embed OLE objects into Excel spreadsheets. CSharp Code sample and steps below explaining  **how to add a Word document into an Excel spreadsheet as an OLE Object**:

1.  Instantiate the [OleSpreadsheetOptions][13] with embedding options and the document to embed in an Excel spreadsheet.
2.  Now instantiate the [Merger][14] object with the **source Spreadsheet** path or stream.
3.  Now call the [ImportDocument][15] method and pass the object of **OLE Spreadsheet Options** that are set in step 1.
4.  Finally, call the [Save][16] method to get the resultant Excel Spreadsheet having a Word document as an OLE object.

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

## Add PDF as OLE Object to PowerPoint Presentation in C# {#insert-ole-obj-into-presentation-in-csharp}



{{< figure align=center src="images/PDF-in-PPT.png" alt="Insert PDF as OLE in PowerPoint Presentation in C#">}}


Similarly, here we are inserting objects in a PowerPoint presentation.

1.  Instantiate the [OlePresentationOptions][17] with embedding options and the document to embed in a PowerPoint presentation.
2.  Now instantiate the [Merger][18] object with the **source Presentation** path or stream.
3.  Call the [ImportDocument][19] method and pass the object of **OLE Presentation Options** that are set in step 1.
4.  Finally, call the [Save][20] method to get the resultant PowerPoint presentation with a PDF document as an OLE object.

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

## Conclusion

We have discussed how easy and quickly we can insert OLE Objects in Word, Excel, or PowerPoint documents programmatically in C#. There is only a small difference in code for each objective i.e. different OLE options class and its options for each file format:

*   **OleWordProcessingOptions** to embed OLE objects in a **Word document**.
*   **OleSpreadsheetOptions** to embed OLE objects in **Excel Spreadsheets**.
*   **OlePresentationOptions** to embed OLE objects in **PowerPoint presentation**.

You can learn more about the API from the [documentation][21] or **Let’s talk more @** [Free Support Forum.][22]







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

