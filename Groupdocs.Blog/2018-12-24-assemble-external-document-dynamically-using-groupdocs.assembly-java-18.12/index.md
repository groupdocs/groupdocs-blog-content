---
title: 'Assemble External Document Dynamically using GroupDocs.Assembly for Java 18.12'
date: Mon, 24 Dec 2018 22:20:52 +0000
draft: false
url: /2018/12/24/assemble-external-document-dynamically-using-groupdocs.assembly-java-18.12/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for Java', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

[![Document Assembly API](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-assembly-java-1.png)](https://www.groupdocs.com/products/assembly/java)We are excitedly announcing the monthly release of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java) **18.12**. Using the latest version, you can now assemble external documents dynamically for Word Processing and Email file formats. Previously, an evaluation mark was added to a nested document being inserted dynamically, which is now fixed. We recommend you to [install](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) the latest version of the API for better user experience.

# Features Introduced

You can insert contents of outer documents to your reports dynamically using doc tags. A doc tag denotes a placeholder within a template for a document to be inserted during runtime. The syntax of a doc tag is defined as follows:```
<<doc ["document_expression"]>> 
```An expression declared within a doc tag is used by the engine to load a document to be inserted during runtime. The expression must return a value of one of the following types:

*   A byte array containing document data
*   An  [InputStream](https://docs.oracle.com/javase/7/docs/api/java/io/InputStream.html) instance able to read document data
*   A string containing a document URI

While building a report, an expression declared within a doc tag is evaluated and its result is used to load a document whose content replaces the doc tag then. By default, a document being inserted is not checked against template syntax and is not populated with data as well. However, you can enable this by using a build switch as follows:```
<<doc ["document_expression"] -build>> 
```When a build switch is used, the engine treats a document being inserted as a template that can access the following data available at the scope of a corresponding doc tag:

*   Data sources
*   Variables
*   A contextual object
*   Known external types

For more details on this feature, please visit [this](https://docs.groupdocs.com/display/assemblyjava/Working+with+Outer+Document+Insertion) documentation article.

# Fixes

The following bug is fixed in the latest version of the API.

*   An evaluation mark is added to a nested document being inserted dynamically

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Assembly for Java:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) - Install GroupDocs.Assembly from Maven
*   [Documentation](https://docs.groupdocs.com/display/assemblyjava/Getting+Started) – API docs
*   [Examples](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java) – Source code examples
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) – Technical support forum for GroupDocs.Assembly product family

# Feedback

We always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Assembly for Java at our [forum](https://forum.groupdocs.com/c/assembly).




