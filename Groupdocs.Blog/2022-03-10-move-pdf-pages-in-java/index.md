---
title: 'How to Rearrange PDF Pages in Java'
seoTitle: "Rearrange PDF Pages in Java | Organize with Java API"
description: "Reorder the pages of PDF files in Java. The running example shows how to correct the sequence of unordered PDF pages within the Java application."
date: Thu, 10 Mar 2022 14:49:46 +0000
draft: false
url: /2022/03/10/move-pdf-pages-in-java/
author: 'Shoaib Khan'
summary: 'PDF is among one of the most in-use portable file formats. For large documents, it is always challenging to change the order of pages with losing the formatting. This article discusses, **how to rearrange PDF pages programmatically in Java**.'
tags: ['Change Page Sequence in Java', 'Move Pages in Java', 'Rearrange Document', 'Rearrange Document Pages in Java', 'Rearrange PDF Pages', 'Rearrange PDF Pages in Java']
categories: ['GroupDocs.Merger Product Family']
---

PDF is among one of the most in-use portable file formats. For large documents, it is always challenging to change the order of pages without losing the formatting. This article discusses, **how to rearrange PDF pages programmatically in Java**.

{{< figure align=center src="images/rearrange-pdf-pages-in-java.jpg" alt="Rearrange PDF Pages in Java">}}

## Java API to Rearrange PDF Pages & Merge Documents

GroupDocs provides [GroupDocs.Merger for Java](https://products.groupdocs.com/merger/java/) to change the order of pages in documents. This API enables merging multiple documents, removing, splitting, and extraction of pages, rotation, and changes in page orientation of document pages within the applications. For the details and other features of the API, you can visit the [documentation](https://docs.groupdocs.com/merger/java/).

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

## Rearrange PDF Pages in Java

The following are the steps that help you change the sequence of PDF document pages in Java.

*   Define the existing and new position of the page in [MoveOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/MoveOptions) class.
*   Load the PDF document using the [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) class.
*   Use the **movePage()** method to rearrange pages according to defined options.
*   Save the reordered PDF file using the **save()** method.

The following Java source code rearranges the pages of PDF documents. Precisely, it moves the 6th page of the document to the 1st place.

{{< gist GroupDocsGists 220616580be284b2a2104e490d840470 "MovePagesInPDF.java" >}}

Here is the output of the above code.



{{< figure align=center src="images/Screenshot-1024x454.png" alt="">}}


## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to reorder documents by changing the page sequence of the PDF files in Java within the application. We have seen the running example that changes the position of the page. You can try building a simple application that can organize the PDF files by easily shuffling their pages.

For more details about the API, visit the [documentation](https://docs.groupdocs.com/merger/). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Password Protection of PDF Files in Java](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
*   [Ways to Split PDF Files in Java](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
*   [Merge Multiple File Types into One using Java](https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/)




