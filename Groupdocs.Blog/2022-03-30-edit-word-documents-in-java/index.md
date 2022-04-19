---
title: 'Edit Word Documents in Java'
date: Wed, 30 Mar 2022 05:58:00 +0000
draft: false
url: /2022/03/30/edit-word-documents-in-java/
author: 'Shoaib Khan'
summary: '**DOC**, **DOCX**, and **ODT** are among the most common and widely in-use word-processing file formats. Microsoft Word and OpenOffice Writer support these formats and are used for drafting documents. Therefore, as a developer, we often need to programmatically edit Word documents within the applications. In this article, we will discuss **how to edit Word documents using the Java API for document editing**.'
tags: ['Edit Word in Java', 'How to Edit Word in Java', 'Word Editing in Java', 'Word Editing Java API']
categories: ['GroupDocs.Editor Product Family']
---



{{< figure align=center src="images/edit-word-docs-in-java.jpg" alt="Edit Word Docs in Java">}}


**DOC**, **DOCX**, and **ODT** are among the most common and widely in-use word-processing file formats. Microsoft Word and OpenOffice Writer support these formats and are used for drafting documents. Therefore, as a developer, we often need to programmatically edit Word documents within the applications. In this article, we will discuss **how to edit Word documents using the Java API for document editing**.

The following topics are covered in this article:

*   [Java API - Word Documents Editing](#word-editing-java-api)
*   [Edit Word Documents in Java](#edit-word-documents-in-java)

## Java API for Word Documents Editing and Automation {#word-editing-java-api}

[GroupDocs.Editor](https://products.groupdocs.com/editor/) provides Java API for document editing and allows developers to load, edit, and save various document formats using WYSIWYG HTML editors. In addition to the word-processing document formats, the API supports editing spreadsheets, presentations, HTML, XML, TXT, CSV, and many other formats.

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

## Edit Word Documents in Java {#edit-word-documents-in-java}

After setting up the API, you can quickly move towards editing the Word document. The following steps will let you edit the word-processing documents DOC/DOCX in Java.

*   Load the Word document using [Editor](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor).
*   Fetch the [Editable Document](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/EditableDocument) using [edit()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#edit()).
*   Get the embedded HTML of the loaded DOC/DOCX document.
*   Edit the content programmatically or by using any WYSIWYG editor.
*   Convert the edited content back to an Editable Document.
*   Save the updated document using the appropriate [save()](https://apireference.groupdocs.com/editor/java/com.groupdocs.editor/Editor#save(com.groupdocs.editor.EditableDocument,%20java.lang.String,%20com.groupdocs.editor.options.ISaveOptions)) method.

The following Java code allows editing Word documents within the application.

{{< gist GroupDocsGists 4946a7e2b81db6af1799cdb151100052 "EditWordDocument.java" >}}

**Load:** You can apply additional options while loading the Word document; like providing the password if the document is protected.

**Edit:** After loading, you can edit the loaded document as per your requirement. The above example replaces all the occurrences of the word “document” with the “edited document” in a Word document.

**Save:** While saving the edited document, you can set different options. These options include; pagination, setting a password, memory optimization settings, and more.

The following is the output of the above code.



{{< figure align=center src="images/edited-document.png" alt="edited docx document using editor API" caption="Output document - All the occurrences are replaced">}}


## Conclusion

To sum up, we learned to edit Word documents in Java using document editing Java API. You can use the API along with WYSIWYG editors to visually edit your documents. You can build your own document editing Java application. For more details, options, and examples, you can visit the [documentation](https://docs.groupdocs.com/editor/java/) and the [GitHub](https://github.com/groupdocs-editor) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/c/assembly).

## See Also

*   [Annotate Word files in Java](https://blog.groupdocs.com/2022/03/19/annotate-word-documents-in-java/)
*   [How to Edit XML files in Java](https://blog.groupdocs.com/2021/11/06/edit-xml-files-in-java/)
*   [Render Word documents as Minified HTML in Java](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)




