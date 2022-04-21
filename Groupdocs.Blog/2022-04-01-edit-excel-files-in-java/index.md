---
title: 'How to Edit Excel Files in Java'
date: Fri, 01 Apr 2022 09:54:00 +0000
draft: false
url: /2022/04/01/edit-excel-files-in-java/
author: 'Shoaib Khan'
summary: '**XLS**, **XLSX**, and **ODS** are among the most common and widely in-use spreadsheet file formats. We normally maintain various accounts and different spreadsheets using famous Microsoft Excel and OpenOffice Calc which support these formats. Therefore, as a developer, we widely require programmatically editing Excel files within our applications. In this article, we will discuss **how to edit Excel files in Java**.'
tags: ['Edit Excel Files', 'Edit Excel Files in Java', 'Excel Editing in Java', 'Excel Editing Java API']
categories: ['GroupDocs.Editor Product Family']
---

{{< figure align=center src="images/edit-excel-sheets-in-java.jpg" alt="Edit Excel Sheets in Java">}}

**XLS**, **XLSX**, and **ODS** are among the most common and widely in-use spreadsheet file formats. We normally maintain various accounts and different spreadsheets using famous Microsoft Excel and OpenOffice Calc which support these formats. Therefore, as a developer, we widely require programmatically editing Excel files within our applications. In this article, we will discuss **how to edit Excel files in Java**.

The following topics are covered in this article:

*   [Java API for Spreadsheet Editing](#spreadsheet-editing-java-api)
*   [Edit Spreadsheets in Java](#edit-excel-files-in-java)

## Java API for Editing Excel Spreadsheets and Automation {#spreadsheet-editing-java-api}

[GroupDocs.Editor](https://products.groupdocs.com/editor/) provides Java API for spreadsheet editing and allows developers to load, edit, and save various document formats using WYSIWYG HTML editors. In addition to the spreadsheet formats, the API supports editing word-processing documents, presentations, HTML, XML, TXT, CSV, and many other formats.

### Download or Configure

You may download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/editor), or just get the repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

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

## Edit Excel Spreadsheets in Java {#edit-excel-files-in-java}

You can edit the spreadsheets right after setting up the API. You can get all the content including images within the spreadsheet. The following steps will let you edit the spreadsheet XLS/XLSX spreadsheets in Java.

*   Prepare the loading options.
*   Load the Excel XLS/XLSX Spreadsheet using [Editor](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor).
*   Set the worksheet tab index and fetch the [Editable Document](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument) using [edit()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()).
*   You can get the content of the loaded worksheet tab using the respective getter method.
*   Edit the content programmatically or by using any WYSIWYG editor.
*   Convert the edited content back to an Editable Document.
*   Save the updated spreadsheet with the appropriate [save()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)) method using relevant save options.

The following Java code allows you to edit the Excel spreadsheet within the application.

{{< gist GroupDocsGists 9fcd27dc5fb28ccbf8a44bbe9d988ece "EditExcelSheets.java" >}}

**Load:** You can apply additional options while loading the spreadsheet; like providing the password if the document is protected.

**Edit:** After loading, you can edit the loaded spreadsheet. The above example replaces all the occurrences of "Old Company Name" with "New Company Name" in the first tab of the XLSX spreadsheet.

**Save:** While saving the edited spreadsheet, you can set various options like password protection, file format, and more.

## Conclusion

To conclude, we learned how to edit Excel spreadsheets in Java using document & spreadsheet editing Java API. You can use the API along with WYSIWYG editors to visually edit the spreadsheets. You can build your own spreadsheet editing Java application. For more details, options, and examples, you can visit the [documentation](https://docs.groupdocs.com/editor/java/) and the [GitHub](https://github.com/groupdocs-editor) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/c/assembly).

## See Also

*   [Watermark Excel Sheets in Java](https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/)
*   [Convert Excel Spreadsheets to PDF in Java](https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/)
*   [Convert Excel (XLS XLSX) to CSV & vice versa in Java](https://blog.groupdocs.com/2021/07/31/convert-csv-and-excel-xls-xlsx-in-java/)
*   [Insert OLE Objects in Word, Excel, PowerPoint using Java](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)
*   [Edit Word Documents in Java](https://blog.groupdocs.com/2022/03/30/edit-word-documents-in-java/)




