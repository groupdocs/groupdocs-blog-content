---
title: 'Lock Watermark in Word Documents using GroupDocs Watermark API for .NET'
date: Fri, 29 Jun 2018 18:27:33 +0000
draft: false
url: /2018/06/29/lock-watermark-in-word-documents-groupdocs.watermark-for-.net-18.6/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Watermarking API', 'C# Watermarking API', 'Document Watermarking', 'lock watermark in word', 'lock watermark in word document', 'Watermark', 'watermarking', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark for .NET', 'GroupDocs.Watermark for .NET Release', 'GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/05/GroupDocs-Watermark-for-.NET_.png)](https://products.groupdocs.com/watermark/net)[GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net) **18.6** has been released and it is available for download. The latest version has come with the feature of locking watermarks in **Word documents**. Furthermore, it also provides the ability to protect/unprotect the Word documents. Please continue to read more about the features added in version 18.6.

## How to Lock Watermark in Word DocumentsThere might be the case when you need to lock the watermarks in a Word document to restrict the editing. To deal with such cases, GroupDocs.Watermark provides 5 variants of locking Word document after adding watermark.

*   _AllowOnlyRevisions_: user can only add revision marks to the document.
*   _AllowOnlyComments:_ user can only modify comments in the document.
*   _AllowOnlyFormFields:_ the document is split into one-page sections and locked section with watermark is added between each two adjacent document sections.
*   _ReadOnly:_ the entire document is read-only.
*   _ReadOnlyWithEditableContent:_ the document is read-only, but all the content except the watermark is marked as editable.

The following code sample shows how to lock watermark in a Word document.```
string inputFileName = @"d:\input.docx";
string outputFileName = @"d:\output.docx";
 
using (WordsDocument doc = Document.Load(inputFileName))
{
    TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
    watermark.ForegroundColor = Color.Red;
 
    WordsShapeSettings settings = new WordsShapeSettings();
    settings.IsLocked = true;
    settings.LockType = WordsLockType.AllowOnlyFormFields;
    settings.Password = "7654321";
 
    doc.AddWatermark(watermark, settings);
 
    doc.Save(outputFileName);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/net) documentation article.

## Protect/Unprotect Word DocumentsGroupDocs.Watermark provides a simplified way of protecting the Word documents with the password. You can protect as well as unprotect the Word documents. The following protection types are supported:

*   _AllowOnlyRevisions:_ user can only add revision marks to the document.
*   _AllowOnlyComments:_ user can only modify comments in the document.
*   _AllowOnlyFormFields:_ user can only enter data in the form fields in the document.
*   _ReadOnly:_ no changes are allowed to the document.

## Protect Word DocumentThe following code sample shows how to protect a Word Document.```
using (WordsDocument doc = Document.Load(@"D:\test.doc"))
{
    doc.Protect(WordsProtectionType.ReadOnly, "7654321");
    doc.Save();
}
```

## Unprotect DocumentThe following code sample shows how to unprotect a Word Document.```
using (WordsDocument doc = Document.Load(@"D:\test.doc"))
{
    doc.Unprotect();
    doc.Save();
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/net) documentation article.

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Watermark:

*   [Installation](https://www.nuget.org/packages/GroupDocs.Watermark/ "Install from NuGet Package") - Install GroupDocs.Watermark using NuGet
*   [Documentation](https://docs.groupdocs.com/watermark/net "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.watermark-for-.NET "How to use Watermark API") - Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPusvdhHD52X_Q8bTjObAc9) – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

## FeedbackAs always, we would love to hear your queries and suggestions at our [forum](https://forum.groupdocs.com/c/watermark "Technical Support Forum").




