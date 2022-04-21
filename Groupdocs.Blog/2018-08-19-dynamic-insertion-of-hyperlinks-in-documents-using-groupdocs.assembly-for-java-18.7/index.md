---
title: 'Dynamic Insertion of Hyperlinks in Documents using GroupDocs.Assembly for Java 18.7'
date: Sun, 19 Aug 2018 18:12:05 +0000
draft: false
url: /2018/08/19/dynamic-insertion-of-hyperlinks-in-documents-using-groupdocs.assembly-for-java-18.7/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for Java', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

[![Document Assembly API](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-assembly-java-1.png)](https://www.groupdocs.com/products/assembly/java)We are excitedly announcing the monthly release of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java) **18.7**.  Using the latest version, you can now insert hyperlinks dynamically in Word Processing, Spreadsheet, Presentation and Email documents. Furthermore, a bug related to **DocumentAssembler** is now fixed. We recommend you to [install](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) the latest version of the API for a better user experience.

## Features IntroducedUsing GroupDocs.Assembly for Java 18.7, you can now insert hyperlinks to your reports dynamically using link tags. The syntax of a link tag is defined as follows:```
 <<link [uri_expression][display_text_expression]>>
```Here, **uri\_expression** defines URI for a hyperlink to be inserted dynamically. This expression is mandatory and must return a non-empty value. In turn, **display\_text\_expression** defines text to be displayed for the hyperlink. This expression is optional. If it is omitted or returns an empty value, then during runtime, the value of **uri\_expression** is used as display text as well. For more details regarding this feature, please have a look at  the following documentation articles:

*   Inserting Hyperlinks Dynamically in Word Processing Document
*   Inserting Hyperlinks Dynamically in Presentation Document
*   Inserting Hyperlinks Dynamically in Spreadsheet Document
*   Inserting Hyperlinks Dynamically in Email Document

## FixesThe following bug is fixed in the latest version.

*   DocumentAssembler.assembleDocument() throws java.lang.ExceptionInInitializerError for Email and Word Processing documents

## Available Channels and ResourcesHere are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Assembly for Java:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) - Install GroupDocs.Assembly from Maven
*   [Documentation](https://docs.groupdocs.com/display/assemblyjava/Getting+Started) – API docs
*   [Examples](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java) – Source code examples
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) – Technical support forum for GroupDocs.Assembly product family

## FeedbackWe always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Assembly for Java at our [forum](https://forum.groupdocs.com/c/assembly).




