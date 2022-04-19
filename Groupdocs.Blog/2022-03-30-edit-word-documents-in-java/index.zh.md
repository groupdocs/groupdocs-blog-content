---
title: "'用 Java 编辑 Word 文档'"
date: Wed, 30 Mar 2022 05:58:00 +0000
draft: false
url: /zh/2022/03/30/edit-word-documents-in-java/
author: 'Shoaib Khan'
summary: "**DOC**、**DOCX** 和 **ODT** 是最常见和广泛使用的文字处理文件格式。 Microsoft Word 和 OpenOffice Writer 支持这些格式并用于起草文档。因此，作为开发人员，我们经常需要在应用程序中以编程方式编辑 Word 文档。在本文中，我们将讨论**如何使用 Java API 编辑 Word 文档以进行文档编辑**。"
tags: ['Edit Word in Java', 'How to Edit Word in Java', 'Word Editing in Java', 'Word Editing Java API']
categories: ['GroupDocs.Editor Product Family']
---



{{< figure align=center src="images/edit-word-docs-in-java.jpg" alt="用 Java 编辑 Word 文档">}}


**DOC**、**DOCX** 和 **ODT** 是最常见和广泛使用的文字处理文件格式。 Microsoft Word 和 OpenOffice Writer 支持这些格式并用于起草文档。因此，作为开发人员，我们经常需要在应用程序中以编程方式编辑 Word 文档。在本文中，我们将讨论**如何使用 Java API 编辑 Word 文档以进行文档编辑**。

本文涵盖以下主题：

* [Java API - Word 文档编辑](#word-editing-java-api)
* [用 Java 编辑 Word 文档](#edit-word-documents-in-java)

## 用于 Word 文档编辑和自动化的 Java API {#word-editing-java-api}

[GroupDocs.Editor](https://products.groupdocs.com/editor/) 提供用于文档编辑的 Java API，并允许开发人员使用所见即所得的 HTML 编辑器加载、编辑和保存各种文档格式。除了文字处理文档格式，API 还支持编辑电子表格、演示文稿、HTML、XML、TXT、CSV 和许多其他格式。

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

## 在 Java 中编辑 Word 文档 {#edit-word-documents-in-java}

设置 API 后，您可以快速转向编辑 Word 文档。以下步骤将让您在 Java 中编辑文字处理文档 DOC/DOCX。

* 使用 [Editor](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor) 加载 Word 文档。
* 使用 [edit()](https://apireference.groupdocs.com/editor/java) 获取 [可编辑文档](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument) /com.groupdocs.editor/Editor#edit())。
* 获取加载的 DOC/DOCX 文档的嵌入 HTML。
* 以编程方式或使用任何所见即所得编辑器编辑内容。
* 将编辑后的内容转换回可编辑文档。
* 使用适当的 [save()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)) 方法保存更新的文档。

以下 Java 代码允许在应用程序中编辑 Word 文档。

```
// 在 Java 中编辑 Word DOC/DOCX 文档
Options.WordProcessingLoadOptions loadOptions = new WordProcessingLoadOptions();
loadOptions.setPassword("password-if-any");

Editor editor = new Editor("path/document.docx", loadOptions);
EditableDocument defaultWordProcessingDoc = editor.edit();

// 使用任何所见即所得编辑器进行编辑或以编程方式进行编辑
String allEmbeddedInsideString = defaultWordProcessingDoc.getEmbeddedHtml();
String allEmbeddedInsideStringEdited = allEmbeddedInsideString.replace("document", "edited document");

// 保存编辑的文档
EditableDocument editedDoc = EditableDocument.fromMarkup(allEmbeddedInsideStringEdited, null);
WordProcessingSaveOptions saveOptions = new WordProcessingSaveOptions(WordProcessingFormats.Docx);
editor.save(editedDoc, "path/edited-document.docx", saveOptions);
```

**加载** 您可以在加载 Word 文档时应用其他选项；就像在文档受到保护时提供密码一样。

**编辑** 加载后，您可以根据需要编辑加载的文档。上面的示例将 Word 文档中所有出现的单词“document”替换为“edited document”。

**保存** 保存编辑后的文档时，您可以设置不同的选项。这些选项包括：分页、设置密码、内存优化设置等。

以下是上述代码的输出。



{{< figure align=center src="images/edited-document.png" alt="使用编辑器 API 编辑 docx 文档" caption="输出文档 - 所有出现的地方都被替换">}}


## 结论

总而言之，我们学会了使用文档编辑 Java API 在 Java 中编辑 Word 文档。您可以使用 API 和所见即所得的编辑器来直观地编辑您的文档。您可以构建自己的文档编辑 Java 应用程序。有关更多详细信息、选项和示例，您可以访问 [文档](https://docs.groupdocs.com/editor/java/) 和 [GitHub](https://github.com/groupdocs-editor)存储库。如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/c/assembly) 上的支持人员。

## 也可以看看

* [用 Java 注释 Word 文件](https://blog.groupdocs.com/2022/03/19/annotate-word-documents-in-java/)
* [如何在 Java 中编辑 XML 文件](https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/)
* [在 Java 中将 Word 文档呈现为缩小的 HTML](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)





