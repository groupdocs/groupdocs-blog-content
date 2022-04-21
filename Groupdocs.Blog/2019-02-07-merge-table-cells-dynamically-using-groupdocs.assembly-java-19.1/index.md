---
title: 'Merge Table Cells Dynamically using GroupDocs.Assembly for Java 19.1'
date: Thu, 07 Feb 2019 08:22:09 +0000
draft: false
url: /2019/02/07/merge-table-cells-dynamically-using-groupdocs.assembly-java-19.1/
author: 'Usman Aziz'
summary: ''
tags: ['Dynamic Report Generation', 'Report Generation API for Java', 'reporting API for Java']
categories: ['GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

[![Document Assembly API](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-assembly-java-1.png)](https://www.groupdocs.com/products/assembly/java)We are pleased to announce the release of version **19.1** of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java). The latest version allows you to merge the table cells having equal textual contents within your reports dynamically. Furthermore, we have introduced the feature of adding optional comments within the syntax tags that can provide a human-readable explanation. For more details on the latest version, please have a look at the [release notes](https://docs.groupdocs.com/display/assemblyjava/GroupDocs.Assembly+for+java+19.1+Release+Notes).

# Features Introduced

## Merging Table Cells DynamicallyUsing the latest version, you can tell the API to merge the table cells that have equal textual content. The following tag is used for this purpose:```
<<cellMerge -horz>>
```In the above expression, the **_horz_** switch is optional. If this switch is present, the cell merging will be performed in the horizontal direction. Otherwise, if the switch is missing, cells will be merged in the vertical direction (the default). At the moment, this feature is supported for the following document types:

*   Spreadsheet Documents
*   Presentation Documents
*   Word Processing Documents
*   Emails with HTML and RTF Bodies

For more details on this feature, please visit [this](https://docs.groupdocs.com/display/assemblyjava/Merging+Table+Cells+Dynamically#MergingTableCellsDynamically-MergingTableCellsDynamically) documentation article.

## Support of Textual Comments within Syntax TagsThis feature is introduced to add the textual comments within the syntax tags in the templates. These comments are only for providing human-readable explanation and ignored by the reporting engine. The following sample shows how to use the comments:```
<<tag\_name \[expression\] –switch1 –switch2 .. // optional\_comment>>
```

# Available Channels and Resources

Here are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Assembly for Java:

*   [Installation](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/19.1) - Install GroupDocs.Assembly for Java from Maven
*   [Download](https://downloads.groupdocs.com/assembly/java) - Zipped JAR
*   [Documentation](https://docs.groupdocs.com/display/assemblyjava/Getting+Started) – Product Documentation
*   [Examples](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java) – Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) – Technical Support Forum for GroupDocs.Assembly Product Family

# Feedback

We always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Assembly for Java at our [forum](https://forum.groupdocs.com/c/assembly).




