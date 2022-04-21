---
title: 'Protect and Unprotect Word Documents with Watermark in Java'
date: Fri, 29 Jun 2018 18:17:50 +0000
draft: false
url: /2018/06/29/protect-word-documents-with-watermark-in-java/
aliases:
    - /2018/06/29/protect-word-documents-groupdocs.watermark-for-java-18.6/
author: 'Usman Aziz'
summary: ''
tags: ['Document Watermarking', 'document-watermark', 'Java Watermarking API', 'watermarking API for Java']
categories: ['GroupDocs.Watermark for Java', 'GroupDocs.Watermark for Java Release', 'GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/01/groupdocs-watermark-java.png)](https://products.groupdocs.com/watermark/java)Another monthly release of [GroupDocs.Watermark for Java](https://products.groupdocs.com/watermark/java) is onboard. **GroupDocs.Watermark for Java 18.6** supports locking of watermarks in **Word** documents. Furthermore, it also provides the ability to protect and unprotect the Word documents. Following are the details about the new features added in version 18.6.

## Lock Watermark in Word DocumentsThere might be the case when you need to lock the watermarks in a Word document to restrict the editing. To deal with such cases, GroupDocs.Watermark provides 5 variants of locking Word document after adding watermark.

*   _AllowOnlyRevisions_: user can only add revision marks to the document.
*   _AllowOnlyComments:_ user can only modify comments in the document.
*   _AllowOnlyFormFields:_ the document is split into one-page sections and locked section with watermark is added between each two adjacent document sections.
*   _ReadOnly:_ the entire document is read-only.
*   _ReadOnlyWithEditableContent:_ the document is read-only, but all the content except the watermark is marked as editable.

The following code sample shows how to lock watermark in a Word document.```
String inputFileName = "d:\\input.docx";
String outputFileName = "d:\\output.docx";
 
WordsDocument doc = Document.load(WordsDocument.class, inputFileName);
 
TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
watermark.setForegroundColor(Color.getRed());
 
WordsShapeSettings settings = new WordsShapeSettings();
settings.setLocked(true);
settings.setLockType(WordsLockType.AllowOnlyFormFields);
settings.setPassword("7654321");
 
doc.addWatermark(watermark, settings);
 
doc.save(outputFileName);
doc.close();
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/java/) documentation article.

## Protect/Unprotect Word DocumentsGroupDocs.Watermark provides a simplified way of protecting the Word documents with the password. You can protect as well as unprotect the Word documents. The following protection types are supported:

*   _AllowOnlyRevisions:_ user can only add revision marks to the document.
*   _AllowOnlyComments:_ user can only modify comments in the document.
*   _AllowOnlyFormFields:_ user can only enter data in the form fields in the document.
*   _ReadOnly:_ no changes are allowed to the document.

### Protect a Word DocumentThe following code sample shows how to protect a Word Document.```
WordsDocument doc = Document.load(WordsDocument.class, "D:\\test.doc");
doc.protect(WordsProtectionType.ReadOnly, "7654321");
doc.save("D:\\test.doc");
doc.close();
```

### Unprotect a Word DocumentThe following code sample shows how to unprotect a Word Document.```
WordsDocument doc = Document.load(WordsDocument.class, "D:\\test.doc");
doc.unprotect();
doc.save("D:\\test.doc");
doc.close();
```For more details on this feature, please visit [this](https://docs.groupdocs.com/display/watermarkjava/Protecting+Word+Documents) documentation article.

## Available Channels and Resources

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-watermark/maven-metadata.xml) - Install GroupDocs.Watermark from Maven
*   [Documentation](https://docs.groupdocs.com/watermark/java/ "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java "How to use Watermark API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").




