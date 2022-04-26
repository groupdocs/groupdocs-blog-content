---
title: 'Introducing Simple and Easy to Use .NET Document Conversion API'
date: Tue, 24 Sep 2019 06:39:19 +0000
draft: false
url: /2019/09/24/introducing-simple-and-easy-to-use-.net-document-conversion-api/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

We are introducing a new public API that is designed to be implemented easily. Those who are using previous version of the API (below 19.9), you don't have to worry. The legacy API has been moved into legacy namespace. If you want to upgrade to [v19.9](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+19.9+Release+Notes), it is required to make project-wide replacement of namespace usages from **GroupDocs.Conversion** to **GroupDocs.Conversion.Legacy** in order to avoid any build issues.

**Why to use new version?**

*   _Converter_ class introduced as a single entry point to manage the document conversion process to any supported file format (instead of ConversionHander class from previous versions)
*   The overall conversion speed improved dramatically by saving each page as soon as it was converted, not when all pages list were converted
*   API architecture was redesigned to **decrease memory usage** (depending on document type)
*   Document convert options are simplified for easy control over document conversion and saving processes

**Changes at code level**

Conversion using older version:  
{{< gist GroupDocsGists 5bde6c08e20e327b32766681cbd70660 "oldconversioncode.cs" >}}

Conversion using new version:  
{{< gist GroupDocsGists 2da7cda82747f498b84deb267669b355 "newconversioncode.cs" >}}

**Bug Fixes**  
Issue "Specified argument was out of range of valid values" is fixed while converting a Spreadsheet document to PDF.

**Get Started**  
Please download or clone our updated example [project](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET) and explore [developer guide](https://docs.groupdocs.com/display/conversionnet/Developer+Guide).




