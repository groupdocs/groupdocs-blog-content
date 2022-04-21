---
title: 'AutoCAD to Image Conversion Issue is Fixed'
date: Fri, 03 May 2019 06:56:56 +0000
draft: false
url: /2019/05/03/autocad-to-image-conversion-issue-is-fixed/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

Here we are with another release of GroupDocs.Conversion for .NET 19.4. We've implemented automatic naming when saving a converted document to file. Do you want to convert a **CMX** (Corel Metafile eXchange) file to PDF or any other [supported](https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats) file format? Then you must try out this release.

We also improved the process of getting page orientation for a specific page

{{< gist GroupDocsGists 3b7e4d5e2a0a2d0e8985e8119f83bae4 "pageorientation.cs" >}}

## Obsolete Methods

*   CellsLoadOptions is marked as obsolete and is replaced by SpreadsheetLoadOptions
*   CellsSaveOptions is replaced by SpreadsheetSaveOptions
*   HtmlSaveOptions is replaced by MarkupSaveOptions

See more details [here](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+19.4+Release+Notes).

## Bug Fixes

In this release, we fixed some major bugs. Let's have a overview.

*   You might be facing issue in opening resultant/converted HTML file in Microsoft Edge? However, this issue is now fixed
*   There was another issue with ODP output file. Arrows in the file star pointing in wrong direction. This bug is fixed
*   Diagrams to image conversion issue is fixed

Have a glance at API documentation [here](https://docs.groupdocs.com/display/conversionnet/Home).




