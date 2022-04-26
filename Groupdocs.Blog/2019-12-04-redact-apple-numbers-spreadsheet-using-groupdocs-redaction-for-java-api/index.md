---
title: 'Redact Content in Apple''s Numbers Spreadsheet using GroupDocs.Redaction for Java 19.11'
date: Wed, 04 Dec 2019 07:27:57 +0000
draft: false
url: /2019/12/04/redact-apple-numbers-spreadsheet-using-groupdocs-redaction-for-java-api/
author: 'Usman Aziz'
summary: ''
tags: ['Blackout Text', 'Find and replace text', 'Groupdocs.Redaction for Java', 'text redaction']
categories: ['GroupDocs.Redaction Product Family']
---



{{< figure align=center src="images/groupdocs-redaction-java.png" alt="Java API to redact text in word pdf excel powerpoint">}}


The technology is growing at a huge pace and to stand strong through this storm you need to improve every day. Accordingly, to make you enhance your applications and take them to the next level, we keep trying to meet your emerging requirements by introducing new features and improving the existing ones. This is the reason we have introduced an optimized and simplified version of our Java document sanitization and text redaction API - [GroupDocs.Redaction for Java](https://products.groupdocs.com/redaction/java).

The **v19.11** of _GroupDocs.Redaction for Java_ has been released with a new public API and a couple of enhancements. So let's have a look at the enhancements and changes we have done in this version.

## Support of Numbers Spreadsheets

[Numbers](https://en.wikipedia.org/wiki/Numbers_(spreadsheet)) is Apple's application to create and view the spreadsheet documents in iOS or macOS. The spreadsheets created within this application are stored with _.numbers_ extension and they are quite similar to the other spreadsheets, for example, that are created with MS Excel. We have extended the list of our support spreadsheet formats in the latest release and added the ability to redact the content in the Numbers spreadsheets. Visit [spreadsheet redaction](https://docs.groupdocs.com/redaction/java) for more details on text redaction in spreadsheets.

## Setting PDF Compliance Level

_GroupDocs.Redaction_ also allows saving the redacted document into a rasterized PDF document. Since the PDF documents may possess different compliance levels such as PDF/A-1a, PDF/A-1b, we have made it possible for you to set the compliance level of the resultant PDF document as per your choice. For this, the enum [PdfComplianceLevel](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction.options/PdfComplianceLevel) has been added to **[com.groupdocs.redaction.options](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction.options/package-frame)** package. The following code sample shows how to set the PDF compliance level.

{{< gist GroupDocsGists b209d95223a0d46f9a4205ceb74117fd "SetPDFCompliance.java" >}}

## Breaking Changes

In v19.11, we have introduced a new public API which is designed to be simple and easy to use. The following are some notable changes we have made in this version and if you are already using the API, you will face these breaking changes once you upgrade.

*   The [Redactor](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction/Redactor) class is introduced to manage the document redaction process (instead of _Document _class from previous versions).
*   The methods _redactWith()_ of the _Document _class are replaced with similar [apply()](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction/Redactor#apply(com.groupdocs.redaction.Redaction)) methods in the _Redactor _class. 
*   The classes _RedactionSummary_**,** _RedactionLogRecord_**,** and _MetadataFilter_ have been renamed to  [RedactorChangeLog](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction/RedactorChangeLog), [RedactorLogRecord](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction/RedactorLogEntry), and [MetadataFilters](https://apireference.groupdocs.com/java/redaction/com.groupdocs.redaction.redactions/MetadataFilters) respectively.
*   A number of new exception classes and base exception class for _GroupDocs.Redaction_ exceptions are added.
*   The constructor _LoadOptions(DocumentFormatConfiguration)_ has been removed.
*   All the obsolete members have been removed from the public API.

Please visit the [migration notes](https://docs.groupdocs.com/display/redactionjava/Migration+Notes) to see how the classes, methods and their usage has been changed in v19.11.

Try out the [latest release](https://downloads.groupdocs.com/redaction/java) by downloading or cloning the source code examples from [GitHub](https://github.com/groupdocs-redaction/GroupDocs.Redaction-for-Java). Visit [documentation](https://docs.groupdocs.com/display/redactionjava/GroupDocs.Redaction+Overview) for more details on how to redact, hide, or find and replace text, metadata, and annotations in Word, Excel, PowerPoint, PDF, and image formats.

In case you find something difficult for you, feel free to let us know via our [forum](https://forum.groupdocs.com/c/parser).




