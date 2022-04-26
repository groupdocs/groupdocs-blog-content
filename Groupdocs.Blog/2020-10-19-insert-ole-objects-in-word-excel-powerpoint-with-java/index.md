---
title: 'Insert OLE Objects in Word, Excel, PowerPoint using Java'
date: Mon, 19 Oct 2020 06:02:40 +0000
draft: false
url: /2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/
author: 'Shoaib Khan'
summary: 'Today, we will be learning to **embed PDF** and other different documents **as OLE objects in Word, Excel, PowerPoint files using Java**. For embedding the documents via **Object Linking and Embedding**, we will be using the GroupDocs.Merger for Java API that also allows us to efficiently combine/merge and split multiple documents with minimum lines of Java code.'
tags: ['embed OLE objects using Java', 'insert OLE objects in Excel using Java', 'insert OLE objects in java', 'insert OLE objects in presentations using Java', 'insert OLE objects in Word using Java']
categories: ['GroupDocs.Merger Product Family']
---

In one of the earlier posts, we learned how to programmatically [insert the OLE Objects in documents with C#][1]. Today, in this article, we will be embedding PDF and other different documents as **OLE objects in Word documents, Excel spreadsheets, PowerPoint presentation slides using Java**.

This article will guide you about:

*   [Java API for OLE Objects][2]
*   [Insert OLE Objects into MS Word Documents using Java][3]
*   [Add OLE Objects into Excel Spreadsheets using Java][4]
*   [Insert Documents into Presentations via OLE using Java][5]

## Java API for OLE Objects {#java-api-for-ole-objects}



{{< figure align=center src="images/groupdocs-merger-java-90x90-no-reply.png" alt="GroupDocs.Merger for Java">}}


Steps and the examples in this article use [GroupDocs.Merger for Java][6] to insert documents into other documents via OLE (_Object Linking and Embedding_). This API also allows us to efficiently combine and split multiple documents with minimum lines of Java code. Before proceeding it will be better if you prepare the environment in any of your relevant ways:

1.  **Download** the API from the [downloads][7] section.
2.  For the **Maven-based** projects, the following is the configuration for your **pom.xml**

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>20.7</version> 
</dependency>
```

## Insert PDF as OLE Object into MS Word Document using Java {#insert-ole-object-into-word-in-java}



{{< figure align=center src="images/PDF-in-Word.png" alt="Insert PDF in Word Document">}}


Step and code example below **inserts the PDF document into a Word document as an OLE object in Java** using the GroupDocs.Merger API.

1.  Instantiate the [Merger][8] object with the source _word processing document_ path or stream.
2.  Initialize the [OleWordProcessingOptions][9] with the path of the PDF document that will be embedded in the Word document.
3.  Call the [importDocument][10] method of the merger class.
4.  Save the resultant word document by calling the [save][11] method.

{{< gist GroupDocsGists 313e9882bedaa1e65c5a540d4f30c8b0 "EmbedDocumentToWordOLE.java" >}}

## Insert Word Document as OLE Object into Excel Spreadsheet using Java {#insert-ole-object-into-excel-in-java}



{{< figure align=center src="images/Word-in-Excel.png" alt="Insert Word File in Excel Spreadsheet">}}


Spreadsheets can also embed other documents, like Word documents, spreadsheets, presentations, images or sound clips, etc. Here, I am be adding a Word document into a spreadsheet as an OLE object.

1.  Initialize the [OleSpreadsheetOptions][12] class object by providing the path of the Word document that will be embedded in the spreadsheet.
2.  Set the options like row and column positions.
3.  Initialize the [Merger][13] class object with the path of the spreadsheet document.
4.  Call the [importDocument][14] method by providing the already set OLE spreadsheet option.
5.  Save the resultant spreadsheet having the embedded Word document by calling the [save][15] method.

{{< gist GroupDocsGists 3ebe23286748c319a6b5429b1bda9696 "EmbedDocumentToExcelOLE.java" >}}

## Insert Excel Sheet as OLE Object into Presentation using Java {#insert-ole-object-into-ppt-in-java}



{{< figure align=center src="images/Add-Excel-Sheet-in-PPT-Presentation-OLE.png" alt="Insert Excel Sheet in PowerPoint">}}


Similarly, if we need to add any external document(s) to our presentations, these can be inserted at the precise location with the few lines of Java code mentioned-below:

1.  Initialize the [OlePresentationOptions][16] class object and pass the path of the spreadsheet document.
2.  Set the OLE presentation options like x and y coordinates, height and width for the upcoming embedded spreadsheet.
3.  Instantiate the [Merger][17] class object with the presentation document path as parameter.
4.  Embed the spreadsheet into presentation using the [importDocument][18] method of the Merger class.
5.  Call [save][19] method to get the resultant presentation file.

{{< gist GroupDocsGists e3a9ef77464fbb0818d81c79cdf18a06 "EmbedDocumentToPresentationsOLE.java" >}}

## Conclusion

We have learned, **how we can programmatically insert OLE objects in Word, Excel, and Powerpoint documents using Java**. The major difference while embedding the documents into various kinds of source documents is just the use of the respective OLE Options class. That's it.

To learn more about the Merger API for Java, visit [documentation][20]. In case of any query, GroupDocs Support Team will more than happy to facilitate you at [Free Support Forum][21].

## See Also

*   [Insert OLE Objects in Word, Excel, PowerPoint using C#][22]







[1]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/
[2]: #java-api-for-ole-objects
[3]: #insert-ole-object-into-word-in-java
[4]: #insert-ole-object-into-excel-in-java
[5]: #insert-ole-object-into-ppt-in-java
[6]: https://products.groupdocs.com/merger/java/
[7]: https://downloads.groupdocs.com/merger/java
[8]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[9]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OleWordProcessingOptions
[10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OleSpreadsheetOptions
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/OlePresentationOptions
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#importDocument(com.groupdocs.merger.domain.options.interfaces.IImportDocumentOptions)
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[20]: https://docs.groupdocs.com/merger/java/
[21]: https://forum.groupdocs.com/c/merger
[22]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/

