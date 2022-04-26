---
title: "用 Java 编辑 XML 文件"
date: Sat, 06 Nov 2021 10:28:27 +0000
draft: false
url: /zh/2021/11/06/edit-xml-files-in-java/
author: 'Shoaib Khan'
summary: "XML 通常用于在应用程序内部和应用程序之间存储和传输数据。开发人员通常需要在接收到 XML 文件时或在传输之前对其进行编辑。在本文中，我们将讨论**如何在 Java 中编辑 XML 文件数据**。"
tags: ['Edit XML File in Java', 'Edit XML in Java', 'How to', 'Update XML data in Java']
categories: ['GroupDocs.Editor Product Family']
---

XML 通常用于在应用程序内部和应用程序之间存储和传输数据。开发人员通常需要在接收到 XML 文件时或在传输之前对其进行编辑。在本文中，我们将讨论**如何在 Java 中编辑 XML 文件数据**。

* [XML 编辑 Java API][1]
* [如何编辑 XML 文件][2]

## 用于编辑 XML 文件的 Java API {#xml-edit-java-api}

GroupDocs.Editor for Java API 允许您编辑各种文件格式的文档。在本文中，我们将使用它来编辑 XML 文件。您可以使用 API 和外部编辑器进行可视化编辑。

从 [下载部分][3] 下载 **JAR** 文件，或者仅在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][4] 配置。

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

## 如何在 Java 中编辑 XML 文件 {#how-to-edit-xml}

让我们跳到重点，通过用另一个值替换一个值来修改 XML 数据。以下是在 Java 中编辑或更新 XML 文件的步骤。

* 在 [Editor][5] 类对象中加载 XML 数据文件。
* 使用 [XmlEditOptions][6] 类为 XML 准备编辑选项。
* 使用 [edit][8] 方法和准备好的编辑选项创建 [EditableDocument][7] 作为源内容。
* 使用 **EditableDocument** 的 [getContent][9] 方法提取 XML 文件的原始内容。
* 现在编辑 XML 内容中所需的任何内容。
* 现在使用 [fromMarkup][10] 方法从更新的 XML 内容创建一个新的 **EditableDocument**。
* 使用 [WordProcessingSaveOptions][11] 或 [TextSaveOptions][12] 等相关保存选项以不同格式保存更新的内容。
* 使用 [save][13] 方法以任何格式保存更新的 XML。

以下代码片段显示了如何在 Java 中编辑 XML 文件并更新数据以将其保存为其他格式。

```
// 通过使用 Java 更新值来编辑 XML 文件
Editor editor = new Editor("path/XMLData.xml");

// 创建 XML 编辑选项
XmlEditOptions editOptions = new XmlEditOptions();
editOptions.setAttributeValuesQuoteType(QuoteType.DoubleQuote);
editOptions.setRecognizeEmails(true);
editOptions.setRecognizeUris(true);
editOptions.setTrimTrailingWhitespaces(true);

// 准备和编辑可编辑文档
EditableDocument beforeEdit = editor.edit(editOptions);

// 编辑 XML
String originalTextContent = beforeEdit.getContent();
String updatedTextContent = originalTextContent.replace("John", "Samuel");

List<IHtmlResource> allResources = beforeEdit.getAllResources();

// 使用更新的内容创建新的 EditableDocument
EditableDocument afterEdit = EditableDocument.fromMarkup(updatedTextContent, allResources);

// 创建文字处理保存选项
WordProcessingSaveOptions wordSaveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);

// 创建 TXT 保存选项
TextSaveOptions txtSaveOptions = new TextSaveOptions();
txtSaveOptions.setEncoding(StandardCharsets.UTF_8);

// 以 DOCX 和 TXT 格式保存编辑的 XML 数据
editor.save(afterEdit, "path/updated-xml-data.docx", wordSaveOptions);
editor.save(afterEdit, "path/updated-xml-data.txt", txtSaveOptions);
```

## 获得免费许可证

您可以 [获得免费的临时许可证][14] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，今天我们学习了在 Java 中以编程方式编辑 XML 文件数据。现在您可以开发您的 [在线 XML 编辑器应用程序][15]。要进一步探索 GroupDocs.Editor 的功能，请访问 [文档][16]。如有疑问，请通过 [论坛][17] 联系我们。

## 也可以看看

* [如何使用 C# 编辑 XML 文件][18]
* [如何在C#中编辑Word文档][19]







[1]: #xml-edit-java-api
[2]: #how-to-edit-xml
[3]: https://downloads.groupdocs.com/editor
[4]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-editor
[5]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor
[6]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/XmlEditOptions
[7]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument
[8]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()
[9]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument#getContent()
[10]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument#fromMarkup(java.lang.String,%20java.util.List)
[11]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/WordProcessingSaveOptions
[12]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor.options/TextSaveOptions
[13]: https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://products.groupdocs.app/editor/xml
[16]: https://docs.groupdocs.com/editor/java/
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/11/02/edit-xml-files-using-csharp/
[19]: https://blog.groupdocs.com/2021/03/26/edit-word-documents-in-csharp/


