---
title: 'Edit XML Files in Java'
seoTitle: "How to Edit XML Files in Java | Java API for XML Editing"
description: "Edit or update XML data within your Java applications. Modify XML files and save the changes in various formats using Editing Java API ."
date: Sat, 06 Nov 2021 10:28:27 +0000
draft: false
url: /2021/11/06/edit-xml-files-in-java/
author: 'Shoaib Khan'
summary: "XML is commonly used to store and transmit data within and between the applications. It is often a requirement where developers need to edit the XML file when it is received or before transmitting. In this article, we will discuss **how to edit the XML file data in Java**."
tags: ['Edit XML File in Java', 'Edit XML in Java', 'How to', 'Update XML data in Java']
categories: ['GroupDocs.Editor Product Family']
---

XML is commonly used to store and transmit data within and between applications. It is often a requirement where developers need to edit the XML file when it is received or before transmitting. In this article, we will discuss **how to edit the XML file data in Java**.

*   [XML Editing Java API][1]
*   [How to Edit XML Files][2]

## Java API to Edit XML Files {#xml-edit-java-api}

GroupDocs.Editor for Java API allows you to edit documents of various file formats. In this article, we will use it to edit XML files. You can use the API along with the external editors for visual editing.

Download the **JAR** file from the [downloads section][3], or just use the latest repository and dependency [Maven][4] configurations within your Java applications.

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

## How to Edit XML Files in Java {#how-to-edit-xml}

Let's jump to the point and modify the XML data by replacing a value with another. The following are the steps to edit or update the XML file in Java.

*   Load the XML data file in the [Editor][5] class object.
*   Prepare the editing options for the XML using the [XmlEditOptions][6] class.
*   Create the [EditableDocument][7] as source content using the [edit][8] method and the prepared editing options.
*   Use [getContent][9] method of the **EditableDocument** to extract the original content of the XML file.
*   Now edit whatever is required in the XML content.
*   Now create a new **EditableDocument** from the updated XML content using [fromMarkup][10] method.
*   Use the relevant saving options like [WordProcessingSaveOptions][11] or [TextSaveOptions][12] to save the updated content in different formats.
*   Save the updated XML in any format using the [save][13] method.

The following code snippet shows how to edit an XML file in Java and update the data to save it in other formats.

{{< gist GroupDocsGists 593b2f80c8ef10c397a89a5683d9530e "EditXML.java" >}}

## Get a Free License

You can [get a free temporary license][14] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, today we learned to programmatically edit XML file data in Java. Now you can develop your [online XML editor app][15]. To further explore the features of GroupDocs.Editor, visit the [documentation][16]. For queries, contact us via the [forum][17].

## See Also

*   [How to Edit XML files using C#][18]
*   [How to Edit Word Documents in C#][19]







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

