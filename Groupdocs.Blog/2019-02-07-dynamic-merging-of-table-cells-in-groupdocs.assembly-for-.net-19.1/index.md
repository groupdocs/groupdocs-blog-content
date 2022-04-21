---
title: 'Support for Dynamic Merging of Table Cells in GroupDocs.Assembly for .NET 19.1'
date: Thu, 07 Feb 2019 08:22:36 +0000
draft: false
url: /2019/02/07/dynamic-merging-of-table-cells-in-groupdocs.assembly-for-.net-19.1/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Reporting API', 'Dynamic Report Generation', 'Report Generation API for .NET', 'Reporting API for .NET']
categories: ['GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly Product Family']
---

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-assembly-net.png)We are delighted to announce the release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) **19.1**. The latest version allows you to merge the table cells having equal textual contents within your reports dynamically. Furthermore, we have introduced the feature of adding optional comments within the syntax tags that can provide a human-readable explanation. For more details on the latest version, please have a glance at the [release notes](https://docs.groupdocs.com/display/assemblynet/GroupDocs.Assembly+for+.net+19.1+Release+Notes).

# Features Introduced

## Merging Table Cells DynamicallyUsing the latest version, you can tell the API to merge the table cells that have equal textual contents. The following tag is used for this purpose:```
<<cellMerge -horz>>
```In the above expression, the **_horz_** switch is optional. If this switch is present, the cell merging will be performed in the horizontal direction. Otherwise, if the switch is missing, cells will be merged in the vertical direction (the default). At the moment, this feature is supported for the following document types:

*   Spreadsheet Documents
*   Presentation Documents
*   Word Processing Documents
*   Emails with HTML and RTF Bodies

For more details on this feature, please visit [this](https://docs.groupdocs.com/display/assemblynet/Merging+Table+Cells+Dynamically#MergingTableCellsDynamically-MergingTableCellsDynamically) documentation article.

## Support of Textual Comments within Syntax TagsThis feature is introduced to add the textual comments within the syntax tags in the templates. These comments are only for providing human-readable explanation and ignored by the reporting engine. The following sample shows how to use the comments:```
<<tag\_name \[expression\] –switch1 –switch2 .. // optional\_comment>>
```

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Assembly for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Assembly/ "GroupDocs.Assembly Nuget Package") - Install GroupDocs.Assembly for .NET using NuGet
*   [Download](https://downloads.groupdocs.com/assembly/net) - MSI Package and Zipped DLLs
*   [Documentation](https://docs.groupdocs.com/display/assemblynet/Getting+Started "Assembly API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET/tree/master/Examples "How to use Assembly API") - Source Code Examples, Plugins, and Showcase Applications
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vOzsaE9Rwjwd4-OwvdaWmJ8 "Assembly API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) - Technical Support Forum for GroupDocs.Assembly Product Family

# Feedback

As always, if you have some questions, queries or suggestions about [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) API, just share with us by creating a [forum thread](https://forum.groupdocs.com/c/assembly).




