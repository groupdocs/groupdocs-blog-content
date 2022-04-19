---
title: 'How to Rearrange Pages in Word using Java'
date: Tue, 01 Mar 2022 06:28:00 +0000
draft: false
url: /2022/03/01/move-word-pages-using-java/
author: 'Shoaib Khan'
summary: 'Word processing documents are one of the most common file formats that are used to draft documents. While dealing with multiple large files, it is never easy to move pages without losing the formatting. In order to rearrange the pages, this article discusses, **how to programmatically move pages in the Word documents (DOC/DOCX) in Java**.'
tags: ['Move Pages in DOC/DOCX', 'Move Pages in Java', 'Rearrange Document', 'Rearrange Document Pages in Java', 'Rearrange Pages in Java', 'Rearrange pages in Word']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-word-pages-in-java.jpg" alt="Rearrange Word Pages in Java">}}


Word processing documents are one of the most common file formats that are used to draft documents. While dealing with multiple large files, it is never easy to move pages without losing the formatting. In order to rearrange the pages, this article discusses, **how to programmatically move pages in the Word documents (DOC/DOCX) in Java**.

## Java API to Move Word Document Pages

**[GroupDocs.Merger](https://products.groupdocs.com/merger/)** provides the [Java API to deal with documents and their pages](https://products.groupdocs.com/merger/java/). It allows moving, removing, splitting of documents, and extraction of pages, changes in page orientation, and rotation of document pages within the Java applications. I will use this API to move pages of DOC/DOCX files. For the details and other features of the API, you can visit the [documentation](https://docs.groupdocs.com/merger/).

### Download and Configure

Get the library from the [downloads](https://downloads.groupdocs.com/merger/) section. For your Maven-based Java application, just add the following pom.xml configuration. After this, you can try the examples of this article as well the many more example available on [GitHub](https://github.com/groupdocs-merger). For the details, you may visit the [API Reference](https://apireference.groupdocs.com/merger/java).

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>22.2</version> 
</dependency>
```

## Move Pages in Word Documents using Java

Just order a page to move to the new position, it will. The following are the steps that rearrange the pages of a Word document in Java.

*   Set the page number of the target page and its new position using the [MoveOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/MoveOptions) class.
*   Load the DOC/DOCX file using the [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class.
*   Use **movePage()** method to move the set page.
*   Save the rearranged document using the **save()** method.

The following Java source code rearranges the pages of a Word document. Precisely, it moves the 7th page of a DOCX document to the 2nd place.

{{< gist GroupDocsGists c7e21344231955782149cd3686ba114b "MovePagesInWord.java" >}}

## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we learned how to change page order of a Word document in Java. We saw the source code example that changed the page position in a DOCX file. You can build your own online application to rearrange Word pages online. For more details about the API, visit the [documentation](https://docs.groupdocs.com/merger/java/). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Render Word documents as Minified HTML](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)
*   [Word Search and Replace Text in Word Documents](https://blog.groupdocs.com/2022/02/04/find-and-replace-text-in-word-documents-using-java/)
*   [How to Password Protect and Remove Protection from Word Documents](https://blog.groupdocs.com/2022/02/02/lock-unlock-word-documents-with-password-in-java/)
*   [View Word Documents as Responsive HTML Page](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)
*   [Insert OLE Objects in Word, Excel, PowerPoint](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)




