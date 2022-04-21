---
title: 'Watermark Word Processing Documents'
date: Wed, 19 Jun 2019 13:30:33 +0000
draft: false
url: /2019/06/19/watermarking-in-word-processing-documents/
author: 'Muhammad Umar'
summary: ''
tags: ['Add Watermark in word', 'lock watermark in word', 'remove watermark in word', 'Watermark Word document', 'watermarking in word']
categories: ['GroupDocs.Watermark Product Family']
---

A watermark in presentation software and word processing is frequently used in a slightly different manner than digital watermarks used in other digital multimedia content. This watermark is often a faded image or text as a background of a slide or a page. It is meant to enhance but is not the focal point of the page/slide. Watermarks are sometimes used in the form of a logo, discreetly placed on a slide or page to brand the presentation or document.

## How GroupDocs.Watermark Works?

GroupDocs.Watermark is an API for adding watermarks to the documents of different formats. It provides the effective watermarking methods that allow you to add watermarks that are hard to be automatically removed by third-party tools. It also allows you to search and remove previously added watermarks of popular types (including watermarks added by third-party tools) in a document. The API provides straight forward and easy to use set of methods to add, search and remove watermarks in supported file formats. It supports following watermark types.

*   Text watermark
*   Image watermark

## Watermarking in Microsoft Word Documents {#WatermarksinWordDocument-WatermarksinWordDocument}

When adding watermark in Microsoft Word application, it places a shape with appropriate content in section headers. GroupDocs.Watermark API uses the same approach. When calling _AddWatermark_ method of _WordsDocument_ class, the shape is added to a document.

You can also set some additional options when adding shape watermark to a Word document using GroupDocs.Watermark.

The Following code sample demonstrates it.

{{< gist GroupDocsGists 1ef15f1094a8064f52832fd8bc439b8f "AddWatermarkWithWordsShapeSettings.cs" >}}

The code snippet for java guys is given below:

{{< gist GroupDocsGists 317b2b4e2fa1cf17b7d15a8d43169540 "Documents-AddWatermarkWithWordsShapeSettings.java" >}}

You can see the faded red watermark in the center of the document page like the screenshot given below:



{{< figure align=center src="images/sample_watermark.png" alt="Watermark in Word document using GroupDocs.Watermark">}}


Let's pick some other cases to see how effectively you can do watermarking in a Word Processing document.

## Adding Watermark to a Particular Section of Word Document {#AddingWatermarktoaWordDocument-AddingWatermarktoaParticularSection}

The Microsoft Word allows the user to divide and format the document into multiple sections. Defining sections in the document enables the user to set specific page layout and formatting for different parts of the document. An example of the sections is headers and footers. Headers and footers are to display text or any graphical object on all the pages.

GroupDocs.Watermark API allows you to add watermark objects in the headers and footers of the page. Adding watermark to a section of a Word document using GroupDocs.Watermark consists of the following steps.

1.  Load the document 
2.  Create and initialize watermark object 
3.  Set watermark properties 
4.  Add watermark to the section of the document
5.  Save the document

Following code sample adds watermark to the headers of a particular section.

{{< gist GroupDocsGists f40ba1e4445449526e3c3dcb2f7e47aa "AddWatermarkToSection.cs" >}}

Java guys will write the code like below:

{{< gist GroupDocsGists 317b2b4e2fa1cf17b7d15a8d43169540 "Documents-AddWatermarkToSection.java" >}}

## Locking Watermark in a Word Document {#LockingWatermarkinWordDocument-LockingWatermarkinWordDocument}

There might be the case when you need to lock the watermarks in a Word document to restrict the editing. To deal with such cases, the GroupDocs.Watermark provides 5 variants of locking Word document when adding watermark.

*   **AllowOnlyRevisions**: user can only add revision marks to the document.
*   **AllowOnlyComments**: user can only modify comments in the document.
*   **AllowOnlyFormFields**: the document is split into one-page sections and locked section with watermark is added between each two adjacent document sections.
*   **ReadOnly**: the entire document is read-only.
*   **ReadOnlyWithEditableContent**: the document is read-only, but all the content except the watermark is marked as editable.

_LockType_ property has been added to _WordsShapeSettings_ class to set any of the above-mentioned lock types. _WordsLockType_ enum in _GroupDocs.Watermark.Office.Words_ namespace is used to define the lock type.

The following code sample shows how to add and lock the watermark in all pages.

{{< gist GroupDocsGists e1ad119ec2a7a89d32a93976438238ad "Documents-AddLockedWatermarkToAllPages_18.6.cs" >}}

Java guys can follow the code as given below:

{{< gist GroupDocsGists 2e2323685441d3f0666499c9cf20f890 "Documents-AddLockedWatermarkToAllPages_18.6.java" >}}

## Removing Watermark from a Particular Section of Word Document {#WorkingwithExistingObjectsinWordDocument-RemovingWatermarkfromaParticularSection}

Removing watermark from a particular section of a Word document using GroupDocs.Watermark consists of following steps.

1.  Load the document 
2.  Create and initialize image/text search criteria  
3.  Find possible watermarks
4.  Remove found watermarks 
5.  Save the document

Following code sample shows how to remove watermark from a particular section.

{{< gist GroupDocsGists ae81ed92c29bf4c3926d9c1922a201c8 "RemoveWatermarkFromSection.cs" >}}

The following is code sample for Java users:

{{< gist GroupDocsGists 317b2b4e2fa1cf17b7d15a8d43169540 "Documents-RemoveWatermarkFromSection.java" >}}

The complete ready to run code sample is available on [GitHub](https://github.com/groupdocs-watermark/).




