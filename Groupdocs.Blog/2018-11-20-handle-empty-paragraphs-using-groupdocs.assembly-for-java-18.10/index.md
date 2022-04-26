---
title: 'Handle Empty Paragraphs using GroupDocs.Assembly for Java 18.10'
date: Tue, 20 Nov 2018 09:56:27 +0000
draft: false
url: /2018/11/20/handle-empty-paragraphs-using-groupdocs.assembly-for-java-18.10/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for Java', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

[![Document Assembly API](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-assembly-java-1.png)](https://www.groupdocs.com/products/assembly/java)We are excitedly announcing the monthly release of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java) **18.10**. Using the latest version, you can now remove empty paragraphs in word processing, presentation, and email documents. We recommend you to [install](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) the latest version of the API for a better user experience.

# Features Introduced

While assembling a document, if syntax tags are removed or replaced with empty values, the output document will have empty paragraphs. In version 18.10, we have introduced a new member **REMOVE\_EMPTY\_PARAGRAPHS** in **DocumentAssemblyOptions**. When this option is applied using **DocumentAssembler.setOptions()**, the engine additionally removes empty paragraphs. You can use this option for the following document types:

*   Word Processing Document
*   Presentation Document
*   Email Document

## Use CaseTemplate document.```
Prefix
<<[""]>>
Suffix
```Result document without the new option applied.```
Prefix
  
Suffix
```Result document when the new option, **REMOVE\_EMPTY\_PARAGRAPHS** is applied.```
Prefix
Suffix
```For more details on this feature, please visit this documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Assembly for Java:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) - Install GroupDocs.Assembly from Maven
*   [Documentation](https://docs.groupdocs.com/display/assemblyjava/Getting+Started) – API docs
*   [Examples](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java) – Source code examples
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) – Technical support forum for GroupDocs.Assembly product family

# Feedback

We always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Assembly for Java at our [forum](https://forum.groupdocs.com/c/assembly).




