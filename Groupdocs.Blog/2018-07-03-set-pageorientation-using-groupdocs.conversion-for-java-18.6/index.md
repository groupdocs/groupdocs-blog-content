---
title: 'Set PageOrientation using GroupDocs.Conversion for Java 18.6'
date: Tue, 03 Jul 2018 10:33:47 +0000
draft: false
url: /2018/07/03/set-pageorientation-using-groupdocs.conversion-for-java-18.6/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for Java', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/09/conversion.png?itok=MpNabR9F)](#)

This month's release of [GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java) 18.6 comes with some bug fixes, improvements and new features. Issue such as printing complete spreadsheet instead of just printable area is fixed. A new property PageOrientation is introduced in DocumentInfo class. Please take a look over the release notes to get an idea about the new features, improvements and bug fixes.

## Features Introduced

*   Implement conversion from DWF
*   Convert specific range when converting cells document
*   Conversion from PostScript
*   specific options for converting CSV documents
*   Setting default zoom when converting to Cells
*   Default zoom when converting to Words
*   Set default zoom when converting to Slides
*   Configurable option for setting a watermark as background

## Improvements

*   Caching with provided LocalCacheDataHandler
*   Implement configuration option for selecting if blank rows and columns should be skipped when converting Cells document
*   Set zoom when converting to Pdf document
*   Update API for getting document info to detect page orientation for the supported formats
*   Set default font to replace all missing fonts when converting Words document
*   Default font to replace all missing fonts when converting Cells document
*   Conversion improvement when converting Psd and Odg to Pdf

## Issues Resolved

*   Unable to set watermark text
*   Converting specific docx document fails with Value cannot be null, parameter trueTypeFont
*   Fix failing conversion from Odg
*   Failing conversion from Ifc
*   Just print area is getting converted, not the entire spreadsheet
*   XPS to PDF conversion failed
*   LoadOptions doesn't possess setDefaultFont method
*   Problem in converting large excel files. Is there a way to paginate the excel sheet?

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [API Home](https://products.groupdocs.com/conversion/java "Product Home") - GroupDocs.Conversion for Java
*   [Download](https://downloads.groupdocs.com/conversion/java "Download API") - GroupDocs.Conversion for Java Download
*   [Documentation](https://docs.groupdocs.com/display/conversionjava/Home "Documentation") - Product Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java "Example projects") - GitHub source code examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPNfkcX3UXzMLKEOZwNpkzN) - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/conversion "Support forum") \- Technical Support Forum for GroupDocs.Conversion




