---
title: 'Strengthen the Protection of Text Watermark in Presentation Documents using GroupDocs.Watermark for Java 18.8'
date: Thu, 06 Sep 2018 06:21:40 +0000
draft: false
url: /2018/09/06/strengthen-the-protection-of-text-watermark-using-groupdocs.watermark-for-java-18.8/
author: 'Usman Aziz'
summary: ''
tags: ['Document Watermarking', 'Java document watermarking API', 'watermarking API for Java']
categories: ['GroupDocs.Watermark for Java', 'GroupDocs.Watermark for Java Releases', 'GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/01/groupdocs-watermark-java.png)](https://products.groupdocs.com/watermark/java)We are pleased to introduce version 18.8 of [GroupDocs.Watermark for Java](https://products.groupdocs.com/watermark/java). This version includes 2 new features, 1 enhancement, 1 bug fix, and a breaking change as well. It supports skipping unreadable characters during text watermark search. Furthermore, we have also added a new feature to strengthen protection of text watermark in PowerPoint documents. Please continue to read more about version 18.8.

# Features Introduced

## Skipping Unreadable Characters During Text Watermark SearchThere might be the case that the watermark's text contains unreadable characters. The unreadable characters may affect the searching of the watermark. The latest version of GroupDocs.Watermark allows finding text watermark even if it contains unreadable characters between the letters. For a working example, please refer to the following article:

*   [Skipping unreadable characters during text watermark search](https://docs.groupdocs.com/watermark/java/)

## Strengthening the Protection of Text Watermark in Presentation DocumentsUsing unreadable characters in the watermark text forbids its modification using _Find and Replace_ dialog and therefore, it strengthens the protection of text watermark in presentation documents. GroupDocs.Watermark for Java 18.8 allows including unreadable characters in a text watermark to strengthen its protection. For a working example, please refer to the following article:

*   [Strengthen protection of text watermark in presentation documents](https://docs.groupdocs.com/watermark/java/)

# Enhancements

## Support of SmartArt and CustomXml Drawing Types in Spreadsheet DocumentsThe latest version of GroupDocs.Watermark also supports **_SmartArt_** and **_CustomXml_** drawing types for Excel documents. You can now find and remove **_SmartArt_** and **_CustomXml_** drawing types from the worksheets. For a working example, please refer to the following article:

*   [Removing SmartArt and CustomXml drawing types from worksheets](https://docs.groupdocs.com/watermark/java/)

# Bug Fixes

GroupDocs.Watermark for Java 18.8 includes the fix for the following issue.

*   Locking watermark in PPTX, PPT is not working

# Breaking Change

Since version 18.8, the security of Metered licensing has been improved. Metered licensing is now applicable only in Java runtime version _8u101_ or above. Please use other types of licensing if you are using v18.8 or above in Java 7.

# Available Channels and Resources

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-watermark/maven-metadata.xml) - Install GroupDocs.Watermark from Maven
*   [Documentation](https://docs.groupdocs.com/watermark/java/ "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java "How to use Watermark API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").




